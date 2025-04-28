# T-SQL语言笔记
- [T-SQL语言笔记](#t-sql语言笔记)
- [数据类型](#数据类型)
  - [1. 精确数字](#1-精确数字)
  - [2. 近似数字](#2-近似数字)
  - [3. 字符串](#3-字符串)
  - [4. 二进制串](#4-二进制串)
  - [5. 日期与时间](#5-日期与时间)
- [常量](#常量)
  - [1. 字符串](#1-字符串)
  - [2. 日期](#2-日期)
  - [3. 货币](#3-货币)
- [变量](#变量)
  - [1. 定义变量](#1-定义变量)
    - [例子](#例子)
  - [2. 变量赋值](#2-变量赋值)
    - [例子](#例子-1)
  - [3. 变量输出](#3-变量输出)
    - [例子](#例子-2)
- [注释](#注释)
- [LEN(·) 函数](#len-函数)
    - [例子](#例子-3)
- [DATALENGTH(·) 函数](#datalength-函数)
    - [例子](#例子-4)
- [创建数据库](#创建数据库)
  - [语法](#语法)
  - [1. filespec 数据文件](#1-filespec-数据文件)
    - [文件后缀：](#文件后缀)
    - [格式](#格式)
    - [例子](#例子-5)
  - [2. filegroup 文件组](#2-filegroup-文件组)
    - [文件后缀：  `.ndf`](#文件后缀--ndf)
    - [格式](#格式-1)
    - [例子](#例子-6)
  - [3. 日志文件](#3-日志文件)
    - [文件后缀：`.ldf`](#文件后缀ldf)
    - [格式](#格式-2)
    - [例子](#例子-7)
  - [4. 完整例子](#4-完整例子)
- [修改数据库](#修改数据库)
  - [语法](#语法-1)
  - [1. add\_or\_modify\_files 添加或修改文件](#1-add_or_modify_files-添加或修改文件)
    - [格式](#格式-3)
    - [例子](#例子-8)
  - [2. add\_or\_modify\_filegroups 添加或修改文件组](#2-add_or_modify_filegroups-添加或修改文件组)
    - [格式](#格式-4)
    - [例子](#例子-9)
  - [完整例子](#完整例子)
- [删除数据库](#删除数据库)
  - [语法](#语法-2)
  - [完整例子](#完整例子-1)
- [分离数据库](#分离数据库)
  - [语法](#语法-3)
  - [分离时获得数据库独占权限](#分离时获得数据库独占权限)
  - [完整例子](#完整例子-2)
- [附加数据库](#附加数据库)
  - [语法](#语法-4)
  - [完整例子](#完整例子-3)
- [创建表](#创建表)
  - [语法](#语法-5)
  - [1. column\_definition 列定义](#1-column_definition-列定义)
    - [格式](#格式-5)
    - [例子](#例子-10)
  - [2. column\_constraint 列约束](#2-column_constraint-列约束)
    - [格式](#格式-6)
    - [例子](#例子-11)
  - [完整例子](#完整例子-4)
- [修改与删除表](#修改与删除表)
  - [语法](#语法-6)
  - [完整例子](#完整例子-5)
- [数据修改](#数据修改)
  - [语法](#语法-7)
  - [完整例子](#完整例子-6)
- [数据查询](#数据查询)
  - [语法](#语法-8)
  - [1. 数据统计](#1-数据统计)
    - [格式](#格式-7)
    - [例子](#例子-12)
  - [2. ORDER BY 排序](#2-order-by-排序)
    - [格式](#格式-8)
    - [例子](#例子-13)
  - [3. FROM ... WHERE 连接](#3-from--where-连接)
    - [格式](#格式-9)
    - [例子](#例子-14)
  - [4. JOIN … ON 连接](#4-join--on-连接)
    - [格式](#格式-10)
    - [说明](#说明)
    - [例子](#例子-15)
  - [5. GROUP BY 分组](#5-group-by-分组)
    - [语法](#语法-9)
    - [说明](#说明-1)
    - [例子](#例子-16)
  - [6. 子查询](#6-子查询)
    - [语法](#语法-10)
    - [相关子查询与无关子查询](#相关子查询与无关子查询)
    - [例子](#例子-17)
  - [7. 集合操作](#7-集合操作)
    - [语法](#语法-11)
    - [集合合并 UNION 与 UNION ALL](#集合合并-union-与-union-all)
    - [集合差 EXCEPT](#集合差-except)
    - [集合交 INTERSECT](#集合交-intersect)
  - [X. 杂项](#x-杂项)
    - [WHERE ... LIKE 模式匹配](#where--like-模式匹配)
      - [格式](#格式-11)
      - [例子](#例子-18)
    - [WHERE 判空](#where-判空)
      - [格式 \& 例子](#格式--例子)
  - [完整例子](#完整例子-7)
- [创建索引](#创建索引)
  - [语法](#语法-12)
  - [语句参数详解与补充](#语句参数详解与补充)
    - [1. `UNIQUE`](#1-unique)
    - [2. `CLUSTERED` | `NONCLUSTERED`](#2-clustered--nonclustered)
    - [3. `ON <object> ( column [ASC|DESC] [,...n] )`](#3-on-object--column-ascdesc-n-)
    - [4. `INCLUDE ( column_name [ ,...n ] )`](#4-include--column_name--n--)
    - [5. `WHERE <filter_predicate>`](#5-where-filter_predicate)
    - [6. `WITH ( <relational_index_option> [ ,...n ] )`](#6-with--relational_index_option--n--)
    - [7. `ON { partition_scheme_name ( column_name ) | filegroup_name | default }`](#7-on--partition_scheme_name--column_name---filegroup_name--default-)
    - [8. `FILESTREAM_ON { filestream_filegroup_name | partition_scheme_name | "NULL" }`](#8-filestream_on--filestream_filegroup_name--partition_scheme_name--null-)
  - [完整例子](#完整例子-8)

# 数据类型
## 1. 精确数字  
   整数：BIGINT 8 bytes，INT 4 bytes，SMALLINT 2 bytes，TINYINT 1bytes ，BIT 1 byte  
   小数：DECIMAL = NUMERIC，MONEY 8 bytes，SMALLMONEY 4 bytes  
` DECIMAL(p, s) -- p:总位数 s:小数位数 `
## 2. 近似数字  
   REAL，FLOAT
## 3. 字符串  
   CHAR 1 byte，VARCHAR，TEXT  
   UNICODE：NCHAR 2 bytes，NVARCHAR，NTEXT  
   ```SQL
   CHAR(n) NCHAR(n) -- n:字符串长度
   VARCHAR(max) NVARCHAR(max) -- max:最长长度
   ```
## 4. 二进制串  
   BINARY，VARBINARY，IMAGE  
   `BINARY(n) -- n:字节长度`  
   `VARBINARY(max)  -- max:字节最长长度`
## 5. 日期与时间  
   DATETIME 精确到 $1/300$s 8bytes，SMALLDATETIME 精确到分钟 4bytes  

# 常量
## 1. 字符串  
   CHAR: `'abcd'`  
   UNICODE: `N'abcd'`  
   单引号转义： `''->'`  

## 2. 日期  
   `'2006-05-21'`  
   `'2006/05/21'`  
   `'2006.05.21'`   
   `'2006-05-21'`   
   `'May 21, 2006'`  
   `10:40:34`  
   `04:24 PM`  
   `'2006-05-21 08:07:02.520'`  

## 3. 货币
   `$1453.23`


# 变量
## 1. 定义变量  
   `DECLARE @变量名 类型`  

@: 局部变量  
@@: 全局变量  
### 例子  
```SQL
DECLARE @a INT  
DECLARE @b NCHAR(10)
```  

## 2. 变量赋值  
   `SET @变量名 = 值`  
### 例子  
```SQL
SET @a = 5
SET @b = 'abc'
```  
## 3. 变量输出  
   `PRINT @变量名`  
### 例子  
```SQL
PRINT @a
```
# 注释  
   单行注释 `-- xxxx`  
   多行注释 `/*  xxxx  */`

# LEN(·) 函数
   返回字符串的字符数  
### 例子  
 `LEN('abc123你好!') = 9`  
 `LEN('') = 0`

# DATALENGTH(·) 函数
   返回变量的字节数
### 例子
 ```SQL
 DECLARE @a INT
 DATALENGTH(@a) = 4
 ```
# 创建数据库

## 语法
```SQL
CREATE DATABASE 数据库名称
  [ ON
    [ < filespec > [ ,...n ] ] 
    [ , < filegroup > [ ,...n ] ] 
  ]
  [ LOG ON { < filespec > [ ,...n ] } ] --指定日志数据文件
  [ COLLATE collation_name ] --排序规则
  [ WITH < external_access_option > ] --外部访问选项
  [ FOR { ATTACH | ATTACH_REBUILD_LOG } ] --数据库附加, 在之后展开

```

## 1. filespec 数据文件  
一个数据库可以分布式的存储在多个文件中  
### 文件后缀：  
主数据文件 `.mdf`  
次数据文件 `.ndf`  
### 格式
```SQL
[ PRIMARY ] --可选的是否是主数据文件
( 
[ NAME = 逻辑文件名, ] 
FILENAME = '文件物理路径' --数据文件的物理文件路径
[ , SIZE = 大小 [ KB | MB | GB | TB ] ] --数据文件的大小
[ , MAXSIZE = { 最大大小 [ KB | MB | GB | TB ] | UNLIMITED } ] --数据文件的最大大小
[ , FILEGROWTH = 增长幅度 [ KB | MB | GB | TB| % ] ] --数据文件的增长
)
```  
### 例子  
```SQL
PRIMARY (
NAME = file1,
FILENAME = 'C:\\file1.mdf',
SIZE = 10MB,
MAXSIZE = UNLIMITED,
FILEGROWTH = 5%
) 
-- 可以有多个文件，逗号隔开
-- 但只能是次数据文件，不能加 PRIMARY
```

## 2. filegroup 文件组  
   通过将不同表或索引放入不同文件组，可以根据磁盘特性或数据访问频率优化性能  
### 文件后缀：  `.ndf`
### 格式
   ```SQL
   FILEGROUP 文件组名称 <filespec> [ ,...n ]
   ```
### 例子  
```SQL
FILEGROUP Group1 
(
NAME = file2,
FILENAME = 'D:\\file1.ndf',
SIZE = 15MB,
MAXSIZE = UNLIMITED,
FILEGROWTH = 5%
) 
--可以有多个文件，逗号隔开
```  

## 3. 日志文件  
   记录数据库的日志信息
### 文件后缀：`.ldf`  
### 格式
```SQL
[ LOG ON { < filespec > [ ,...n ] } ]
```  
### 例子  
```SQL
LOG ON
(
NAME = log1,
FILENAME = 'C:\\log1.ldf',
SIZE = 5MB,
MAXSIZE = 20MB,
FILEGROWTH = 2MB
)
```

## 4. 完整例子
```SQL
CREATE DATABASE MyDatabase
ON
PRIMARY (
NAME = file1,
FILENAME = 'C:\\file1.mdf',
SIZE = 10MB,
MAXSIZE = UNLIMITED,
FILEGROWTH = 5%
),
(
NAME = file2,
FILENAME = 'C:\\file2.ndf',
SIZE = 20MB,
MAXSIZE = 50MB,
FILEGROWTH = 10MB
), --有逗号

FILEGROUP Group1 
(
NAME = file3,
FILENAME = 'D:\\file3.ndf',
SIZE = 15MB,
MAXSIZE = UNLIMITED,
FILEGROWTH = 5%
) --无逗号

LOG ON
(
NAME = log1,
FILENAME = 'C:\\log1.ldf',
SIZE = 5MB,
MAXSIZE = 20MB,
FILEGROWTH = 2MB
)
; --语句分隔
```  

# 修改数据库  
## 语法  
```SQL
ALTER DATABASE 数据库名称 
{
    <add_or_modify_files>
  | <add_or_modify_filegroups>
};
```  
## 1. add_or_modify_files 添加或修改文件  
用于对数据库文件进行变更，包括添加、修改或移除文件（数据或日志）  
### 格式
```SQL
ADD FILE <filespec> [ ,...n ]  --添加数据文件
      [ TO FILEGROUP { filegroup_name } ] --可选的加入文件组
| ADD LOG FILE <filespec> [ ,...n ] --添加日志文件
| REMOVE FILE logical_file_name  --删除文件 
| MODIFY FILE <filespec> --修改文件
```
### 例子
```SQL
-- 添加文件
ADD FILE 
(
NAME = file666,
FILENAME = 'C:\\file666.ndf',
SIZE = 20MB,
MAXSIZE = 50MB,
FILEGROWTH = 10MB
) TO FILEGROUP Group2

-- 添加日志文件
ADD LOG FILE
(
NAME = log666,
FILENAME = 'C:\\log666.ldf',
SIZE = 20MB,
MAXSIZE = 50MB,
FILEGROWTH = 10MB
)

-- 删除文件
REMOVE FILE file666

--修改文件
MODIFY FILE
(
NAME = file666, --逻辑名称用来寻找要修改的数据文件
NEWNAME = file777， --新逻辑名称
-- 文件的新属性
SIZE = 30MB, --大小不能往小改
MAXSIZE = 100MB,
FILEGROWTH = 20MB
)
```  
## 2. add_or_modify_filegroups 添加或修改文件组  
### 格式
```SQL
ADD FILEGROUP filegroup_name  -- 添加文件组
      [ CONTAINS FILESTREAM ] -- 表示此组用于存储 FILESTREAM 类型数据
| REMOVE FILEGROUP filegroup_name -- 删除文件组
| MODIFY FILEGROUP filegroup_name -- 修改文件组
    { 
      { READONLY | READWRITE } -- 设置组的读写权限
      | DEFAULT -- 将组设为默认组
      | NAME = new_filegroup_name -- 重命名文件组 
    }
```
### 例子
```SQL
ADD FILEGROUP Group3
MODIFY FILEGROUP Group3 READONLY
MODIFY FILEGROUP Group3 NAME = Group666
```  

## 完整例子
```SQL
-- 1
ALTER DATABASE MyDatabase
ADD FILE 
(
NAME = file666,
FILENAME = 'C:\\file666.ndf',
SIZE = 20MB,
MAXSIZE = 50MB,
FILEGROWTH = 10MB
);

-- 2
ALTER DATABASE MyDatabase
MODIFY FILEGROUP Group3 READONLY;
```

# 删除数据库

## 语法
```SQL
DROP DATABASE { 数据库名称 | 数据库快照名称 } [,...n ] 
```

## 完整例子

```SQL
DROP DATABASE MyDatabase;
```
# 分离数据库

## 语法
```SQL
EXEC sp_detach_db 数据库名称
```

## 分离时获得数据库独占权限

```SQL
USE master
ALTER DATABASE 数据库名称
SET SINGLE_USER
```

## 完整例子
```SQL
USE master
ALTER DATABASE MyDB
SET SINGLE_USER;

EXEC sp_detach_db MyDatabase;
```

# 附加数据库

## 语法
```SQL
CREATE DATABASE 数据库名称
ON
(
FILENAME = '主数据文件物理路径'
)
FOR ATTACH
```

## 完整例子
```SQL
CREATE DATABASE MyDatabase1
ON
(
   FILENAME = 'C:\\MyDatabase1.mdf'
)
FOR ATTACH;
```

# 创建表

## 语法
```SQL
-- 创建表，给出表名
CREATE TABLE [数据库名.[模式名]. | 模式名.] 表名 
( 
  { <column_definition> [ ,...n ] --列定义
   | <computed_column_definition>  --计算列定义
   | <column_set_definition>  --列集定义
  }
  [ <table_constraint> ] [ ,...n ] --表约束 可选
) 
[ ON  --数据存储位置 可选
  { partition_scheme_name ( partition_column_name ) 
  | filegroup 
  | "default" 
  } 
] 
[ TEXTIMAGE_ON { filegroup | "default" } ]  --TEXT，IMAGE存储位置 可选
[ FILESTREAM_ON { -- FILESTREAM存储位置 可选
  partition_scheme_name 
  | filegroup 
  | "default" 
  } 
]
[ WITH ( <table_option> [ ,...n ] ) ] --表选项 可选
;
```

## 1. column_definition 列定义
用于定义每一列的具体属性，可以重复多次以定义不同的列
### 格式
```SQL
列名 列数据类型
[ FILESTREAM ] --表示存储在文件系统（大文件用）
[ COLLATE collation_name ]  --指定字符列的排序规则
[ NULL | NOT NULL ] --指定该列是否允许为空值
[  -- 默认值或表示列，二选一
  [ CONSTRAINT constraint_name ]  --指定列的约束
  DEFAULT 常量表达式 /*指定列的默认值*/ 
  | [ IDENTITY [ ( begin, increment ) ] -- 定义自增列 seed：起始值  increment：自增值
  [ NOT FOR REPLICATION ] --表示在复制过程中不自动生成新值
]
[ ROWGUIDCOL ] -- 标记此列为表的行 GUID 列.  必须配合默认值使用
[ <column_constraint> [ ...n ] ] -- 指定列级约束, 解释见后
[ SPARSE ] -- 用于节省大量 NULL 值的列的存储空间
```
### 例子
```SQL
-- 多个列定义，逗号隔开
CustomerID INT IDENTITY(1,1) NOT NULL PRIMARY KEY,
Name NVARCHAR(100) COLLATE Latin1_General_CI_AS NOT NULL,
Email VARCHAR(100) NULL UNIQUE,
RegisteredDate DATETIME DEFAULT GETDATE(),
Price DECIMAL(10, 2) NOT NULL CHECK (Price >= 0),
ProfilePicture VARBINARY(MAX) FILESTREAM NULL
```

## 2. column_constraint 列约束

### 格式
```SQL
CONSTRAINT [ 约束名 ]  --约束名为此约束的逻辑名称，不指定系统将自动分配
{
  { PRIMARY KEY | UNIQUE }  -- 指定主键(不能为NULL) 或 值唯一(可为NULL)
  [ CLUSTERED | NONCLUSTERED ] -- 指定约束背后的索引类型（聚集索引或非聚集索引）
  ( 列名 ) --在column_definition中对某一列使用，不需要指定列名
  [ WITH (FILLFACTOR = 填充比例)  --控制索引页填充比例，范围为 10%~100%
      | WITH ( < index_option > [, ...n] ) ] --提供更复杂的索引选项配置，如 PAD_INDEX, IGNORE_DUP_KEY, STATISTICS_NORECOMPUTE 等
  [ ON { partition_scheme_name (partition_column_name) | filegroup |  "default" } ] --指定索引（即约束背后的索引）应创建在哪个分区方案或文件组中

| FOREIGN KEY -- 定义当前列引用另一个表的主键或唯一键（建立参照完整性）
  ( 列名 ) --在column_definition中对某一列使用，不需要指定列名
    REFERENCES [ schema_name. ]referenced_table_name [(ref_column)] -- 指定目标表和被引用列
    [ ON DELETE { NO ACTION | CASCADE /*同步删除/更新子表行 */ | SET NULL | SET DEFAULT }  ] -- 指定主表数据变更时，从表的同步行为
    [ ON UPDATE { NO ACTION | CASCADE /*同步删除/更新子表行 */ | SET NULL | SET DEFAULT }  ] -- 指定主表数据变更时，从表的同步行为
    [ NOT FOR REPLICATION ] -- 表示复制过程中不触发这些规则

| CHECK [ NOT FOR REPLICATION ] ( logical_expression ) -- 定义逻辑表达式约束，强制某列（或多列）满足给定条件
}
```

### 例子
```SQL
--定义Student为主键
CONSTRAINT Cons1 PRIMARY KEY (Student) 

--定义复合主键
CONSTRAINT Cons2 PRIMARY KEY (Student, ID) 

-- 复杂例子
CONSTRAINT Cons3 UNIQUE CLUSTERED (Name) 
WITH (FILLFACTOR = 20) 
ON [PRIMARY]

--当前表中的 ID 列只能取 Customers 表中 ID 列已存在的值
CONSTRAINT Cons4 FOREIGN KEY (ID) 
REFERENCES Customers(ID)

-- 限制值范围
CONSTRAINT Cons5 CHECK (Price >= 0 AND Price <= 10000)
```

## 完整例子
```SQL
USE MyDatabase1; -- 先选择一个数据库

CREATE TABLE MyClass
(
ID INT NOT NULL,
Name NCHAR(20) NOT NULL,
Age INT DEFAULT 18 CHECK (Age >= 0 AND Age <= 120),
Gender NCHAR(2) NULL,

CONSTRAINT ConsPriKey PRIMARY KEY (ID, Name),
CONSTRAINT ConsID FOREIGN KEY (ID) REFERENCES Students(ID) ON DELETE CASCADE
)
ON [PRIMARY] -- 表数据存储位置
;
```

# 修改与删除表

## 语法
```SQL
-- 修改表
ALTER TABLE [数据库名.[架构名].|架构名.]表名 
{ 
  ALTER COLUMN 列名 
  { 
    [ 新类型架构名. ] 新类型名
    [ COLLATE collation_name ] -- 用于指定字符串列的排序规则
    [ NULL | NOT NULL ] -- 更改该列是否允许为 NULL
    [ SPARSE ] -- 指定列是否为稀疏列
    | { ADD | DROP } -- 用于添加或移除列上的特殊属性
      { ROWGUIDCOL | PERSISTED | NOT FOR REPLICATION | SPARSE }
  } 
| [ WITH { CHECK | NOCHECK } ] -- 用于控制在添加外键或 CHECK 约束时是否立即验证现有数据
| ADD -- 用于向表中添加列或表约束 与创建表时的列定义相同
  { 
      <column_definition> -- 列定义
    | <computed_column_definition>
    | <table_constraint> 
    | <column_set_definition> 
  } [ ,...n ]
| DROP -- 用于删除表中现有的列或约束
  { 
    [ CONSTRAINT ] 约束名 -- 删除约束
    [ WITH ( <drop_clustered_constraint_option> [ ,...n ] ) ]
    | COLUMN 列名
  } [ ,...n ] 
};

-- 删除表
DROP TABLE [ 数据库名 . [ 架构名 ] . | 架构名 . ]
      表名 [ ,...n ]
;
```

## 完整例子
```SQL
-- 修改Name列为 50长度的NCHAR
ALTER TABLE MyClass
ALTER COLUMN Name NCHAR(50);

-- 修改Age列为 总长10，小数精度2的DECIMAL
ALTER TABLE MyClass
ALTER COLUMN Age DECIMAL(10,2);

-- 为Age增加SPARSE属性
ALTER TABLE MyClass
ALTER COLUMN Age ADD SPARSE;

-- 增加列Score，总长10，小数精度2的DECIMAL
ALTER TABLE MyClass
ADD Score DECIMAL(10,2) NOT NULL;

-- 增加列约束
ALTER TABLE MyClass
ADD CONSTRAINT ConsScoreCheck CHECK (Score >= 0 AND Score <= 150);

-- 添加默认值约束
ALTER TABLE MyClass
ADD CONSTRAINT ConsCourse DEFAULT 4 FOR Score;

-- StuID 列增加 UNIQUE属性
ALTER TABLE MyClass
ADD CONSTRAINT Uni1 UNIQUE (StuID);

-- MyClass表的CourseID 列增加 外键约束
-- MyClass.CourseID 的值必须是 Course.CouseID 的已有值
ALTER TABLE MyClass
ADD CONSTRAINT Fori FOREIGN KEY (CourseID) REFERENCES Course(CouseID);

-- 删除列
ALTER TABLE MyClass
DROP COLUMN Score;

-- 删除表
DROP TABLE MyDatabase1.dbo.MyClass;
```

# 数据修改

## 语法
```SQL
-- 插入行,可以一次性插入多行
INSERT [INTO] table_name [(column1, column2, ...)] 
VALUES (value1, value2, ...), (value1, value2, ...), ...n;

-- 删除行
DELETE FROM table_name
[WHERE <search_condition>];


-- 修改数据
UPDATE table_name
SET column1 = {expression | DEFAULT | NULL}, column2 = ...
[WHERE <search_condition>];
```

## 完整例子
```SQL
-- 一次插入三条学生记录
INSERT INTO students (id, name, age, grade)
VALUES 
  (101, '张三', 18, 'A'),
  (102, '李四', 19, 'B'),
  (103, '王五', 17, 'A');

-- 将所有成绩为A的学生插入到high_achievers表
INSERT INTO high_achievers (student_id, name)
SELECT id, name FROM students WHERE grade = 'A';

-- 删除2023年1月1日之前且已取消的订单
DELETE FROM orders
WHERE order_date < '2023-01-01' AND status = '已取消';

-- 删除所有属于北京部门的员工
DELETE FROM employees
WHERE department_id IN (
    SELECT id FROM departments WHERE location = '北京'
);

-- 将所有电子产品价格设为120，增加库存100
UPDATE products
SET price = 120, stock = stock + 100
WHERE category = '电子产品';

-- 根据分数批量更新学生的等级
UPDATE students
SET grade = 
    CASE 
        WHEN score >= 90 THEN 'A'
        WHEN score >= 80 THEN 'B'
        WHEN score >= 70 THEN 'C'
        ELSE 'D'
    END;
```


# 数据查询

## 语法
一些细节部分未完整列出，见下详细解释
```SQL
SELECT 
[
  [TOP n [PERCENT]]  -- 列出前n行或前n%
  | [DISTINCT] -- 消除重复行
] 
select_list[=
CASE [列名]
  WHEN 表达式 THEN 表达式 [...n] 
  [ELSE 表达式] --所有WHEN都不成立的情况 
END
]
[{= | AS | 空格} 别名] --结果显示的列的名称
[,...n] -- 查询的列, CASE 可以进行逻辑判断并映射

[ INTO 新表名 ] -- 的结果存储到一个新的表中
[ FROM table_source ] -- 单表、多个表（通过连接），或者子查询
[ WHERE search_condition ] --查询的条件
[ GROUP BY group_by_expression] -- 将结果按某些字段进行分组
[ HAVING search_condition] -- 对分组的结果进行过滤，与 WHERE 不同，HAVING 是针对聚合结果的条件筛选
[ ORDER BY order_expression [ ASC | DESC ] ] -- 结果的排序方式  ASC:默认，升序   DESC:降序
```

## 1. 数据统计

### 格式
```SQL
SUM(col) -- 列求和
AVG(col) -- 列平均
MIN(col) -- 列最小
MAX(col) -- 列最大
COUNT(*) -- 行个数
COUNT(col) -- 列中取值不为空的项个数，不考虑是否重复
```

### 例子
```SQL
SELECT SUM(Score) AS '总分',AVG(Score) AS '平均分',MAX(Score) AS '最高分',
MIN(Score) AS '最低分'

SELECT COUNT(*) AS '作者人数', COUNT(Provinces) AS '登记有所在省份的作者人数'
```

## 2. ORDER BY 排序

### 格式
```SQL
ORDER BY column1 [ASC | DESC], column2 [ASC | DESC], ...
```
+ 可以使用 SELECT 子句中定义的别名作为 column
+ 可以指定多个列进行排序，次序优先级从左到右

### 例子
```SQL
-- 按 salary 降序
ORDER BY salary DESC

-- 先按 salary 降序排列，若工资相同则再按 name 升序排列
ORDER BY salary DESC, name ASC

--别名排序
SELECT salary * 1.1 AS adjusted_salary
FROM employees
ORDER BY adjusted_salary DESC; 
```

## 3. FROM ... WHERE 连接

隐式连接（Implicit Join）的写法。等价于将表与表进行笛卡尔积（Cartesian Product），并在 WHERE 子句中加以限制，从而只保留满足条件的记录

### 格式
```SQL
FROM table_name [,table_name, … ]
WHERE condition
```
### 例子
```SQL
-- 找出每个学生所就读的学校名
SELECT Name, SchoolName
FROM Student, School
WHERE Student.SchoolID = School.SchoolID

-- “计算机学院”学生所修课程的成绩及对应课程名称
SELECT Name, SchoolName, Course.CourseName, Mark.Score
FROM Student,School,Mark,Course
WHERE Student.StudentID = Mark.StudentID
AND Course.CourseID = Mark.CourseID
AND School.SchoolName = '计算机学院'
```
## 4. JOIN … ON 连接

### 格式
```SQL
FROM table_name 
{ 
[ INNER | { LEFT | RIGHT | FULL } ] [ CROSS ] 
JOIN table_name 
ON condition --连接条件
} [...,n]
WHERE condition --选择条件
```

### 说明
+ INNER表示内连接，是系统默认的连接方式。
+ 外连接分为左外连接（LEFT）、右外连接（RIGHT）、完全外连接（FULL）。
  - 左外连接的结果集中除了包括满足条件的行外，还包括左表所有的行。
  - 右外连接的结果集中除了包括满足条件的行外，还包括右表所有的行。
  - 完全外连接的结果集中除了包括满足条件的行外，还包括左右两表所有的行。
  - 不匹配则补 NULL
+ CROSS表示交叉连接，即生成一个笛卡尔积，即每个左表行与右表所有行组合。
+ ON 与 WHERE 的区别：ON在连接时进行判断，WHERE在连接后的临时表中进行判断筛选

### 例子
```SQL
-- 内连接，查询返回每位已选课学生的姓名、课程名称及对应成绩
SELECT Student.Name, Course.CourseName, Mark.Score
FROM Student
JOIN Mark ON Student.StudentID = Mark.StudentID
JOIN Course ON Course.CourseID = Mark.CourseID;


-- 右外连接，查询返回所有学生的姓名及其所选课程的编号，即使某没有选课，其课程编号也会显示为 NULL
SELECT Name,Mark.CourseID
FROM Mark 
RIGHT JOIN Student
ON Mark.StudentID = Student.StudentID;
```

## 5. GROUP BY 分组

对查询结果按照某些字段进行分组，以便结合 聚合函数（如 SUM()、COUNT()、AVG() 等）进行统计分析

### 语法
```SQL
GROUP BY column_name -- 对查询结果按照某一列或多列进行分组
[ HAVING condition ] -- 对分组后的结果进一步过滤（区别于 WHERE，HAVING 是作用在聚合之后的分组结果上）
| [ WITH CUBE | ROLLUP ] -- 对分组结果进一步进行多维统计或汇总
```
### 说明
+ WITH CUBE 和 ROLLUP
  + ROLLUP：生成层次汇总，可以逐层汇总每一个分组的结果，最终得到总汇
  + CUBE：生成所有可能的分组组合的汇总，提供更全面的多维分析
+ GROUP BY后的column_name必须出现在SELECT后的select_list中，或者出现在聚合函数中，否则不允许分组
+ 如果 GROUP BY 后跟多个列，如：GROUP BY A, B，那么是先按 A 分组，在 A 相同的组内再按 B 分组。
+ GROUP BY 无聚合函数时等同于 DISTINCT

### 例子
```SQL
-- 返回人数超过10人的部门
SELECT dept_id, COUNT(*) 
FROM employees 
GROUP BY dept_id 
HAVING COUNT(*) > 10;

-- 对CourseID进行分组，并按分组后的 组 平均成绩进行降序
SELECT CourseID,SUM(Score) AS '总分',AVG(Score) AS '平均分'
FROM Mark
GROUP BY Mark.CourseID
ORDER BY AVG(Score) DESC
```
```SQL
-- 查询统计了每个课程的学生人数，并通过 WITH CUBE 生成了所有课程的总学生人数汇总
SELECT CourseName, COUNT(*) AS '人数'
FROM Course, Mark
WHERE Course.CourseID = Mark.CourseID
GROUP BY CourseName
WITH CUBE
```
可能的结果：
| CourseName | 人数 | WITH CUBE 解释 |
| ---------- | ---- | -------------- |
| 数学       | 2    |
| 物理       | 2    |
| 化学       | 3    |
| NULL       | 7    | 生成的总人数   |
```SQL
-- 统计每所学校中不同性别的学生人数，并通过 WITH ROLLUP 生成汇总结果
SELECT SchoolName, Sex, COUNT(*) AS '人数'
FROM Student, School
WHERE Student.SchoolID = School.SchoolID
GROUP BY SchoolName, Sex
WITH ROLLUP
```
可能的结果：
| SchoolName | Sex  | 人数 | WITH ROLLUP 解释 |
| ---------- | ---- | ---- | ---------------- |
| 学校A      | 男   | 1    |
| 学校A      | 女   | 1    |
| 学校A      | NULL | 2    | 每所学校的总人数 |
| 学校B      | 男   | 2    |
| 学校B      | 女   | 1    |
| 学校B      | NULL | 3    | 每所学校的总人数 |
| NULL       | NULL | 5    | 所有学校的总人数 |



## 6. 子查询
子查询（Subquery）是嵌套在其他查询语句（如 SELECT、FROM、WHERE、HAVING 或 JOIN 子句中）的查询。子查询的作用是为外部查询提供中间结果

### 语法

在 SELECT 列表中的标量子查询：
```SQL
SELECT 
    column1,
    (SELECT expression FROM table WHERE conditions) AS alias
FROM table;
```

在 FROM 中作为派生表：
```SQL
SELECT columns
FROM (
    SELECT columns FROM table WHERE conditions
) AS alias;
```

在 WHERE 或 HAVING 子句中使用：
```SQL
-- 比较符号，标量子查询
SELECT columns
FROM table
WHERE column [= | >|< | > = |<= |<>] (SELECT expression FROM table WHERE conditions);

-- IN / NOT IN，多值子查询
SELECT columns
FROM table
WHERE column [NOT] IN (SELECT column FROM table WHERE conditions);

-- EXISTS / NOT EXISTS
SELECT columns
FROM table t1
WHERE [NOT] EXISTS (
    SELECT 1 FROM table t2 WHERE t2.foreign_key = t1.primary_key
); -- SELECT 1： 它不表示从表中选取某个字段，而是返回一个固定值 1. 表示只关心有没有数据，不关心具体数据
```
### 相关子查询与无关子查询
无关子查询是可以独立于外层查询单独执行的子查询。它不会引用外层查询的任何列。  
  特点：
  + 先执行子查询，结果作为外层查询的输入；

  + 可作为常量使用（如果返回单一值）或集合（用于 IN、EXISTS 等）；

  + 可嵌套在 SELECT、WHERE、FROM 等多个位置；

  + 执行计划中只运行一次。  

例子
```SQL
SELECT DeptAvg.DepartmentID, DeptAvg.AvgSalary
FROM (
    SELECT DepartmentID, AVG(Salary) AS AvgSalary
    FROM Employees
    GROUP BY DepartmentID
) AS DeptAvg
WHERE DeptAvg.AvgSalary > 8000;
```
相关子查询是依赖于外层查询的值，不能独立运行的子查询。通常子查询中会引用外层查询的列。  
  特点：
  + 每处理外层查询的一行，子查询都会被重新执行一次；

  + 执行成本较高，尤其在数据量大时；

  + 常见于 WHERE、SELECT 或 HAVING 中的判断逻辑；

  + 适用于每一行需要对其上下文进行判断的场景。  

例子
```SQL
SELECT Name, Salary
FROM Employees E
WHERE Salary > (
    SELECT AVG(Salary)
    FROM Employees
    WHERE DepartmentID = E.DepartmentID
);
```
### 例子
```SQL
-- 找出选修了《计算机网络》课程的学生的姓名
-- 利用上一层返回的学号集合，从 Student 表中找出这些学生的姓名 Name
SELECT Name
FROM Student
WHERE StudentID IN
( -- 使用最内层查询结果，筛选出在 Mark 表中选修了这些课程（即“计算机网络”）的学生编号 StudentID
  SELECT StudentID
  FROM Mark
  WHERE CourseID IN
  ( --查询课程表 Course 中，课程名称为“计算机网络”的课程编号 CourseID
    SELECT CourseID
    FROM Course
    WHERE CourseName='计算机网络'
  )
);

-- 查询不属于“物理学院”的学生中，出生日期早于所有“物理学院”学生的学生姓名及其学院名
SELECT Name, SchoolName
FROM Student, School
WHERE Student.SchoolID = School.SchoolID
  AND SchoolName <> '物理学院'
  AND Birthday < ALL -- ALL 的语义：表达式要对集合中“所有元素”都成立, SOME（或ANY）表示结果集中的任一数据，如果有一个满足关系表达式就输出
   (
    -- 得到物理学院所有学生的出生日期列表
    SELECT Birthday
    FROM Student, School
    WHERE Student.SchoolID = School.SchoolID
      AND SchoolName = '物理学院'
);
```

## 7. 集合操作

集合操作用于对多个 SELECT 语句的结果进行合并、取交集或差集处理。

### 语法
```SQL
-- UNION 与 UNION ALL
<查询1>
UNION [ALL]
<查询2>
[UNION [ALL] <查询3> ...]

-- EXCEPT
<查询1>
EXCEPT
<查询2>

-- INTERSECT
<查询1>
INTERSECT
<查询2>
```

### 集合合并 UNION 与 UNION ALL

将多个查询结果合并成一个结果集。

基本规则：
+ 所有参与合并的查询结果集 列数必须相同。
+ 对应列的 数据类型必须兼容（例如不能将字符串和数值型直接合并）。
+ 合并时默认去除重复行，除非使用 UNION ALL 明确要求保留所有行（包括重复行）。

例子
```SQL
-- 将员工与客户的姓名合并为一个结果集，默认去重
SELECT name FROM employees
UNION
SELECT name FROM customers;
```

### 集合差 EXCEPT
返回左侧查询中存在但右侧查询中不存在的行（去重后）
基本规则：
+ 列数与数据类型必须匹配。
+ 结果集自动去重。

例子
```SQL
-- 查询只在员工中出现、但不在客户中的姓名
SELECT name FROM employees
EXCEPT
SELECT name FROM customers;
```

### 集合交 INTERSECT
返回左右两个查询结果中都存在的行（去重后）
基本规则：
+ 列数与数据类型必须匹配。
+ 结果集自动去重。

例子
```SQL
-- 查询同时出现在员工和客户中的姓名
SELECT name FROM employees
INTERSECT
SELECT name FROM customers;
```

## X. 杂项

### WHERE ... LIKE 模式匹配

#### 格式
```SQL
WHERE col LIKE expression
```
| 通配符 | 说明                       |
| ------ | -------------------------- |
| %      | 匹配0个或多个任意字符      |
| _      | 匹配1个任意字符            |
| [ ]    | 匹配集合中的任意单个字符   |
| [^ ]   | 不匹配集合中的任意单个字符 |

#### 例子
```SQL
-- 以赵开始
WHERE Name LIKE '赵%'

-- 不以张开始
WHERE Name LIKE '[^张]%'

-- 中间两字符任意
WHERE Author LIKE 'K__n'
```

### WHERE 判空

#### 格式 & 例子
```SQL
WHERE col IS NULL

WHERE Name IS NULL
```


## 完整例子
```SQL
-- 查询表中的所有数据
SELECT * FROM employees;

-- 列出name 和 salary列，salary的值+10，且年龄>30
SELECT name, salary + 10
FROM employees
WHERE age > 30;

-- 复杂例子
SELECT d.name AS department_name, COUNT(*) = emp_count, AVG(e.salary) avg_salary
INTO dept_summary
FROM employees e
JOIN departments d ON e.department_id = d.id
WHERE e.age >= 25
GROUP BY d.name
HAVING AVG(e.salary) > 8000
ORDER BY emp_count DESC;

-- 映射Score到RANK
SELECT StudentID,CourseID,Score,RANK=
CASE
  WHEN Score>=80 THEN '优秀'
  WHEN Score>=60 THEN '及格'
  ELSE '不及格'
END
FROM Mark;

-- 映射Sex
SELECT Name,性别=
CASE Sex
  WHEN '男' THEN '男生'
  WHEN '女' THEN '女生'
END
FROM Student;

-- 将所有性别的值列出去重
SELECT DISTINCT Sex AS '性别'
FROM Author;
```

#  创建索引
## 语法
```SQL
CREATE 
[ UNIQUE ] 
[ CLUSTERED | NONCLUSTERED ] 
INDEX index_name 
    ON <object> ( column [ ASC | DESC ] [ ,...n ] ) 
    [ INCLUDE ( column_name [ ,...n ] ) ]
    [ WHERE <filter_predicate> ]
    [ WITH ( <relational_index_option> [ ,...n ] ) ]
    [ ON { partition_scheme_name ( column_name ) 
         | filegroup_name 
         | default 
         }
    ]
    [ FILESTREAM_ON { filestream_filegroup_name | partition_scheme_name | "NULL" } ]
```
## 语句参数详解与补充

### 1. `UNIQUE`
- 含义：指定索引中的每个键值必须唯一，防止重复数据。
- 补充说明：唯一索引常用于实现唯一性约束，例如邮箱、身份证号等场景。主键约束本质上会自动创建唯一聚集索引（如果表还没有聚集索引）。

### 2. `CLUSTERED` | `NONCLUSTERED`
- 含义：指定索引类型。
    - `CLUSTERED`（聚集索引）：表中数据的物理顺序与索引一致。每张表最多有一个聚集索引。
    - `NONCLUSTERED`（非聚集索引）：索引结构与数据分开，逻辑顺序与物理存储无关。表可以有多个非聚集索引。
- 补充说明：聚集索引通常用于主键或经常排序、范围查询的列。非聚集索引适合频繁查找的数据列。

### 3. `ON <object> ( column [ASC|DESC] [,...n] )`
- 含义：指定在哪个表（或视图）的哪些列上创建索引，可以指定排序方式（升序ASC或降序DESC）。
- 补充说明：一个索引最多可以包含16列，且键长度有最大字节数限制（如900字节）。

### 4. `INCLUDE ( column_name [ ,...n ] )`
- 含义：为非聚集索引指定**包含列**，这些列不会参与索引排序，但会作为索引页的附加信息存储。
- 补充说明：包含列可显著提升只查询部分非键列的性能，避免回表操作。只能用于非聚集索引。

### 5. `WHERE <filter_predicate>`
- 含义：用于创建**筛选索引**（Filtered Index），只对满足条件的行建立索引。
- 补充说明：适合稀疏数据，提高空间利用率和查询效率。例如只为有效状态的数据建立索引。

### 6. `WITH ( <relational_index_option> [ ,...n ] )`
- 含义：为索引创建过程或属性设置额外选项。
- 常用选项如：
    - `FILLFACTOR = n`：指定叶级页的填充程度（1-100），有助于减少页分裂。
    - `PAD_INDEX = ON|OFF`：是否为非叶级页设置相同填充因子。
    - `IGNORE_DUP_KEY = ON|OFF`：插入重复键时是否报错。
    - `STATISTICS_NORECOMPUTE = ON|OFF`：是否自动重建统计信息。
    - `DROP_EXISTING = ON|OFF`：是否替换已有同名索引。
    - `ONLINE = ON|OFF`：是否在线创建/重建索引（对业务影响小）。
    - `DATA_COMPRESSION = { NONE | ROW | PAGE }`：数据压缩类型。
- 补充说明：可以同时指定多个选项，使用逗号分隔。

### 7. `ON { partition_scheme_name ( column_name ) | filegroup_name | default }`
- 含义：指定索引的物理存储位置，可以是分区方案、文件组或默认。
- 补充说明：分区索引适合大表的分区管理，有助于性能和维护。

### 8. `FILESTREAM_ON { filestream_filegroup_name | partition_scheme_name | "NULL" }`
- 含义：用于包含FILESTREAM数据的表，指定FILESTREAM数据的存储位置。
- 补充说明：只适用于包含大对象（如文件、图片）的表。

## 完整例子
```SQL
-- 为Employees表的LastName列创建一个非聚集索引，加速基于姓氏的查询
CREATE NONCLUSTERED INDEX idx_employees_lastname
ON Employees (LastName);

-- 为Users表的UserID列创建唯一聚集索引，确保每个用户ID唯一
CREATE UNIQUE CLUSTERED INDEX idx_users_userid
ON Users (UserID);

-- 为Orders表的OrderDate列创建非聚集索引，并将CustomerID和TotalAmount作为包含列
CREATE NONCLUSTERED INDEX idx_orders_orderdate
ON Orders (OrderDate)
INCLUDE (CustomerID, TotalAmount);

-- 只为Status为'Active'的订单创建索引
CREATE NONCLUSTERED INDEX idx_orders_active
ON Orders (OrderDate)
WHERE Status = 'Active';

-- 为Products表的CategoryID和Price列创建唯一非聚集索引，包含ProductName
-- 设置填充因子、在线创建，并指定索引存储在UserIndexes文件组
CREATE UNIQUE NONCLUSTERED INDEX idx_products_category_price
ON Products (CategoryID ASC, Price DESC)
INCLUDE (ProductName)
WITH (
    FILLFACTOR = 80,
    ONLINE = ON,
    DATA_COMPRESSION = PAGE
)
ON [UserIndexes];
```