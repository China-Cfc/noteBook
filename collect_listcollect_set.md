[![Fork me on GitHub](../tuxiang/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6461726b626c75655f3132313632312e706e67)
![img]()Fork me on GitHub](https://github.com/CC11001100)

# [Hive笔记之collect_list/collect_set（列转行）](https://www.cnblogs.com/cc11001100/p/9043946.html)

Hive中collect相关的函数有collect_list和collect_set。

它们都是将分组中的某列转为一个数组返回，不同的是collect_list不去重而collect_set去重。

 

做简单的实验加深理解，创建一张实验用表，存放用户每天点播视频的记录：

```
create` `table` `t_visit_video (``  ``username string,``  ``video_name string``) partitioned ``by` `(``day` `string)``row format delimited fields terminated ``by` `','``;
```

在本地文件系统创建测试数据文件：

```
张三,大唐双龙传``李四,天下无贼``张三,神探狄仁杰``李四,霸王别姬``李四,霸王别姬``王五,机器人总动员``王五,放牛班的春天``王五,盗梦空间
```

将数据加载到Hive表：

```
load` `data ``local` `inpath ``'/root/hive/visit.data'` `into` `table` `t_visit_video partition (``day``=``'20180516'``);
```

![image](../tuxiang/784924-20180516011138356-706761665.png)

 

按用户分组，取出每个用户每天看过的所有视频的名字：

```
select` `username, collect_list(video_name) ``from` `t_visit_video ``group` `by` `username ;
```

![image](../tuxiang/784924-20180516011138692-883299316.png)

但是上面的查询结果有点问题，因为霸王别姬实在太好看了，所以李四这家伙看了两遍，这直接就导致得到的观看过视频列表有重复的，所以应该增加去重，使用collect_set，其与collect_list的区别就是会去重：

```
select` `username, collect_set(video_name) ``from` `t_visit_video ``group` `by` `username;
```



![image](../tuxiang/784924-20180516011140823-794187986.png)

李四的观看记录中霸王别姬只出现了一次，实现了去重效果。

 

## 突破group by限制

还可以利用collect来突破group by的限制，Hive中在group by查询的时候要求出现在select后面的列都必须是出现在group by后面的，即select列必须是作为分组依据的列，但是有的时候我们想根据A进行分组然后随便取出每个分组中的一个B，代入到这个实验中就是按照用户进行分组，然后随便拿出一个他看过的视频名称即可：

```
select` `username, collect_list(video_name)[0] ``from` `t_visit_video ``group` `by` `username;
```

![image](../tuxiang/784924-20180516011142033-508747980.png)

video_name不是分组列，依然能够取出这列中的数据。

