# MySQL 命令

## 基础内容

### SQL语法规则

- SQL大小写不敏感

### 数据类型

- 整数 `int`
- 字符串 `char`,当字符串长度不确定时使用`varchar(50)`括号内为最大字符数
- 真伪值 `bool`
- 日期    `date`

**获取数据类型的帮助：**`? data types` 

---

### 一些缩写

- 数据库 Database --> DB
- 数据库管理系统 Database Management System --> DBMS
- 关系型数据库管理系统 Relational Database Management System --> RDBMS
- 数据库管理员 Database Administrator --> DBA

---

## 创建和删除数据库

- **创建数据库：** `create database name default charset utf8mb4;`

> default后面的内容是为了兼容更早版本的SQL
> 
> 不要忘记分号！

- **删除数据库：** `drop database name;` 或者 `drop database if exists name;`

> 这是一个不可逆操作！程序不会给你确认选项而是直接删除，慎重使用！

---

## 对现有数据库的操作

**更改数据库字符集：** `alter database name default charset gbk;`

**展示系统中存在的数据库：** `show databases;`

**切换到需要使用的某数据库：** `use database_name;`

**显示当前数据库中的二维表：** `show tables;`

**展示当前的表**：`desc tb_name;`

---

## 二维表

### 创建一个二维表

**一般创建：** `create table tb_name (header1, header2);`创建一个有两个headers的二维表

> 再给二维表起名时，为了符合习惯会在名字前加上tb_

**创建时声明数据类型：**`create table tb_name (header1 int, header2 char);`空格+数据类型

**创建时增加限制条件和默认值：**

```sql
create table tb_student
(
    stu_id int not null,
    stu_name varchar(50) not null,
    stu_sex char(1) default 'M',
    stu_birthdate date default '2000-01-01'
);
```

**增加comment**

```sql
create table tb_student
(
    stu_id int not null comment '学号',
    stu_name varchar(50) not null comment '姓名',
    stu_sex char(1) default 'M' comment '性别',
    stu_birthdate date default '2000-01-01' comment '生日'
)engine = innodb comment '学生表';
```

> `engine = innodb`在这里的作用也是为了向下兼容

如果需要**检查创建某table时所用的命令语句**，输入 `show create table tb_student;`

**删除某table：** `drop table if exists tb_name; `

**把某个表头设置为主要键(Primary Key)：**

```sql
CREATE TABLE tb_name
(
    header_1 int
    header_2 varchar(20)
    PRIMARY KEY(header_1)
);
```

---

### 修改一个二维表

**为现存的表新加一个列column：** 

```sql
alter table tb_student add column stu_addr varchar(500) default '' comment '家庭住址;'

alter table tb_student add column stu_tel char(11) not null comment '联系方式;'
```

**删除一个列**，和添加列相似的语法，把add改为drop

```sql
alter table tb_student drop column stu_tel;
```

**修改某个列**

只修改数据类型：

```sql
alter table tb_student modify column stu_sex bool default 1 comment '性别‘；
```

全部修改：

```sql
alter table tb_student change column stu_sex stu_gender bool default 1 comment '性别‘；
```

**修改表的名字：**

```sql
alter table tb_student rename to tb_test；
```

**为表填写内容**

```sql
INSERT INTO tb_name VALUES (value1,value2);
```

**更改某特定键的值**

```sql
UPDATE tb_name
SET stu_sex = 'F'
WHERE stu_id = '12345';
```

---

## SELECT 和 FROM 的用法

**参照表：** tb_Product

| product_id | product_name | product_type | sale_price | purchase_price | regist_date |
| ---------- | ------------ | ------------ | ---------- | -------------- | ----------- |
| 0001       | T恤衫          | 衣服           | 1000       | 500            | 2009-09-20  |
| 0002       | 打孔器          | 办公用品         | 500        | 320            | 2009-09-11  |
| 0003       | 运动T恤         | 衣服           | 4000       | 2800           | 2009-       |
| 0004       | 菜刀           | 厨房用品         | 3000       | 2800           | 2009-09-20  |
| 0005       | 高压锅          | 厨房用品         | 6800       | 5000           | 2009-01-15  |
| 0006       | 叉子           | 厨房用品         | 500        |                | 2009-09-10  |
| 0007       | 擦菜板          | 厨房用品         | 880        | 790            | 2008-04-28  |
| 0008       | 圆珠笔          | 办公用品         | 100        |                | 2009-11-11  |

**查询一个表的内容**，查看表的内容：`select * from tb_Product;`

**显示表中A、B、C列的内容：**`select product_id, product_name from tb_Product;`

**显示表中A、B、C列的内容，并为其安排别名：**

```sql
SELECT
    product_id AS id,
    product_name AS name
FROM tb_Product;
```

**显示表中A列下，不重复的内容**： `select distinc regist_date from tb_Product;`

**显示选定内容时，填充常数**：`SELECT ''`

---

## 表达式、条件语句和运算

### 条件语句

**显示所有办公用品的行：**

```sql
SELECT * FROM tb_Product
WHERE product_type = '办公用品';
```

**显示所有日期是2008年的行：**

```sql
SELECT * FROM tb_Product  
WHERE EXTRACT(YEAR FROM regist_date) = '2008';
```

**显示所有价格低于1000的行：**

```sql
SELECT * FROM tb_Product
WHERE purchase_price < 1000;
```

### 运算

四则运算：`+ - * /`

`%`取模（求余数），e.g. 10%3=1。

> 对NULL进行的任何运算，结果都会是NULL

**显示购买价格打八折的效果**

```sql
SELECT
    product_name AS Name,
    purchase_price AS Previos_Price,
    purchase_price*0.8 AS Sale_Price
FROM tb_Product;
```

**SELECT当计算器使用：**`SELECT (1+100)*100/2 AS outcome;`

### 判断

| **运算符** | **含义** |
| ------- |:------:|
| `<=`    | 小于等于   |
| `<`     | 小于     |
| `>=`    | 大于等于   |
| `>`     | 大于     |
| `<>`    | 不等于    |

> NULL不可以使用判断符，反之使用`IS NULL`和`IS NOT NULL`

**显示数据有空缺的行**

```sql
SELECT * FROM tb_Product
WHERE (purchase_price IS NOT NULL AND regist_date IS NOT NULL); 
```

**AND, OR**

> SQL的逻辑分**真、伪和不确定**三种，NULL会被认定为不确定

---

## 聚合和排序
