[hive sql基本知识地址](https://www.gairuo.com/p/hive-sql-tutorial)



# sql基础操作

## 筛选指定字段

---



## distinct去重

在真实环境中，数据往往是流水形成出现，有些字段会有大量的重复值，我们需要进行去重。`count(distinct uuid)` 是常用的获取 UV 的方法。

distinct 与 `group by` 可以得到相同的结果，从效率上可能会比 distinct 更高。

## `case`条件赋值

#### case

```mysql
select c_1,
       CASE
           WHEN condition1 THEN result1
           WHEN condition2 THEN result2
           WHEN conditionN THEN resultN
           ELSE result_else
           END as c_name
from tab_name
```

注：

- 由 CASE 开始 END 结束
- 最好起一个别名（as c_name，c_name 为别名），不然此列没有可读性名称
- WHEN 和 THEN 成对出现，WHEN 后边为条件，可以使用表中的所有字段，THEN 后为最终输出的值
- ELSE 为兜底逻辑，直接给出值，ELSE 可以没有
- 没有被条件覆盖的值为 null

### **`order by`**应用

有时候用 order by 排序时，如果有空值想排到前边或者后边，或者给定一定的排序算法，可以将 CASE 语句用在 order by 中。

以下将生日小于 1990 年的同学数据加20分，再排序：

```mysql
select name, b_year, math
from students
order by (CASE
              WHEN b_year < 1990 THEN math+20
              ELSE math
    END) DESC
'''
name|b_year|math|
----+------+----+
王卫栋 |  1966|  88|
田迪  |  1988|  78|
武明  |  1977|  78|
周平  |  1988|  77|
王琳  |  2010|  88|
张涛  |  1950|  66|
赵天成 |  2000|  77|
赵丹丹 |  1996|  55|
李成  |  2011|  54|
'''
```



## `where`条件查询

| 操作                   | 条件说明           | SQL 样例                   |
| ---------------------- | ------------------ | -------------------------- |
| =, !=, <>, < <=, >, >= | 数字及逻辑         | class != 3; math > 80      |
| IS NULL                | 值为 NULL          | name IS NULL               |
| IS NOT NULL            | 值不为 NULL        | name IS NOT NULL           |
| BETWEEN … AND …        | 包含两端的数字范围 | math BETWEEN 60 AND 80     |
| NOT BETWEEN … AND …    | 上述的不包含       | math NOT BETWEEN 60 AND 80 |
| IN (…)                 | 内容在指定的列表中 | class IN (1,2)             |
| NOT IN (…)             | 不在指定的列表中   | class NOT IN (1,2)         |
| LIKE …                 | 按内容搜索匹配     | name LIKE "张%"            |
| NOT LIKE …             | 不匹配此规则       | name NOT LIKE "张%"        |

注：

- != 和 <> 都是不等于
- 判断是空字符串为 `a = ''`
- LIKE 可以用 `%` 和 `_` 通配符等进行匹配
- In 不能滥用，in 里面只能有几个（如枚举），不能有几千几万几十万个，容易卡死系统。更好的办法是不用 in ，使用 join 处理

通配符：

- `%`：匹配不定长，"%AT%" (匹配 "AT", "ATTIC", "CAT" 及 "BATS")
- `_`：匹配1个定长，"AN_" (匹配 "AND", 但不匹配 "AN")
- Hive 可以使用 RLIKE 使用正则进行匹配 // TODO

注：如果需要匹配 `%` 和 `_` 本身，需要进行转义，如 `8\%%`（8%，8%9），`my\_code_`（my_codes）。



## 标量子查询

标量子查询就是返回单一值的子查询。标量就是单一值的意思，有时候我们在查询中需要和某个计算后的单一值进行查询或者计算，它可以和本表组合，也可以和外表组合。

警告

**==Hive SQL 不支持标量子查询，可以使用 [join 连接](https://www.gairuo.com/p/sql-join)替换子查询的方式。MySQL 等支持，在此了解一下。==**

---

# 条件设定

## `order by`排序

**升降序:**

- asc: ascending order 升序
- desc: descending order 降序

### 用序号代表字段

在用 ORDER BY 按一定的字段排序时，如果你不想写字段名，可以用 Select 中的序号来代码这些字段，如：

```mysql
SELECT item_id, uesr_id
         ^^^^        ^^^^
          1           2
FROM tab
ORDER BY 1; 
#加入limit限制条数  比如 
select * from emp limit 100; 取前一百的数据
```

在上面的查询中 ORDER BY 1 指的是 select 语句中的第一列，那就是 item_id。这个用法，还可以用在 GROUP BY 子句中。

注意：**ORDER BY 和GROUP BY 中的数字始终以 1 开头，而不是以 0 开头。**

---





## Hive Sql数据排序

本文将介绍 Hive SQL 中对数据进行排序的方法。与标准 SQL 一样，HQL 也支持 ORDER BY 语句，但由于 Hive 对大数据的处理机制，需要我们在认识这些机制的基础上做些调整以达到 SQL 执行性能的最优化。

### `sort by`

Hive SQL 还支持 sort by 进行排序，功能与 ORDER BY 一致：

```mysql
SELECT column, another_column
FROM mytable
WHERE condition(s)
sort by column ASC/DESC
```

hive 中的 order by 会对查询出的结果集执行一次全局排序，意味着所有的数据都通过一个 reduce 进行处理过程，这对于大数据集，这个过程将消耗很大的时间来执行。

**在严格模式下直接使用 order by 会报错，必须加上 LIMIT 关键字。**

hive 的 sort by 是执行一个局部排序过程。这可以保证每个 reduce 的输出数据都是有序的(但并非全局有效)。这样就可以提高后面进行的全局排序的效率了。对于这两种情况，语法区别仅仅是，一个关键字是 order，另一个关键字是 sort。用户可以指定任意期望进行排序的字段，并可以在字段后面加上asc关键字(默认)表示升序，desc关键字是降序排序。

**在使用sort by之前，需要先设置Reduce的数量>1**(`set mapreduce.job.reduces=n;`)，才会做局部排序，如果Reduce数量是1，作用与 order by一样，全局排序,最后输出结果会按照Reduce的数量m分成m个文件.

缺点：只能做局部排序，对输出的结果再执行归并排序，即可得到全部排序结果。

优点：sort by 不受 hive.mapred.mode 是否为strict ,nostrict 的影响。且查询效率比order by高

sort by 是单独在各自的reduce中进行排序，所以并不能保证全局有序，一般和distribute by 一起执行，而且distribute by 要写在sort by前面。

- 将查询结果导入到文件中

  ```mysql
  insert overwrite local directory '/hive_data'
  select * from employee sort by salary desc;
  ```

- 设置reduce个数

  ```mysql
  set mapreduce.job.reduces=n;
  ```

- 查看reduce个数

  ```mysql
  set mapreduce.job.reduces;
  ```

  

[原文链接：][https://blog.csdn.net/weixin_45666566/article/details/112006662]



### `distribute by` 分区排序

Hive SQL 还支持 distribute by 进行排序。distribute 意为分发、分配。

distribute by 控制 map 的输出在 reduer 中是如何划分的，mapreduce job 中传输的所有数据都是按照键-值对的方式进行组织的，因此 hive 在将用户的查询语句转换成mapreduce job 时，其必须在内部使用这个功能。默认情况下，MapReduce 计算框架会依据 map 输入的键计算相应的哈希值，然后按照得到的哈希值将键-值对均匀分发到多个reducer 中去，不过不幸的是，这也是意味着当我们使用sort by 时，不同 reducer 的输出内容会有明显的重叠，至少对于排序顺序而已只这样，即使每个 reducer 的输出的数据都有序的。

> distribute by 控制 map的输出在reduer中是如何划分的，mapreduce job 中传输的所有数据都是按照键-值对的方式进行组织的，因此hive在将用户的查询语句转换成mapreduce job时，其必须在内部使用这个功能。默认情况下，MapReduce计算框架会依据map输入的键计算相应的哈希值，然后按照得到的哈希值将键-值对均匀分发到多个reducer中去，不过不幸的是，这也是意味着当我们使用sort by 时，不同reducer的输出内容会有明显的重叠，至少对于排序顺序而已只这样，即使每个reducer的输出的数据都有序的。如果我们想让同一年的数据一起处理，那么就可以使用distribute by 来保证具有相同年份(即相同KEY)的数据分发到同一个reducer中进行处理，然后使用sort by 来按照我们的期望对数据进行排序:
> ————————————————
> 版权声明：本文为CSDN博主「珞沫」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
> [原文链接][https://blog.csdn.net/weixin_45666566/article/details/112006662]



```mysql
FROM records
SELECT year, temperature
DISTRIBUTE BY year
SORT BY year DESC, temperature DESC
```

以上例子子为在根据年份和气温对气象数据进行排序时，我们希望看到同一年的数据被放到同一个reducer中去处理。因而，这个结果也肯定是全局排序的。特别的，因为distribute by 通常和sort by 一起用，所以当distribute by 遇上 sort by时，distribute by要放在前面，这个不难理解，因为要先通过 distribute by 将待处理的数据从map端做分发，这样，sort by 这个擅长局部排序的才能去放开的干活。不然要是没有distribute by的分发，那么sort by 将要处理全部的数据，即全局排序，这不是 sort by的活，这样做只能拖慢集群工作效率。

### `cluster by`

- Hive 的 cluster by 除了distribute by 的功能外，还会对该字段进行排序，cluster by 指定的列只能是降序，不能指定 asc 和 desc。

- 当distribute by 和 sort by 字段相同时,所以 cluster by = distribute by + sort by 。

例如：

```mysql
select * from students cluster by b_year
```

等价于：

```mysql
select * from students distribute by b_year sort by b_year
```

例子：
（1）设置reduce的个数

```mysql
set mapreduce.job.reduces=3;
```


(2) 按部门分区排序

```mysql
insert overwrite local directory '/hive_data/cluster_result'
select * from employee cluster by deptID;
```


等价于

```mysql
insert overwrite local directory '/hive_data/cluster_result'
select * from employee distribute by deptID sort by deptID ;
```

`


### Hive SQL 的排序

hive 的 order by ，sort by ，distribute by 和 cluster by 这几个语句，在 hive 中都有排序和聚集的作用，然而，它们在执行时所启动的MR却各不相同。

- order by：全部数据进行全局排序，只会启动一个 reducer
- sort by：局部排序，会根据数据量大小启动一到多个 reducer
- distribute by：控制 map 结果的分发
- cluster by：如果 distribute by 和 sort by 的列相同可以用 cluster by 简写

其中，以下语句只能降序，不能指定 asc 和 desc：

- distribute by
- cluster by

## and,or和not的逻辑连接



| 符号 | 逻辑             | 举例                          |
| ---- | ---------------- | ----------------------------- |
| AND  | 和，全部为真     | b_year > 2000 and math > 80   |
| OR   | 或，只要一个为真 | b_year = 2010 or chinese > 80 |
| NOT  | 非，与逻辑值相反 | not gender == '男'            |



## `LIMIT`和`OFFSET`限制结果数量

### **<u>LIMIT</u>**

在SQL逻辑后面加入`LIMIT N`(N 为要返回几个数量)

```mysql
select * from emp limit 100;
```

以上的 LIMIT 是对数量的限制是从第一个开始的,从第一条到100条.

有时候需要指定一个位置开始

```mysql
select * from emp limit 10,20;
```

以上从第10条(不含)开始取20条.

---

### <u>**OFFSET**</u>

`OFFSET`是设置开始取数的位置,位置从0开始计算,一般可以省略写成上例纯limit形式:

```mysql
-- 取3条,从第5个开始
select * from emp limit 3 offset 4
-- 取4条,从第4个开始
select * from emp limit 3,4
```

---

### <u>**对比**</u>

**区别:**

- limit Y:从头取Y个数据
- limit X,Y:跳过X个数据,取Y个数据
- limit Y offset X : 跳过X条数据,取Y条数据

如果跳过的数量大于总数量则返回空,如果选取的数量不够,有多少返回多少

---

### **<u>TOP N</u>**

`TOP`可以指定前几个输出结果,但只有像 SQL Server/MS Access才支持,其他数据库还是 LIMIT.

```sql
SELECT TOP 3 * FROM EMP;
```

`ORACLE`中没有 limit 支持,只有`ROWNUM`参数,放在条件判断里,如

```plsql
select * from emp where rownum <=3
```

---

# SQL高级操作

## 常用聚合统计函数

| 函数    | 功能描述 | 其他                                          |
| ------- | -------- | --------------------------------------------- |
| count() | 条数     | 不计 null 值                                  |
| sum()   | 求和     | True 按 1 处理，False 按 0 处理，忽略 null 值 |
| max()   | 最大值   | 时间字段代表最近最晚的时间                    |
| min()   | 最小值   | 时间字段代表最早的时间                        |
| avg()   | 平均值   | 忽略 null 值, sum 除以非空值的计数 count      |

以上函数会返回一个值，建议给返回字段起一个别名。

其他：

- `count(*)`、`count(1)` 等可以解决不计 null 的问题
- `sum(*)`、`sum(1)` 可实现上述 count 的效果

## 和 DISTINCT 配合

count() 经常与 DISTINCT 组合使用，表示去重后的总数量：

```mysql
-- 有几个班：3
select count(distinct class) as class_qty from students
-- 有几个性别：2
select count(distinct gender) as gender_qty from students
```

## 聚合使用

对数据使用 `GROUP BY` 聚合后必须使用聚合函数指出聚合后想要输出字段的计算方法，以上几个函数便经常使用在聚合操作中。

---

## Hive Sql聚合统计函数

### 计数COUNT

**查询结果总共有多少条，有三种形式：**

- count(*) 返回检索到的行总数，包括包含NULL值的行
- **count(col) 返回为其提供的列为非 NULL 的行数**
- count(DISTINCT col[, col]) 返回所提供的列唯一且非NULL的行数

**需要注意的是：**

- count(1) 与 count(*) 得到的结果一致，包含 null 值
- count(字段) 不计算 null 值
- count(null) 结果恒为 0
- count 中不能使用算术比较运算符（如=，<或<>）

### 去重计数 count(distinct)

```mysql
ELECT count(DISTINCT class) AS Qty
FROM Students；

SELECT count(DISTINCT team, gender) AS Qty
FROM Students
```

但是，对于千万上亿的大量数据来说，上边的方法容易造成「==**数据倾斜**==」，所谓「==**数据倾斜**==」就是指数据的分散度不够，导致大量的数据集中到了一台或者几台机器上计算，造成执行缓慢、卡死等现象。

解决「数据倾斜」可以使用「group by」如：

```mysql
SELECT class,
         gender,
         count(*) AS Qty
FROM Students
GROUP BY class,
         gender
```



### SUM求和

`sum(col)` 返回组中元素的总和或组中列的不同值的总和。

```mysql
SELECT sum(math) AS total
FROM Students;

SELECT class,sum(math) AS total
FROM Students
GROUP BY class;
```

`sum(DISTINCT col)` 可以让去重后的值相加：

```mysql
SELECT sum(DISTINCT age) AS total FROM Students;
SELECT team, sum(DISTINCT age) AS total FROM Students GROUP BY team;
```

### 平均值 AVG

`avg(col)`返回组中元素的平均值或组中列的不同值的平均值。

```mysql
SELECT avg(math) AS total
FROM Students;

SELECT team,
       avg(math) AS total
FROM Students
GROUP BY team;
```

`avg(DISTINCT col)` 可以让去重后的值平均：

```mysql
SELECT avg(DISTINCT age) AS total
FROM Students;

SELECT team,
       avg(DISTINCT age) AS total
FROM Students
GROUP BY team;
```

### 最大最小值 Max Min

`max(col)` 和 `min(col)` 可以取出结果中的最大值和最小值。

```mysql
SELECT max(math) AS math FROM Students；
SELECT class,max(math) AS math FROM Students GROUP BY class;
```



### **==collect_list(col)==**

定义：返回具有重复项的对象列表（array），就是说不会对聚合后的内容去重，可以理解成 python 中的 list 类型转换。

个人理解：取一列中的数据形成 python中的列表形式 

[collect_list/collect_set](collect_listcollect_set.md) 



### **==collect_set(col)==**

返回去除了重复元素的一组对象（array），对聚合后的内容去重，可以理解成 python 的中的 set 类型转换，集合类型中的元素是不能重复的。

<!--可以用两个内置函数实现行转列列转行-->

---



## Hive Sql的操作和运算

### 运算符优先级

| **例子**                       | **操作**                             | **功能说明**   |
| ------------------------------ | ------------------------------------ | -------------- |
| -A                             | unary(+), unary(-), unary(~)         | 一元前缀运算符 |
| A & B                          | bitwise and(&)                       | 按位和         |
| A * B                          | star(*), divide(/), mod(%), div(DIV) | 乘法运算符     |
| A + B                          | plus(+), minus(-)                    | 加法运算符     |
| A ^ B                          | bitwise xor(^)                       | 按位异或       |
| A IS [NOT] (NULL\|TRUE\|FALSE) | IS NULL,IS NOT NULL, ...             | 一元后缀       |
| A \| B                         | bitwise or(\|)                       | 按位或         |
| A \|\| B                       | string concatenate(\|\|)             | 字符串连接     |
| A[B] , A.identifier            | bracket_op([]), dot(.)               | 元素选择器，点 |

<!--不理解，待详细查阅-->



### 关系运算符^不会^

以下运算符比较传递的操作数，并根据操作数之间的比较是否成立来生成TRUE或FALSE值。

| **操作**                 | **操作数类型**                   | **说明**                                                     |
| ------------------------ | -------------------------------- | ------------------------------------------------------------ |
| A = B                    | All primitive types 所有原始类型 | 如果表达式A等于表达式B，则为TRUE，否则为FALSE。              |
| A == B                   | All primitive types              | = 运算符的同义词。                                           |
| **<u>A <=> B</u>**       | All primitive types              | 对于非空操作数，使用EQUAL（=）运算符返回相同的结果，但如果两个均为NULL，则返回TRUE，如果其中之一为NULL，则返回FALSE。(As of version [0.9.0](https://issues.apache.org/jira/browse/HIVE-2810).) |
| A <> B                   | All primitive types              | NULL if A or B is NULL, TRUE if expression A is NOT equal to expression B, otherwise FALSE. |
| A != B                   | All primitive types              | 相当于 <> 不等于操作                                         |
| A < B                    | All primitive types              | 如果A或B为 NULL，则为 NULL；如果表达式A小于表达式B，则为 TRUE；否则为 FALSE |
| A <= B                   | All primitive types              | 如果A或B为NULL，则为NULL；如果表达式A小于或等于表达式B，则为TRUE；否则为FALSE |
| A > B                    | All primitive types              | 如果A或B为NULL，则为NULL；如果表达式A大于表达式B，则为TRUE；否则为FALSE |
| A >= B                   | All primitive types              | 如果A或B为NULL，则为NULL；如果表达式A大于或等于表达式B，则为TRUE；否则为FALSE |
| A [NOT] BETWEEN B AND C  | All primitive types              | 如果A、B或C为空，则为空；如果A大于或等于B且A小于或等于C，则为真；否则为假。这可以通过使用NOT关键字来反转 (始于版本 [0.9.0](https://issues.apache.org/jira/browse/HIVE-2005).)<!--相当于 B<=A<=C--> |
| A IS NULL                | All types                        | 如果表达式A的计算结果为NULL，则为TRUE，否则为FALSE           |
| A IS NOT NULL            | All types                        | 如果表达式A的计算结果为NULL，则为FALSE，否则为TRUE           |
| A IS [NOT] (TRUE\|FALSE) | Boolean types(布尔类型)          | 仅当满足条件时才计算为TRUE. (始于 [3.0.0](https://issues.apache.org/jira/browse/HIVE-13583) ) 注意：NULL是未知的，因此（UNKNOWN是TRUE）和（UNKNOWN是FALSE）都计算为FALSE。<!--不懂,待查询--> |
| A [NOT] LIKE B           | strings                          | 如果A或B为NULL，则为NULL；如果字符串A与SQL简单正则表达式B匹配，则为TRUE；否则为FALSE。比较是逐字进行的。 B中的 _ 字符与A中的任何字符匹配 (类似点 . 在posix正则表达式中)，而B中的%字符与A中任意数量的字符相匹配 (类似于 .* 在 posix 正则表达式中)。**如, 'foobar' like 'foo' 结果为 FALSE 而 'foobar' like 'foo_ _ _' 和 'foobar' like 'foo%' 相同等于 TRUE** |
| A RLIKE B                | strings                          | 如果A或B为NULL，则为NULL；<u>如果A的**任何子字符串**（可能为空）与Java正则表达式B匹配，则为TRUE</u>, 否则 FALSE。例如，“foobar”RLIKE“foo”的计算结果为TRUE， 'foobar' RLIKE '^f.*r$'. 的计算结果也是TRUE。 |
| A REGEXP B               | strings                          | 与 RLIKE 相同                                                |

### 算术运算符^不会^

<!--不理解，待详细查阅-->

以下运算符支持对操作数的各种常见算术运算。 所有返回数字类型； 如果任何操作数为NULL，则结果也为 NULL。

| **操作** | **操作数类型**   | **说明**                                                     |
| -------- | ---------------- | ------------------------------------------------------------ |
| A + B    | All number types | 给出A和B相加的结果。结果的类型与操作数类型的公共父级（在类型层次结构中）相同。例如，因为每个整数都是一个浮点，所以float是一个包含类型的整数，所以float上的+运算符和int将产生一个浮点 |
| A - B    | All number types | 给出从A中减去B的结果。结果的类型与操作数类型的公共父级（在类型层次结构中）相同 |
| A * B    | All number types | 给出A和B相乘的结果。结果的类型与操作数类型的公共父级（在类型层次结构中）相同。请注意，如果乘法导致溢出，则必须将其中一个运算符强制转换为类型层次结构中较高的类型 |
| A / B    | All number types | 给出A除以B的结果。在大多数情况下，结果是双精度类型。当A和B都是整数时，结果是一个双精度类型，但当 [hive.compat](https://cwiki.apache.org/confluence/display/Hive/Configuration+Properties#ConfigurationProperties-hive.compat) 配置参数设置为“0.13”或“最新”，在这种情况下，结果为十进制类型 |
| A DIV B  | Integer types    | 给出A除以B所得的整数部分。例如 17 div 3 结果为5              |
| A % B    | All number types | 给出A除以B的结果提示。结果类型与操作数类型的公共父级（在类型层次结构中）相同 |
| A & B    | All number types | 给出A和B的按位AND的结果。结果的类型与操作数类型的公共父级（在类型层次结构中）相同 |
| A \| B   | All number types | 给出按位或A和B的结果。结果的类型与操作数类型的公共父级（在类型层次结构中）相同 |
| A ^ B    | All number types | 给出A和B的按位异或结果。结果的类型与操作数类型的公共父级（在类型层次结构中）相同 |
| ~A       | All number types | 给出按位而非A的结果。结果的类型与A的类型相同                 |

### 逻辑运算^不会^

<!--不理解，待详细查阅-->

以下运算符为创建逻辑表达式提供支持。 它们都根据操作数的布尔值返回布尔值TRUE，FALSE或NULL。 NULL表现为“未知”标志，因此，如果结果取决于未知状态，则结果本身是未知的。

| **操作**                   | **操作数类型** | **说明**                                                     |
| -------------------------- | -------------- | ------------------------------------------------------------ |
| A AND B                    | boolean        | 如果A和B都为真，则为真，否则为假。如果A或B为空，则为空       |
| A OR B                     | boolean        | 如果A或B或两者都为真，则为真；如果为假，则为空；否则为假     |
| NOT A                      | boolean        | 如果A为FALSE，则为TRUE；如果A为NULL，则为NULL。否则就 FALSE. |
| ! A                        | boolean        | 同 NOT A                                                     |
| A IN (val1, val2, ...)     | boolean        | 如果A等于任何值，则为TRUE。从配置单元0.13开始，语句中支持子查询。[subqueries](https://cwiki.apache.org/confluence/display/Hive/LanguageManual+SubQueries) |
| A NOT IN (val1, val2, ...) | boolean        | 如果A不等于任何值，则为TRUE。从配置单元0.13开始，NOT in语句支持子查询。 [subqueries](https://cwiki.apache.org/confluence/display/Hive/LanguageManual+SubQueries). |
| [NOT] EXISTS (subquery)    |                | 如果子查询返回至少一行，则为TRUE。始于 [Hive 0.13](https://cwiki.apache.org/confluence/display/Hive/LanguageManual+SubQueries). |

### 字符串运算符

| **操作** | **操作数类型** | **操作数类型**                                               |
| -------- | -------------- | ------------------------------------------------------------ |
| A \|\| B | strings        | 连接操作数，`concat(A,B)` 的简写，支持于 [Hive 2.2.0](https://issues.apache.org/jira/browse/HIVE-14580). |

### 复杂类型构造函数^不会^

<!--不理解，待详细查阅-->

以下函数构造复杂类型的实例。

| **操作数类型** | **操作数类型**                    | **说明**                                                     |
| -------------- | --------------------------------- | ------------------------------------------------------------ |
| map            | (key1, value1, key2, value2, ...) | 使用给定的键/值对创建映射                                    |
| struct         | (val1, val2, val3, ...)           | 使用给定的字段值创建结构。结构字段名将为 col1, col2, ....    |
| named_struct   | (name1, val1, name2, val2, ...)   | 使用给定的字段名和值创建结构 (始于 [0.8.0](https://issues.apache.org/jira/browse/HIVE-1360).) |
| array          | (val1, val2, ...)                 | 使用给定元素创建数组                                         |
| create_union   | (tag, val1, val2, ...)            | 使用标记参数指向的值创建联合类型                             |

### 复杂类型的运算符^不会^

<!--不理解，待详细查阅-->

以下运算符提供了访问复杂类型的元素的机制。

| **操作** | **操作数类型**                      | **说明**                                                     |
| -------- | ----------------------------------- | ------------------------------------------------------------ |
| A[n]     | A is an Array and n is an int       | 返回数组A中的第n个元素。第一个元素的索引为0。如，如果A是由以下各项组成的数组： ['foo', 'bar'] 然后 A[0] 返回 'foo' 而 A[1] 返回 'bar'. |
| M[key]   | M is a Map<K, V> and key has type K | 返回与映射中的键对应的值。 如，如果 M 由以下内容构成 {'f' -> 'foo', 'b' -> 'bar', 'all' -> 'foobar'} 然后 M['all'] 返回 'foobar'. |
| S.x      | S is a struct                       | 返回 S 的 x 字段。例如，结构 foobar {int foo，int bar}，foobar.foo 返回存储在结构的 foo 字段中的整数 |

----

