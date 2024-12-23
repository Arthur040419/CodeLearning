# JavaWeb快速入门

参考视频：[05-DDL-操作数据库_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Qf4y1T7Hx?spm_id_from=333.788.player.switch&vd_source=f3cb3ea986b26c6910b4df6d37acd60d&p=6)

## 05-DDL-操作数据库

命令行登录数据库

```mysql
mysql -u root -p			-- 然后输入密码进入mysql操作环境
```



![image-20241222101745304](./pictures/image-20241222101745304.png)



### 相关命令

#### 查询数据库命令

```mysql
show databases;
```

![image-20241222102127280](./pictures/image-20241222102127280.png)



#### 创建数据库命令

```mysql
create database 数据库名称;
create database testdb;
create database if not exists testdb;		-- 创建testdb数据库如果该数据库不存在
```

![image-20241222102306037](./pictures/image-20241222102306037.png)



#### 删除数据库命令

```mysql
drop database 数据库名称;
drop database testdb;
drop database if exists testdb;			-- 删除数据库，如果该数据库存在
```

![image-20241222102643344](./pictures/image-20241222102643344.png)

#### 使用数据库命令

```mysql
select database();			-- 查看当前使用的数据库
use 数据库名称;				-- 使用指定数据库
use eduadmsys-final;
```

![image-20241222102853345](./pictures/image-20241222102853345.png)



## 06-DDL-操作表-查询表&创建表

#### 查询表命令

```mysql
show tables;
```

![image-20241222103401027](./pictures/image-20241222103401027.png)

#### 查询表结构命令

```mysql
desc 表名称;
desc teacher;
```

![image-20241222103524810](./pictures/image-20241222103524810.png)

#### 创建表命令

```mysql
create table 表名(
	字段名 字段类型,
    字段名 字段类型,
    字段名 字段类型		--最后一个字段不能加逗号,
);

create table tb_user(
	id int,
    username varchar(25),		--括号里面要指定字段的长度
    password varchar(32)
);
```

![image-20241222104048240](./pictures/image-20241222104048240.png)



## 07-DDL-操作表-数据类型

#### mysql的主要数据类型

![image-20241222104319508](./pictures/image-20241222104319508.png)

熟悉一下mysql的数据类型的使用

创建以下学生表

![image-20241222105038708](./pictures/image-20241222105038708.png)

```mysql
create table student(
	id int,
    name varchar(10),
    gender char(1),
    birthday date,
    score double(5,2),				-- 使用double类型，括号中前一个数字表示最大长度，后一个数字表示保留几位小数
    email varchar(64),
    tel varchar(15),
    status tinyint					-- 学生状态一般也就几个，所以用tinyint即可
);
```



## 08-DDL-操作表-修改&删除

#### 删除表命令

```mysql
drop table 表名;
drop table tb_user;
```

![image-20241222105948530](./pictures/image-20241222105948530.png)

### 修改表的一系列命令

#### 修改表名

```mysql
alter table 表名 rename to 新的表名;
alter table student rename to stu;
```

![image-20241222110503916](./pictures/image-20241222110503916.png)



#### 添加一列

```mysql
alter table 表名 add 列名 数据类型;
alter table stu add class_id int;
```

![image-20241222110635036](./pictures/image-20241222110635036.png)

#### 修改数据类型

```mysql
alter table 表名 modify 列名 新的数据类型;
alter table stu modify status varchar(10);
```

![image-20241222110830896](./pictures/image-20241222110830896.png)

#### 修改列名和数据类型

```mysql
alter table 表名 change 列名 新的列名 新的数据类型;
alter table stu change class_id class_name varchar(10);
```

![image-20241222110943532](./pictures/image-20241222110943532.png)

#### 删除列

```mysql
alter table 表名 drop 列名;
alter table stu drop class_name;
```

![image-20241222111042727](./pictures/image-20241222111042727.png)

## 10-DML-操作数据-添加&修改&删除

### 添加系列命令

#### 给指定列添加数据

```mysql
insert into 表名(列名1,列名2,....) values(值1,值2,...);
insert into stu(id,name) values(1,'张三');
```

![image-20241222115331588](./pictures/image-20241222115331588.png)

#### 给全部列添加数据

```mysql
insert into 表名 values(值1,值2,....);			-- 表名后面的括号里的列名可以省略也可以全写
insert into 表名(列名1,列名2,等全部列名) values(值1,值2,...);
```

![image-20241222115742754](./pictures/image-20241222115742754.png)

#### 批量添加数据

```mysql
insert into 表名 values(值1,值2,...),(值1,值2,...),(值1,值2,...)....;
insert into 表名(列名1,列名2,...) values (值1,值2,...),(值1,值2,...),(值1,值2,...)....;
```

![image-20241222120035196](./pictures/image-20241222120035196.png)

### 修改数据命令

```mysql
update 表名 set 列名1=值1,列名2=值2,.....;			-- 如果不添加where条件，该命令会对所有行执行修改操作
update 表名 set 列名1=值1,列名2=值2,..... where 某个列=某个值;
```

![image-20241222120234138](./pictures/image-20241222120234138.png)

### 删除数据命令

```mysql
delete from 表名 where 条件;					-- 如果不添加where条件，该命令会删除所有的行
delete from 表名;								 -- 删除所有行
```

![image-20241222120725492](./pictures/image-20241222120725492.png)

![image-20241222120742410](./pictures/image-20241222120742410.png)

## 11-DQL-基础查询

#### 查询多个字段

```mysql
select 字段1,字段2,..... from 表名;
select * from 表名;					-- 实际业务中不建议使用，若要查询全部，仍然要写出全部字段
```

![image-20241222141421234](./pictures/image-20241222141421234.png)

#### 去除重复记录

```mysql
select distinct 字段1,字段2,.... from 表名; 		-- 只需加上distinct关键字
```

![image-20241222141544119](./pictures/image-20241222141544119.png)

#### 为查询字段起别名

```mysql
select 字段1 as 别名1,字段2 as 别名2,...... from 表名;			-- as可省略
select 字段1 别名1,字段2 别名2,..... from 表名;
```

![image-20241222141719298](./pictures/image-20241222141719298.png)

## 12-DQL-条件查询

```mysql
select * from 表名 where 条件;
```

### 几个条件查询的例子

#### 查询年龄大于20岁的学员信息

```mysql
select * from stu where age >20;
```

![image-20241222143907059](./pictures/image-20241222143907059.png)

#### 查询年龄大于等于20岁的学员信息

```mysql
select * from stu where age >=20;
```

![image-20241222144331639](./pictures/image-20241222144331639.png)

#### 查询年龄大于等于20岁并且小于30岁的学员信息

```mysql
select * from stu where age >=20 and age < 30;
select * from stu where age >=20 && age <30;			-- 不推荐使用&&
select * from stu where age between 20 and 30;
```

![image-20241222144514157](./pictures/image-20241222144514157.png)

![image-20241222144536371](./pictures/image-20241222144536371.png)

#### 查询入学日期在‘1998-09-01’到‘1999-09-01’之间的学员信息

```mysql
select * from stu where hire_date between '1998-09-01' and '1999-09-01' ;  -- date类型数据也支持比较
```

![image-20241222144734348](./pictures/image-20241222144734348.png)

#### 查询年龄等于18岁的学院信息

```mysql
select * from stu where age = 18;
```

![image-20241222144811168](./pictures/image-20241222144811168.png)

#### 查询年龄不等于18岁的学员信息

```mysql
select * from stu where age != 18;
```

![image-20241222144850640](./pictures/image-20241222144850640.png)

#### 查询年龄等于18岁或20岁或22岁的学员信息

```mysql
select * from stu where age=18 or age=20 or age=22;
select * from stu where age=18||age=20||age=22;				-- 不推荐使用||
select * from stu where age in 一个集合;
select * from stu where age in (18,20,22);
```

![image-20241222145103109](./pictures/image-20241222145103109.png)

#### 查询英语成绩为null的学员信息

要注意的是查询为null的数据不能使用 = 与 !=来比较，要使用 is null 或 is not null

```mysql
select * from stu where english is null;
select * from stu where english is not null;
```

![image-20241222145311916](./pictures/image-20241222145311916.png)

![image-20241222145325651](./pictures/image-20241222145325651.png)

### 模糊查询

`_`代表单个字符，`%`代表任意字符

#### 查询姓‘马‘的学员信息

```mysql
select * from stu where name like '马%';
```

![image-20241222145557450](./pictures/image-20241222145557450.png)

#### 查询第二个字是’花‘的学员信息

```mysql
select * from stu where name like '_花%';
```

![image-20241222145643621](./pictures/image-20241222145643621.png)

#### 查询名字中包含’德‘的学员信息

```mysql
select * from stu where name like '%德%';
```

![image-20241222145718899](./pictures/image-20241222145718899.png)

## 13-DQL-排序查询

排序方式主要有升序排序`asc`，这是默认的；还有一个降序排序`desc`

```mysql
select 字段1,字段2,.... from 表名 order by 排序字段名1 排序方式1 ,排序字段名2 排序方式2,....;
```

#### 按照年龄升序排列

```mysql
select * from stu order by age asc;				-- asc 也可以不写，默认升序排列
```

![image-20241222150936796](./pictures/image-20241222150936796.png)

#### 按照数学成绩降序排列

```mysql
select * from stu order by math desc;
```

![image-20241222151016004](./pictures/image-20241222151016004.png)

#### 按照数学成绩降序排列，如果数学成绩一样，再按照英语成绩升序排列

```mysql
select * from stu order by math desc , english asc;
```

![image-20241222151132519](./pictures/image-20241222151132519.png)

## 14-DQL-聚合函数

聚合函数是将一列数据作为整体，进行纵向计算。

主要有以下5个聚合函数

```mysql
/*
	count		统计数量，如果有值为null，则null不参与统计
	max			求某一列的最大值
	min			求某一列的最小值
	sum			求某一列值的总和
	avg			求某一列的平均值
	需要注意，null也不参与计算比较
*/
select 聚合函数名(列名) from 表名;
```

#### 统计班级一共有多少个学生

```mysql
select count(name) from stu;
```

![image-20241222152306993](./pictures/image-20241222152306993.png)

#### 查询数学成绩的最高分

```mysql
select max(math) from stu;
```

![image-20241222152359781](./pictures/image-20241222152359781.png)

#### 查询数学成绩的最低分

```mysql
select min(math) from stu;
```

![image-20241222152455727](./pictures/image-20241222152455727.png)

#### 查询数学成绩的总分

```mysql
select sum(math) from stu;
```

![image-20241222152527490](./pictures/image-20241222152527490.png)

#### 查询数学成绩的平均分

```mysql
select avg(math) from stu;
```

![image-20241222152555153](./pictures/image-20241222152555153.png)

#### 查询英语成绩的最低分

英语成绩中的null值不会参与比较

```mysql
select min(english) from stu;
```

![image-20241222152632782](./pictures/image-20241222152632782.png)

## 15-DQL-分组查询

```mysql
select 字段列表 from 表名 [where 条件语句] group by 分组字段名 [having 筛选语句]
```

要注意的是分组查询只能查询被分组的字段和聚合函数，查询其他字段是没有意义的

#### 查询男同学和女同学各自的数学平均分

```mysql
select sex,avg(math) from stu group by sex;			-- sex是分组字段 avg(math)是聚合函数
```

![image-20241222153731514](./pictures/image-20241222153731514.png)

#### 查询男同学和女同学各自的数学平均分，以及各自的人数

```mysql
select sex,avg(math),count(*) from stu group by sex;
```

![image-20241222153838605](./pictures/image-20241222153838605.png)

#### 查询男同学和女同学各自的数学平均分，以及各自的人数，并且要求分数低于70分的不参与分组

```mysql
select sex,avg(math),count(*) from stu where math >=70 group by sex;
```

![image-20241222153959757](./pictures/image-20241222153959757.png)

#### 查询男同学和女同学各自的数学平均分，以及各自的人数，并且要求分数低于70分的不参与分组、分组后人数大于2的才显示



```mysql
select sex,avg(math),count(*) from stu where math >=70 group by sex having count(*)>2;
```

![image-20241222154126639](./pictures/image-20241222154126639.png)

## 16-DQL-分页查询

```mysql
select 字段列表 from 表名 limit 起始索引, 查询条目数;
```

起始索引的计算公式：

起始索引=(当前查询的页码-1)*查询条目数

#### 从0开始查询，查询3条数据

```mysql
select * from stu limit 0,3;
```

![image-20241222161407573](./pictures/image-20241222161407573.png)

#### 每页显示3条数据，查询第1页数据

```mysql
select * from stu limit 0,3;
```

#### 每页显示3条数据，查询第2页数据

```mysql
select * from stu limit 3,3;
```

![image-20241222161456363](./pictures/image-20241222161456363.png)

#### 每页显示3条数据，查询第3页数据

```mysql
select * from stu limit 6,3;
```

![image-20241222161528680](./pictures/image-20241222161528680.png)

## 08-多表查询-内连接&外连接

### 内连接

```mysql
select 字段列表 from 表1,表2.... where 条件;			-- 这是隐式内连接
select 字段列表 from 表1 [inner] join 表2 on 条件;		-- 这是显式内连接，其中inner可以省略
```

内连接是查询 表1 与 表2相交的数据

![image-20241222211732864](./pictures/image-20241222211732864.png)

#### 隐式内连接查询emp和dept的数据

```mysql
select * from emp,dept where emp.dep_id=dept.did;			-- 隐式内连接
```

![image-20241222212933054](./pictures/image-20241222212933054.png)

#### 隐式内连接查询emp的name,gender,和dept表的dname

```mysql
select emp.name,emp.gender,dept.dname from emp,dept where emp.dep_id=dept.did;
```

![image-20241222213013685](./pictures/image-20241222213013685.png)

#### 显示内连接查询数据

```mysql
select * from emp inner join dept on emp.dep_id=dept.did;
select * from emp join dept on emp.dep_id=dept.did;				-- 省略inner
```

![image-20241222213247760](./pictures/image-20241222213247760.png)

### 外连接

#### 左外连接

```mysql
select 字段列表 from 表1 left [outer] join 表2 on 条件;				-- outer可省略

```

查询emp表的所有数据及对应的部门信息

```mysql
select * from emp left join dept on emp.dep_id=dept.did;
```

![image-20241222213900157](./pictures/image-20241222213900157.png)

#### 右外连接

```mysql
select 字段列表 from 表1 right [outer] join 表2 on 条件;			-- outer可省略 
```

查询dept表的所有数据及其对应的员工信息

```mysql
select * from emp right join dept on emp.dep_id = dept.did;
```

![image-20241222214033673](./pictures/image-20241222214033673.png)

## 09-多表查询-子查询

子查询根据查询结果的不同，其作用也不同，主要有三种查询情况：1.单行单列 2.多行单列 3.多行多列

#### 子查询结果为单行单列

可以作为条件值来进行条件判断

```mysql
select 字段列表 from 表1 where 表1.某个字段 {=,>,<,...} (子查询);
select * from emp where emp.salary > (
	select salary from emp where emp.name = '猪八戒'					--子查询不能带分号;
);		-- 查询工资大于猪八戒的所有员工信息，子查询先查出猪八戒的工资.
```

![image-20241222215923811](./pictures/image-20241222215923811.png)

#### 子查询结果为多行单列

可以作为一个集合条件，查询在这个集合内的数据，使用in关键字进行条件判断

```mysql
select 字段列表 from 表1 where 表1.某个字段 in (子查询);
-- 查询财务部和市场部所有员工信息
select * from emp where emp.dep_id in (
	select did from dept where dname in ('财务部','市场部')
);
```

![image-20241222220343617](./pictures/image-20241222220343617.png)

#### 子查询结果为多行多列

可以作为一个虚拟表来与其他表进行连接

```mysql
select 字段列表 from 表1 left join (
	select 字段列表 from 表2 where 条件
) on 连接条件;

-- 查询入职日期是'2011-11-11'之后的员工信息和部门信息
select * from (
	select * from emp where emp.join_date > '2011-11-11'
) as t1 left join dept on t1.dep_id=dept.did;
```

![image-20241222220939097](./pictures/image-20241222220939097.png)

## 10-多表查询-案例

相关数据表的模型如下：

![image-20241222222712326](./pictures/image-20241222222712326.png)

```mysql
-- 1.查询所有员工信息。查询员工编号，员工姓名，工资，职务名称，职务描述
SELECT
  emp.id,
  emp.ename,
  emp.salary,
  job.jname,
  job.description 
FROM
  emp
  JOIN job ON emp.job_id = job.id;
-- 2.查询员工编号，员工姓名，工资，职务名称，职务描述，部门名称，部门位置
SELECT
  emp.id,
  emp.ename,
  emp.salary,
  job.jname,
  job.description,
  dept.dname,
  dept.loc 
FROM
  emp,
  job,
  dept 
WHERE
  emp.job_id = job.id 
  AND emp.dept_id = dept.id;-- 隐式内连接
SELECT
  emp.id,
  emp.ename,
  emp.salary,
  job.jname,
  job.description,
  dept.dname,
  dept.loc 
FROM
  emp
  JOIN job ON emp.job_id = job.id
  JOIN dept ON emp.dept_id = dept.id;-- 显式内连接
-- 3.查询员工姓名，工资，工资等级
SELECT
  emp.ename,
  emp.salary,
  t1.grade 
FROM
  emp
  LEFT JOIN salarygrade t1 ON emp.salary BETWEEN t1.losalary 
  AND t1.hisalary;		-- 外连接方法
  
SELECT
  emp.ename,
  emp.salary,
  t1.grade 
FROM
  emp,
  salarygrade t1 
WHERE
  emp.salary BETWEEN t1.losalary 
  AND t1.hisalary;-- 内连接方法
-- 4.查询员工姓名，工资，职务名称，职务描述，部门名称，部门位置，工资等级
SELECT
  emp.id,
  emp.ename,
  emp.salary,
  job.jname,
  job.description,
  dept.dname,
  dept.loc,
  t1.grade 
FROM
  emp
  JOIN job ON emp.job_id = job.id
  JOIN dept ON emp.dept_id = dept.id
  JOIN salarygrade t1 ON emp.salary BETWEEN t1.losalary 
  AND t1.hisalary;-- 显式内连接
-- 5.查询出部门编号、部门名称、部门位置、部门人数
SELECT
  dept.id,
  dept.dname,
  dept.loc,
  count 
FROM
  dept,
  (SELECT dept_id, count(*) count FROM emp GROUP BY dept_id) t1 
WHERE
  dept.id = t1.dept_id;
```



## 01-JDBC简介 快速入门

使用jdbc的步骤如下

#### 0.首先创建工程，导入数据库驱动jar包

创建一个空工程，进入project structure设置jdk和language level

![image-20241223132000098](./pictures/image-20241223132000098.png)

然后创建一个模块，在模块里面创建一个lib文件夹，将驱动jar包放入lib文件夹并将该文件夹设置为library文件夹

![image-20241223125910477](./pictures/image-20241223125910477.png)

设置该文件夹的有效范围

![image-20241223130024971](./pictures/image-20241223130024971.png)

#### 1.注册驱动

```java
Class.forName("com.mysql.jdbc.Driver");
```

#### 2.获取连接

```java
String url = "jdbc:mysql://127.0.0.1:3306/testdb";
String username = "root";
String password = "对应的数据库密码";
Connection conn = DriverManager.getConnection(url,username,password);
```

#### 3.定义sql语句

```java
String sql = "update account set money = 2000 where id =1 ";
```

#### 4.获取执行sql对象

```java
Statement stmt = conn.createStatement();
```

#### 5.执行sql

```java
int count = stmt.executeUpdate(sql);			//返回结果为受影响的行数
```

#### 6.处理返回结果

```java
System.out.println(count);
```

#### 7.释放资源

```java
stmt.close();
conn.close();
```

![image-20241223134341400](./pictures/image-20241223134341400.png)

修改成功

![image-20241223134357995](./pictures/image-20241223134357995.png)

## 02-JDBC-API详解-DriverManager

DriverManager是驱动管理类，其主要有以下两个作用：

1.注册驱动

2.获取sql连接对象

DriverManager是一个工具类，其函数都是静态函数，因此可以直接通过类名来访问成员函数

```java
Connection conn = DriverManager.getConnection(url,username,password);
```

url的定义详解如下

```java
//设置url的完整语法
String url = "数据库协议://数据库ip地址:数据库端口号/要访问的数据库名?参数键值对1&参数键值对2....";
//后面的键值对可以进行某些设置，比如配置useSSL=false参数，禁用安全连接方式，解决警告提醒
//如果是访问本地数据库并且端口为3306，ip地址还可以省略
String url = "jdbc:mysql:///testdb?useSSL=false";
```

警告提醒：

![image-20241223140302587](./pictures/image-20241223140302587.png)

禁用安全连接方式，解决警告提醒

![image-20241223140741243](./pictures/image-20241223140741243.png)

## 03-JDBC-API详解-Connection

Connection是数据库连接对象，其主要作用如下：

1.获取执行sql的对象

2.管理事务

这里先将管理事务，第一个后面讲

```java
//connection提供了三个管理事务的函数
//1.setAutoCommit(boolean autoCommit);	true为自动提交事务，false为手动提交事务
//2.commit()							提交事务
//3.roolback()							回滚事务
```

修改前面快速入门代码，使其要么修改两个数据，要么一个也不修改

```java
//1.注册驱动
Class.forName("com.mysql.jdbc.Driver");
//2.获取连接
String url ="jdbc:mysql:///testdb?useSSL=false";
String username="root";
String password="gt1303190518";
Connection conn = DriverManager.getConnection(url,username,password);
//3.定义sql语句
String sql1="update account set money=2000 where id = 1";
String sql2="update account set money=3000 where id = 2";
//4.获取执行sql对象
Statement stmt = conn.createStatement();
conn.setAutoCommit(false);                  //设置手动提交事务
        try {

            //5.执行sql语句
            int count1 = stmt.executeUpdate(sql1);
            int i=3/0;							//这里会抛出异常，使得第一个sql成功执行，第二个sql不能执行
            
            int count2 = stmt.executeUpdate(sql2);
            //6.处理执行结果
            System.out.println(count1);
            System.out.println(count2);
            conn.commit();                      //提交事务
        } catch (SQLException e) {
            conn.rollback();                    //捕获到错误就回滚
            throw new RuntimeException(e);
        }
//7.释放资源
stmt.close();
conn.close();
```

如果没有报错，数据会被正常修改，但如果让int i = 3/0;这行代码生效的话，结果如下

![image-20241223153651936](./pictures/image-20241223153651936.png)

![image-20241223153703910](./pictures/image-20241223153703910.png)

控制台第一行打印出来的1就是第一个sql执行的结果，sql1成功修改了一行数据，但数据库里面并没有看到sql1的修改，因为事务被回滚了，此时如果我们再把回滚、提交、设置自动提交的代码去掉，就会发现sql1的修改成功了，但sql2没有执行

![image-20241223154001917](./pictures/image-20241223154001917.png)

## 04-JDBC-API详解-Statement

Statement的作用是执行sql语句，其提供两种执行函数

1.执行DML、DDL语句，即对数据库的修改语句

```java
int executeUpdate(sql);					//返回受影响的行数
```

前面快速入门里的代码就是这个

2.执行DQL语句，即查询语句

```java
ResultSet executeQuery(sql);			//返回ResultSet结果集对象
```

## 05-JDBC-API详解-ResultSet

ResultSet是查询语句的结果的集合，如果要取出里面的数据，就要通过一个抽象的“光标”一行一行去访问里面的数据，其提供了以下用于访问里面数据的函数

#### 1.next()函数

```java
boolean next();					//将访问光标向下移动一行，并判断该行是否是有效行，有效行就返回true
```

#### 2.getxxx函数

```java
xxx getxxx(索引或字段名);			//xxx代表数据类型，索引是指要获取的数据在第几列，从1开始
int getInt("id");
String getString(2);
```

总获取数据方式是通过一个while循环来遍历所有行

```java
		//1.注册驱动
        Class.forName("com.mysql.jdbc.Driver");
        //2.获取连接
        String url ="jdbc:mysql:///testdb?useSSL=false";
        String username="root";
        String password="gt1303190518";
        Connection conn = DriverManager.getConnection(url,username,password);
        //3.定义sql语句
        String sql1="select * from account";
        //4.获取执行sql对象
        Statement stmt = conn.createStatement();
        //5.执行sql语句
        ResultSet res=stmt.executeQuery(sql1);
        //6.获取查询的数据
        while(res.next()){
            System.out.println(res.getInt(1));          //通过索引来获取数据
            System.out.println(res.getString("name"));  //通过字段名来获取数据
            System.out.println(res.getDouble(3));
            System.out.println("---------------");
        }
        //7.释放资源
        res.close();
        stmt.close();
        conn.close();
```

![image-20241223160816926](./pictures/image-20241223160816926.png)

#### 案例

查询account账户表数据，将其封装为Account对象中，并且存储到ArrayList集合中

首先建立一个Account的实体类

![image-20241223161651156](./pictures/image-20241223161651156.png)

然后将数据封装成Account对象并打印出来

```java
public static void main(String[] args) throws ClassNotFoundException, SQLException {
        //1.注册驱动
        Class.forName("com.mysql.jdbc.Driver");
        //2.获取连接
        String url ="jdbc:mysql:///testdb?useSSL=false";
        String username="root";
        String password="gt1303190518";
        Connection conn = DriverManager.getConnection(url,username,password);
        //3.定义sql语句
        String sql1="select * from account";
        //4.获取执行sql对象
        Statement stmt = conn.createStatement();
        //5.执行sql语句
        ResultSet res=stmt.executeQuery(sql1);
        //6.获取查询的数据
        //建立list集合
        ArrayList<Account> list = new ArrayList<>();
        while(res.next()){
            //创建实体
            Account account=new Account();

            account.setId(res.getInt(1));          //通过索引来获取数据
            account.setName(res.getString("name"));  //通过字段名来获取数据
            account.setMoney(res.getDouble(3));
            list.add(account);
        }
        System.out.println(list);
        //7.释放资源
        res.close();
        stmt.close();
        conn.close();
    }
```

![image-20241223162623352](./pictures/image-20241223162623352.png)

 

## 06-JDBC-API详解-PreparedStatement-SQL注入

PreparedStatement是预编译sql语句执行类，是Statement的一个继承类，同样是用来执行sql语句的，但是它可以放置SQL注入。

#### 什么是SQL注入

```java
//通常我们用于查询的sql语句是这样定义的
String name="username";
String pwd="123";				//这是一验证用户登录的查询语句
//sql语句是通过字符串拼接出来的
String sql="select * from tb_user where username= '"+name+"'and password='"+pwd+"'";

//然后根据查询结果，如果查询结果大于0，则表示存在用户且密码正确，则允许登录，否则不允许登录
```

而sql注入就是通过输入相关字符来达到修改sql语句的目的

```java
//举个例子
//这里不管用户名输什么
//只要对password输入
String pwd = "0' or '1' = '1'";
//此时sql语句就变成了 select * from tb_user where username = 'username' and password='0' or '1'= '1'
//而这个sql语句由于后面的or ‘1’=’1‘,不管怎样都能查出所有的数据，也就是会导致最终判断结果>0成立，从而使得可以登录成功

```

输入正确的账号密码登录

![image-20241223165421504](./pictures/image-20241223165421504.png)

sql注入方式登录成功

![image-20241223165831338](./pictures/image-20241223165831338.png)

## 06-JDBC-API详解-PreparedStatement

如何解决sql注入，这就要用到PreparedStatement。

### 使用PreparedStatement的步骤

#### 1.获取PreparedStatement对象

```java
//要使用PreparedStatement的话就要先定义sql语句，且语句中的参数值要用?替代
//定义sql语句
String sql="select * from tb_user where username=? and password = ?";
//获取对象,将sql语句传入构造函数来获取PreparedStatement对象
Connection conn = DriverManager.getConnection(url,username,password);			//先获取连接
PreparedStatement pstmt=conn.preparedStatement(sql);
```



#### 2.设置参数值

```java
//PreparedStatement有 setxxx(参数1,参数2)函数
//xxx代表数据类型
//参数1代表?的位置,从1开始
//参数2代表要替换的值
pstmt.setString(1,name);
pstmt.setString(2,pwd);
```

#### 3.执行sql

```java
//通过PreparedStatement执行sql语句不需要再传递sql语句
//直接使用函数executeUpdate()或executeQuery()来执行
pstmt.executeQuery();
```

```java
public static void main(String[] args) throws ClassNotFoundException, SQLException {
        //1.注册驱动
        Class.forName("com.mysql.jdbc.Driver");
        //2.获取连接
        String url ="jdbc:mysql:///testdb?useSSL=false";
        String username="root";
        String password="gt1303190518";
        Connection conn = DriverManager.getConnection(url,username,password);
        //3.定义sql语句
        String name="fjdaklfjla";
        String pwd="0' or '1' = '1";
        String sql1="select * from tb_user where username=?and password=?";
        System.out.println(sql1);
        //4.获取执行sql对象
        PreparedStatement pstmt = conn.prepareStatement(sql1);
        //设置参数值
        pstmt.setString(1,name);
        pstmt.setString(2,pwd);
        //5.执行sql语句
        ResultSet res=pstmt.executeQuery();
        //6.处理执行结果
        if(res.next()){
            System.out.println("登录成功");
        }else{
            System.out.println("登录失败");
        }
        //7.释放资源
        res.close();
        pstmt.close();
        conn.close();
    }
```





通过这样修改sql注入便不再生效

![image-20241223171655268](./pictures/image-20241223171655268.png)

#### 注意事项

使用预编译性能会更好，但mysql默认是没有开启这个功能的，所以我们要在获取与数据库连接的时候去将它打开

```java
String url = "jdbc:mysql:///testdb?useSSL=false&useServerPrepStmts=true";
String username = "root";
String password = "对应的数据库密码";
Connection conn = DriverManager.getConnection(url,username,password);
```

## 09-数据库连接池-简介&Druid使用

Druid使用步骤

#### 1.导入jar包

#### 2.定义配置文件

```properties
driverClassName=com.mysql.jdbc.Driver
url=jdbc:mysql:///testdb?useSSL=false&useServerPrepStmts=true
username=root
password=gt1303190518
#最小连接数
initialSize=5
#最大连接数
maxActive=10
#最大等待时间
maxWait=3000
```



#### 3.加载配置文件

```java
Properties prop = new Properties();				
prop.load(new FileInputStream("src/druid.properties"));			//记得做异常处理
```

#### 4.获取数据库连接池对象

```java
DataSource datasource=DuridDataSourceFactory.createDataSource(prop);		
```

#### 5.获取连接

```java
Connection connection = datasource.getConnection();
```

```java
public class JDBCDemo {
    public static void main(String[] args) throws Exception {
        //1.导入Durid jar包
        //2.定义配置文件
        //3.加载配置文件
        Properties prop = new Properties();
        prop.load(new FileInputStream("src/druid.properties"));
        //4.获取数据库连接池对象
        DataSource dataSource= DruidDataSourceFactory.createDataSource(prop);       //根据配置文件建立连接池
        //5.获取连接
        Connection connection= dataSource.getConnection();
        System.out.println(connection);
    }
}
```

![image-20241223215514571](./pictures/image-20241223215514571.png)
