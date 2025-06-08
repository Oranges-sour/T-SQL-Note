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
  - [完整例子](#完整例子-8)
- [修改索引](#修改索引)
  - [语法](#语法-13)
  - [完整例子](#完整例子-9)
- [优化索引](#优化索引)
  - [索引性能分析](#索引性能分析)
    - [1. SHOWPLAN 命令](#1-showplan-命令)
    - [2. STATISTICS IO 命令](#2-statistics-io-命令)
- [创建视图](#创建视图)
  - [语法](#语法-14)
  - [例子](#例子-19)
- [查询视图](#查询视图)
  - [例子](#例子-20)
- [更新视图](#更新视图)
  - [例子](#例子-21)
- [修改视图](#修改视图)
  - [语法](#语法-15)
  - [例子](#例子-22)
- [删除视图](#删除视图)
  - [语法](#语法-16)
  - [例子](#例子-23)
- [用户定义函数](#用户定义函数)
  - [标量值函数](#标量值函数)
    - [语法](#语法-17)
    - [例子](#例子-24)
  - [内嵌表值函数](#内嵌表值函数)
    - [语法](#语法-18)
    - [例子](#例子-25)
  - [多语句表值函数](#多语句表值函数)
    - [语法](#语法-19)
    - [例子](#例子-26)
- [创建存储过程](#创建存储过程)
  - [语法](#语法-20)
    - [创建存储过程的基本步骤](#创建存储过程的基本步骤)
    - [`CREATE PROCEDURE`语句的语法](#create-procedure语句的语法)
      - [语法说明：](#语法说明)
    - [存储过程的常见使用场景](#存储过程的常见使用场景)
    - [创建存储过程的注意事项](#创建存储过程的注意事项)
  - [例子](#例子-27)
- [调用存储过程](#调用存储过程)
- [创建触发器](#创建触发器)
  - [语法](#语法-21)
    - [关键部分解释：](#关键部分解释)
  - [触发器类型](#触发器类型)
  - [例子](#例子-28)
- [禁止或删除触发器](#禁止或删除触发器)
  - [语法](#语法-22)
- [创建游标](#创建游标)
  - [语法](#语法-23)
    - [**解析：**](#解析)
      - [游标的使用场景：](#游标的使用场景)
  - [例子](#例子-29)
- [使用游标](#使用游标)
  - [打开游标](#打开游标)
  - [读取游标](#读取游标)
  - [关闭游标](#关闭游标)
  - [删除游标](#删除游标)
- [用户权限管理](#用户权限管理)
  - [创建用户](#创建用户)
  - [分配用户权限](#分配用户权限)
    - [语法](#语法-24)
      - [主要组成部分：](#主要组成部分)
    - [例子](#例子-30)
  - [收回用户权限](#收回用户权限)
    - [语法](#语法-25)
    - [一、REVOKE 语句语法解析](#一revoke-语句语法解析)
      - [参数说明：](#参数说明)
    - [例子](#例子-31)
  - [DENY 语句](#deny-语句)
    - [语法](#语法-26)
    - [例子](#例子-32)
- [事物的概念](#事物的概念)
  - [ACID原则](#acid原则)
  - [事务分类](#事务分类)
    - [1. **系统事务**：](#1-系统事务)
    - [2. **用户定义的事务**：](#2-用户定义的事务)
- [用户定义事物](#用户定义事物)
  - [`BEGIN TRANSACTION` 启动事务](#begin-transaction-启动事务)
    - [语法](#语法-27)
    - [分析：](#分析)
    - [示例：](#示例)
  - [`COMMIT TRANSACTION` 提交事务](#commit-transaction-提交事务)
    - [语法](#语法-28)
    - [分析](#分析-1)
    - [例子](#例子-33)
  - [`ROLLBACK TRANSACTION` 回滚事务](#rollback-transaction-回滚事务)
    - [语法](#语法-29)
    - [分析](#分析-2)
    - [例子](#例子-34)
  - [`SAVE TRANSACTION` 设置保存点](#save-transaction-设置保存点)
    - [语法](#语法-30)
    - [分析](#分析-3)
    - [例子](#例子-35)
  - [完整例子](#完整例子-10)
  - [事务控制流程图](#事务控制流程图)
- [事物隔离等级](#事物隔离等级)
    - [事务隔离级别的分类](#事务隔离级别的分类)
    - [例子](#例子-36)
    - [设置隔离级别为 `READ UNCOMMITTED`](#设置隔离级别为-read-uncommitted)
    - [补充内容](#补充内容)
- [锁](#锁)
  - [锁机制分类与意向锁详细说明](#锁机制分类与意向锁详细说明)
    - [锁的分类（按操作类型）](#锁的分类按操作类型)
    - [意向锁（Intent Locks）](#意向锁intent-locks)
      - [定义：表示事务“**有意**”对更低层次的资源加锁（如对页或行），从而在高层（如表）加锁时避免冲突。](#定义表示事务有意对更低层次的资源加锁如对页或行从而在高层如表加锁时避免冲突)
      - [类型与用途：](#类型与用途)
      - [示例：](#示例-1)
  - [三、锁兼容性分析](#三锁兼容性分析)
  - [死锁处理机制](#死锁处理机制)
    - [预防死锁方法](#预防死锁方法)
    - [解除死锁方法](#解除死锁方法)
  - [锁的使用要求](#锁的使用要求)

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
索引是在数据库表的一个或多个列上建立的数据结构，用于加快数据查询和检索速度
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

1. `UNIQUE`
- 含义：指定索引中的每个键值必须唯一，防止重复数据。
- 常用于实现唯一性约束，例如邮箱、身份证号等场景。主键约束会自动创建唯一聚集索引（如果表还没有聚集索引）。  

  
2. `CLUSTERED` | `NONCLUSTERED`
- 含义：指定索引类型。
    - `CLUSTERED`（聚集索引）：表中数据的物理顺序与索引一致。每张表最多有一个聚集索引。
    - `NONCLUSTERED`（非聚集索引）：索引结构与数据分开，逻辑顺序与物理存储无关。表可以有多个非聚集索引。
- 常用于主键或经常排序、范围查询的列。非聚集索引适合频繁查找的数据列。

3. `ON <object> ( column [ASC|DESC] [,...n] )`
- 含义：指定在哪个表（或视图）的哪些列上创建索引，可以指定排序方式（升序ASC或降序DESC）。
- 一个索引最多可以包含16列，且键长度有最大字节数限制（如900字节）。

4. `INCLUDE ( column_name [ ,...n ] )`
- 含义：为非聚集索引指定**包含列**，这些列不会参与索引排序，但会作为索引页的附加信息存储。
- 可显著提升只查询部分非键列的性能，只能用于非聚集索引。

5. `WHERE <filter_predicate>`
- 含义：用于创建**筛选索引**（Filtered Index），只对满足条件的行建立索引。
- 适合稀疏数据，提高空间利用率和查询效率。例如只为有效状态的数据建立索引。

6. `WITH ( <relational_index_option> [ ,...n ] )`
- 含义：为索引创建过程或属性设置额外选项。
- 常用选项如：
    - `FILLFACTOR = n`：指定叶级页的填充程度（1-100），有助于减少页分裂。
    - `PAD_INDEX = ON|OFF`：是否为非叶级页设置相同填充因子。
    - `IGNORE_DUP_KEY = ON|OFF`：插入重复键时是否报错。
    - `STATISTICS_NORECOMPUTE = ON|OFF`：是否自动重建统计信息。
    - `DROP_EXISTING = ON|OFF`：是否替换已有同名索引。
    - `ONLINE = ON|OFF`：是否在线创建/重建索引（对业务影响小）。
    - `DATA_COMPRESSION = { NONE | ROW | PAGE }`：数据压缩类型。
- 可以同时指定多个选项，使用逗号分隔。

7. `ON { partition_scheme_name ( column_name ) | filegroup_name | default }`
- 含义：指定索引的物理存储位置，可以是分区方案、文件组或默认。
- 分区索引适合大表的分区管理，有助于性能和维护。

8. `FILESTREAM_ON { filestream_filegroup_name | partition_scheme_name | "NULL" }`
- 含义：用于包含FILESTREAM数据的表，指定FILESTREAM数据的存储位置。
- 只适用于包含大对象（如文件、图片）的表。

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

# 修改索引

## 语法
```sql
ALTER INDEX { index_name | ALL }
    ON <object> -- 指的是索引所属的对象，通常是表名
    { REBUILD | DISABLE | REORGANIZE }
```
- REBUILD 是用来彻底重建索引，适用于碎片较严重的情况。
- DISABLE 用来禁用索引，适合临时不需要索引时使用。
- REORGANIZE 是对索引进行轻量的碎片整理，适用于碎片较少的情况。
## 完整例子
```sql
-- 重新构建名为 `idx_customer_name` 的索引
ALTER INDEX idx_customer_name 
ON customers 
REBUILD;

-- 重新组织名为 `idx_product_name` 的索引
ALTER INDEX idx_product_name 
ON products 
REORGANIZE;
```

# 优化索引
## 索引性能分析

### 1. SHOWPLAN 命令
SHOWPLAN命令用来显示SQL Server查询执行计划的详细信息。查询执行计划是SQL Server执行查询时选择如何访问表和索引的步骤。

**SHOWPLAN的类型：**
- SHOWPLAN_XML: 显示执行计划的XML格式。这种格式包含了非常详细的执行计划信息，通常适用于需要分析和处理执行计划的场景。
- SHOWPLAN_TEXT: 显示以文本格式的执行计划信息。相对简单易读，适合快速查看和理解执行计划。
- SHOWPLAN_ALL: 提供比SHOWPLAN_TEXT更详细的执行计划信息，包含了执行计划中各个操作的更多内部细节。
```sql
-- 在例子中，执行查询时SQL Server不会真正执行查询，而是返回查询的执行计划，帮助查看查询如何执行。
USE COLLEGE
GO
SET SHOWPLAN_XML ON -- SHOWPLAN_XML 可以被替换为另外两个showplan选项
GO
SELECT Name, Sex, Birthday
FROM Student
WHERE Name = 'John'
GO
SET SHOWPLAN_XML OFF
GO
```
### 2. STATISTICS IO 命令
STATISTICS IO命令用于显示SQL Server执行查询时，涉及的磁盘I/O操作的详细信息。
```sql
USE COLLEGE
GO
SET STATISTICS IO ON
GO
SELECT CourseName, Credit
FROM Course
WHERE Credit > 3
GO
SET STATISTICS IO OFF
GO
```
执行查询后，SQL Server会返回查询执行期间的磁盘I/O统计信息。

# 创建视图
视图是基于查询结果的虚拟表，用于简化操作和增强数据安全。
## 语法
```sql
CREATE VIEW [ schema_name . ] view_name [ (column [ ,...n ] ) ]
[ WITH <view_attribute> [ ,...n ] ]
AS select_statement [ ; ]
[ WITH CHECK OPTION ]
```

## 例子
```sql
USE COLLEGE
GO
CREATE VIEW VIEW_Score_COMPUTER(学号,姓名,学院名,课程名,分数)
AS
SELECT Student.StudentID, Student.Name, School.SchoolName, Course.CourseName, Mark.Score
FROM Student, School, Course, Mark
WHERE Student.StudentID = Mark.StudentID
  AND Course.CourseID = Mark.CourseID
  AND Student.SchoolID = School.SchoolID
  AND SchoolName = '计算机学院'
GO


USE COLLEGE
GO
CREATE VIEW VIEW_Score_AVG_SUM(姓名,平均分,总分)
AS
SELECT Student.Name,AVG(Score),SUM(Score)
FROM Student,Course,Mark
WHERE Student.StudentID=Mark.StudentID
AND Course.CourseID=Mark.CourseID
GROUP BY Student.Name
GO
```

# 查询视图

使用与查询表相同的语法进行视图查询。

## 例子
```sql
USE COLLEGE
GO
SELECT *
FROM VIEW_Score_COMPUTER -- 这是一个视图，而不是表
WHERE 分数>=90
GO
```

# 更新视图

要使视图成为可更新视图，必须满足以下几个条件

1. **单个表的列：**

任何修改（包括UPDATE、INSERT和DELETE语句）只能涉及一个基础表的列。这意味着通过视图进行的数据修改，不能涉及多个表的联合操作，且修改的数据必须直接对应基础表的某些列。  

2. **不能通过计算或聚合派生的列：**

视图中的列必须直接引用表中的列数据。它们不能通过计算派生出来，例如使用聚合函数（如AVG、COUNT、SUM等）进行计算，或者通过表达式（例如列之间的运算）进行修改。也不能包含使用集合运算符（如UNION、UNION ALL等）产生的列。因为这些列的计算结果在视图层无法反向推送到基础表。

3. **不能受GROUP BY、TOP、HAVING或DISTINCT子句影响：**

如果视图中包含GROUP BY、TOP、HAVING或DISTINCT等子句，视图中的列就不能用于更新。这是因为这些子句可能会对数据进行聚合、限制或去重操作，导致视图的数据不是基础表数据的直接映射，无法正确地反向更新到基础表。

## 例子

```sql
USE COLLEGE
GO
UPDATE VIEW_Score_COMPUTER
SET 分数 = 分数 + 2
WHERE 姓名 = '刘雨航' AND 课程名 = '大学物理'
GO

-- 如果平均分是通过某个聚合计算（如AVG函数）得出的，那么这个视图就不符合可更新视图的条件。
USE COLLEGE
GO
UPDATE VIEW_Score_AVG_SUM
SET 平均分 = 平均分 + 2
WHERE 姓名 = '刘雨航'
GO

-- 该视图显示每个学生的平均分，但由于它使用了AVG()聚合函数，无法通过该视图进行更新。
CREATE VIEW VIEW_Score_AVG AS
SELECT 姓名, AVG(分数) AS 平均分
FROM Scores
GROUP BY 姓名;
```

# 修改视图

## 语法
```sql
ALTER VIEW [ schema_name . ]
view_name -- 必填：要创建或修改的视图名称
[ ( column [ ,...n ] ) ] -- 定义视图返回结果的列名列表，需与 SELECT 查询的列数量和顺序一致
[ WITH <view_attribute> -- 指定视图的附加属性
[ ,...n ] ] -- 多个属性时，用逗号分隔
AS 
select_statement -- 视图的核心查询语句，定义视图从些表中选取哪些数据
[ ; ]-- 语句结束分号，T-SQL 中不是必须的，但建议加以提高兼容性

[ WITH CHECK OPTION ]-- 启用后，插入或更新数据时必须满足 SELECT 中的 WHERE 条件，否则操作失败
```

## 例子

```sql
USE COLLEGE
GO
-- 修改视图，以新的查询替代
ALTER VIEW VIEW_Score_COMPUTER(学号, 姓名, 学院名, 课程名, 分数)
AS
SELECT 
    s.StudentID,
    s.Name,
    sch.SchoolName,
    c.CourseName,
    m.Score
FROM 
    Student s
    INNER JOIN Mark m ON s.StudentID = m.StudentID
    INNER JOIN Course c ON m.CourseID = c.CourseID
    INNER JOIN School sch ON s.SchoolID = sch.SchoolID
WHERE 
    sch.SchoolName = '物理学院'
GO
```

# 删除视图

## 语法
```sql
DROP VIEW view_name
```

## 例子
```sql
--删除VIEW_Score_AVG_SUM视图。
DROP VIEW VIEW_Score_AVG_SUM
```

# 用户定义函数

## 标量值函数
### 语法
```sql
-- 创建标量值函数
CREATE FUNCTION [ schema_name. ] function_name 
( 
    [ { @parameter_name [ AS ][ type_schema_name. ] parameter_data_type 
        [ = default ] [ READONLY ] } 
    [ ,...n ] 
)
RETURNS return_data_type
    [ WITH <function_option> [ ,...n ] ]
    [ AS ]
    BEGIN 
        -- 函数主体
        function_body 
        -- 返回值
        RETURN scalar_expression
    END
```

### 例子
```sql
--创建标量值函数FUN_SUM，函数返回两个数的和。
USE COLLEGE
GO
CREATE FUNCTION FUN_SUM
(@i INT,@j INT)
RETURNS INT
AS
BEGIN
  DECLARE @s INT
  SET @s=@i+@j
  RETURN @s
END
GO

--调用FUN_SUM函数，求两个数的和。
USE COLLEGE
GO
DECLARE @m INT
DECLARE @n INT
SET @m=10
SET @n=20
SELECT dbo.FUN_SUM(@m,@n)
GO


--创建标量值函数FUN_AVGScore，代入某课程号，函数返回某门课程的平均分。
USE COLLEGE
GO
CREATE FUNCTION FUN_AVGScore(@CID INT)
RETURNS FLOAT
AS
BEGIN
  DECLARE @avgscore FLOAT
  SELECT @avgscore=AVG(Score)
  FROM Mark
  WHERE CourseID=@CID
  GROUP BY CourseID
  RETURN @avgscore
END
GO
--调用该函数。
USE COLLEGE
GO
SELECT dbo.FUN_AVGScore(021)
GO
```

## 内嵌表值函数
内嵌表值函数是一种用户自定义函数（User-Defined Function，UDF），其返回结果是一个表（TABLE），并且该表是由一个单独的 SELECT 语句定义的。
### 语法
```sql
CREATE FUNCTION [ schema_name. ] function_name 
(
  [ @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type 
    [ = default ] [ READONLY ] 
  [, ...n ] 
  ]
)
RETURNS TABLE
  [ WITH <function_option> [ ,...n ] ]
AS
RETURN [ ( ] select_stmt [ ) ]

```
### 例子
```sql
USE PUBLISH
GO
CREATE FUNCTION FUN_Book(@Bid INT)
RETURNS TABLE
AS
RETURN
(
  SELECT BookID,BookName
  FROM Book
  WHERE TypeID=@Bid
)
GO
--创建完成后，调用该函数。
USE PUBLISH
GO
SELECT * 
FROM dbo.FUN_Book (1)
GO
--结果显示类型编号为“1”号的图书名称。
```
## 多语句表值函数
### 语法
```sql
CREATE FUNCTION [ schema_name. ] function_name 
( 
    [ 
      { @parameter_name [ AS ] [ type_schema_name. ] parameter_data_type 
        [ = default ] [ READONLY ] } 
      [ ,...n ] 
    ]
)
RETURNS @return_variable TABLE (<table_type_definition>)
    [ WITH <function_option> [ ,...n ] ]
AS
BEGIN 
    function_body
    RETURN
END
```
### 例子
```sql
创建多语句表值函数
USE COLLEGE
GO
CREATE FUNCTION FUN_Sch(@schname NCHAR(20))
RETURNS @stuSch  TABLE
(
  stuid   INT PRIMARY KEY NOT NULL,
  stuName NCHAR(10)       NOT NULL,
  stuSex  NCHAR(2)        NOT NULL
)
AS
BEGIN
 INSERT @stuSch
   SELECT StudentID,Name,Sex
   FROM Student
   WHERE SchoolID=
   (
     SELECT SchoolID
     FROM School
     WHERE SchoolName=@schname    
   )  
 RETURN
END
GO


--调用该函数。
USE COLLEGE
GO
SELECT *
FROM dbo.FUN_Sch('计算机学院')
GO
--结果显示计算机学院学生的信息。

```

# 创建存储过程
存储过程（Stored Procedure）是一组由SQL语句组成的程序，可以通过数据库管理系统（如SQL Server）进行管理和执行。存储过程可以用来封装一系列的数据库操作，提高数据库的性能、可维护性、安全性以及代码复用性。

## 语法
```sql
CREATE { PROC | PROCEDURE } [schema_name.] procedure_name 
    [ ; number ] 
    [ { @parameter [ type_schema_name. ] data_type } 
        [ VARYING ] [ = default ] [ OUT | OUTPUT ] [READONLY]
    ] [ ,...n ] 
[ WITH <procedure_option> [ ,...n ] ]
[ FOR REPLICATION ] 
AS { <sql_statement> [;][ ...n ] | <method_specifier> }

```

### 创建存储过程的基本步骤

在创建存储过程时，通常需要确定以下三个主要组成部分：

1. **输入参数和输出参数**：
   - 存储过程可以有一个或多个输入参数（例如，查询的条件、需要处理的数据等），也可以有输出参数，用于返回结果。
   - 输入参数用于接收外部传入的数据，输出参数用于将结果返回给调用者。

2. **执行的SQL操作**：
   - 存储过程内部包含针对数据库的操作，例如 `SELECT`、`INSERT`、`UPDATE`、`DELETE`等。
   - 存储过程也可以调用其他存储过程，执行复杂的业务逻辑。

3. **返回状态值**：
   - 存储过程通常会返回一个状态值，以便调用者知道该过程是否成功执行。成功时，通常返回`0`或`1`；失败时，返回非零值。

### `CREATE PROCEDURE`语句的语法

创建存储过程的基本语法如下：

```sql
CREATE { PROC | PROCEDURE } [schema_name.] procedure_name 
    [ ; number ] 
    [ { @parameter [ type_schema_name. ] data_type } 
        [ VARYING ] [ = default ] [ OUT | OUTPUT ] [READONLY]
    ] [ ,...n ] 
[ WITH <procedure_option> [ ,...n ] ]
[ FOR REPLICATION ] 
AS { <sql_statement> [;][ ...n ] | <method_specifier> }
```

#### 语法说明：

1. **`CREATE PROCEDURE`**：用来定义存储过程，关键字可以是`PROC`或`PROCEDURE`。`schema_name`为存储过程所属的架构名，`procedure_name`为存储过程的名称。
 
2. **参数声明**：
   - 存储过程支持参数的声明，包括输入参数和输出参数。`@parameter`用于声明参数，`data_type`指定参数的数据类型。
   - **`OUTPUT`**表示输出参数，表示调用存储过程时，可以通过这个参数将值返回给调用者。
   - 参数可以指定默认值，例如 `@param INT = 100` 表示如果调用时没有传入该参数，默认使用100。

3. **`WITH`选项**：可以设置存储过程的附加选项，例如是否为复制使用（`FOR REPLICATION`）。
 
4. **SQL语句**：`AS`后跟存储过程的主体部分，可以包含一个或多个SQL语句，用来实现存储过程的核心功能。

### 存储过程的常见使用场景

1. **封装业务逻辑**：
   存储过程可以将复杂的业务逻辑封装成单一的数据库对象，简化应用程序的数据库操作。

2. **提高性能**：
   存储过程通过在数据库服务器端执行，减少了客户端与数据库之间的网络流量，可以提升性能。

3. **提高安全性**：
   存储过程可以限制对敏感数据的访问，只通过存储过程对数据进行操作，避免直接对表进行访问。

### 创建存储过程的注意事项

1. **不能使用某些语句**：
   存储过程内部不能使用某些创建或修改数据库对象的语句，如 `CREATE AGGREGATE`、`CREATE RULE`等。

2. **参数声明和使用**：
   - 存储过程的参数可以是输入、输出或只读（`READONLY`）。输出参数将值返回给调用者。
   - 临时表只能在存储过程中使用，退出存储过程后会自动消失。

3. **执行远程存储过程的注意事项**：
   - 如果存储过程在远程 SQL Server 实例上执行更改，这些更改不能被回滚，因为远程存储过程不参与本地事务处理。

4. **架构的影响**：
   - 存储过程中的对象访问通常依赖于创建存储过程的用户的权限。如果表或视图没有明确的架构，默认使用存储过程所在架构的权限。

5. **加密存储过程定义**：
   - 使用 `WITH ENCRYPTION` 选项可以对存储过程定义进行加密，以防止用户查看其内容。

6. **命名规则**：
   - 不要以 `sp_` 为前缀创建存储过程，因为 `sp_` 前缀是SQL Server系统存储过程的约定，使用该前缀可能导致未来的冲突。

## 例子

```sql
-- 存储过程 GetEmployeeDetails 接受一个 EmployeeID 作为输入参数，并通过输出参数 EmployeeName 返回该员工的名字。如果员工不存在，则会输出错误消息。
CREATE PROCEDURE GetEmployeeDetails
    @EmployeeID INT,
    @EmployeeName NVARCHAR(100) OUTPUT
AS
BEGIN
    SELECT @EmployeeName = EmployeeName
    FROM Employees
    WHERE EmployeeID = @EmployeeID;
  
    IF @EmployeeName IS NULL
    BEGIN
        PRINT 'Employee not found';
    END
    ELSE
    BEGIN
        PRINT 'Employee found: ' + @EmployeeName;
    END
END;


-- 在COLLEGE数据库中创建存储过程，将Mark表中所有226号课程的分数加5分。
USE COLLEGE
GO
CREATE PROC PROC_AddScore
AS
UPDATE Mark
SET Score=Score+5
WHERE CourseID='226'
GO


--创建带有通配符参数的存储过程。
--下面的存储过程只从Student表中返回指定的一些学生（提供名字和姓氏）的信息。该存储过程对传递的参数进行模式匹配，如果没有提供参数，则返回所有学生的信息。
USE COLLEGE
GO
CREATE PROC PROC_Name
@stuname NCHAR(20)='%'
AS
SELECT *
FROM Student
WHERE Name LIKE @stuname
GO

--创建使用OUTPUT参数的存储过程。
USE COLLEGE
GO
CREATE PROCEDURE PROC_GetStudentAveAge
@schid NCHAR(2),
@aveage INT OUTPUT
AS 
  Set @aveage=
  (
   SELECT AVG(YEAR(GETDATE())-YEAR(Birthday))
   FROM Student
   WHERE SchoolID=@schid
  )
GO
```

# 调用存储过程
```sql
USE COLLEGE
GO
EXECUTE dbo.PROC_AddScore
GO

-- 调用时需要输入参数值,参数值与存储过程名中间用空格分开。
--EXECUTE可以缩写为EXEC
USE COLLEGE
GO
EXEC dbo.PROC_AddScore1 2
GO
-- 
USE COLLEGE
GO
EXEC dbo.PROC_Name '王%'
GO
-- 
USE COLLEGE
GO
DECLARE @stubiravg INT
EXEC dbo.PROC_GetStudentAveAge '1',@stubiravg OUTPUT
PRINT '2号学院的学生平均年龄是'+STR(@stubiravg)+'岁'
GO
```

# 创建触发器
## 语法
```sql
CREATE TRIGGER [ schema_name . ]trigger_name 
ON { table | view } 
[ WITH <dml_trigger_option> [ ,...n ] ]
{ FOR | AFTER | INSTEAD OF } 
{ [ INSERT ] [ , ] [ UPDATE ] [ , ] [ DELETE ] } 
[ WITH APPEND ] 
[ NOT FOR REPLICATION ] 
AS 
{ sql_statement  [ ; ] [ ...n ] | EXTERNAL NAME <method specifier [ ; ] > }
```
### 关键部分解释：

- `schema_name.trigger_name`：触发器的完整名称，可以指定架构（如 `dbo.MyTrigger`）。
- `ON { table | view }`：指定触发器所关联的对象（通常是**表**，INSTEAD OF 可以用于视图）。
- `WITH <dml_trigger_option>`：用于指定触发器的附加属性，如 `ENCRYPTION`（加密触发器体）或 `EXECUTE AS`。
- `{ FOR | AFTER | INSTEAD OF }`：指定触发时机：
  - `FOR` 和 `AFTER` 实际等价，都是表示在数据操作执行 **之后** 执行触发器。
  - `INSTEAD OF` 表示替代原有数据操作执行触发器逻辑（常用于视图）。
- `{ INSERT | UPDATE | DELETE }`：触发器响应的操作类型，可以是多个。
- `WITH APPEND`：当一个同类型触发器已存在时，使用该选项可以追加而不是替换原有触发器（仅 SQL Server 2005+，且仅适用于 AFTER 触发器）。
- `NOT FOR REPLICATION`：复制操作不激活该触发器，避免复制时误触发业务逻辑。
- `AS { sql_statement }`：触发器体，即在触发时执行的 SQL 语句块。可为一条或多条语句。

## 触发器类型

T-SQL 中的触发器分为三类：

- **DML触发器（Data Manipulation Language）**：用于响应 INSERT、UPDATE 或 DELETE 操作。
  - AFTER 触发器（默认）在操作完成后执行。
  - INSTEAD OF 触发器在操作发生前拦截，并可替代执行。
- **DDL触发器（Data Definition Language）**：用于响应如 CREATE、ALTER、DROP 等数据库结构更改语句。
  - 用法不同于 `CREATE TRIGGER ON table`，而是 `ON DATABASE` 或 `ON ALL SERVER`。
- **登录触发器（Logon Trigger）**：用于响应登录事件（`CREATE TRIGGER ... ON ALL SERVER FOR LOGON`）。

## 例子
```sql
CREATE TRIGGER trg_AuditUpdate
ON Employees
AFTER UPDATE
AS
BEGIN
    INSERT INTO EmployeeAudit (EmpID, OldSalary, NewSalary, ChangeDate)
    SELECT d.EmpID, d.Salary, i.Salary, GETDATE()
    FROM deleted d
    INNER JOIN inserted i ON d.EmpID = i.EmpID
    WHERE d.Salary <> i.Salary
END

--创建DDL触发器。
--下列代码说明了如何使用DDL触发器来防止数据库中的任一表被修改或删除。
USE COLLEGE
GO
CREATE TRIGGER safety
ON database
FOR DROP_TABLE, ALTER_TABLE 
AS 
   PRINT '你必须使safety触发器无效才能执行对表的操作!' 
   ROLLBACK
GO


--使用包含提醒消息的DML触发器。
USE COLLEGE
GO
CREATE TRIGGER reminder
ON Student
AFTER INSERT, UPDATE
AS RAISERROR ('你在插入或修改学生表的数据', 16, 10)
GO
```

# 禁止或删除触发器
## 语法
- 禁用触发器：
```sql
DISABLE TRIGGER trigger_name ON table_name;
```
- 启用触发器：
```sql
ENABLE TRIGGER trigger_name ON table_name;
```
- 删除触发器：
```sql
DROP TRIGGER trigger_name;
```

# 创建游标
## 语法
```sql
DECLARE cursor_name CURSOR
[ LOCAL | GLOBAL ]
[ FORWORD_only | SCROLL ]
[ STATIC | KEYSET | DYNAMIC | FAST_FORWARD ]
[ READ_ONLY | SCROLL_LOCKS | OPTIMISTIC ]
[ TYPE_WARING ]
FOR select_list
[ FOR UPDATE [ OF column_name [,…n ] ] ]
```

### **解析：**

1. **LOCAL / GLOBAL**：
   - **LOCAL**：游标的作用域限制在当前的存储过程、触发器或批处理中。当存储过程结束时，游标会自动关闭并释放资源。
   - **GLOBAL**：游标的作用域是全局的，意味着它在整个会话期间都有效，直到用户断开数据库连接时才会释放。

2. **FORWARD_ONLY / SCROLL**：
   - **FORWARD_ONLY**：游标只能按顺序（从第一行到最后一行）处理结果集。只能使用 `FETCH NEXT` 操作。
   - **SCROLL**：支持任意方向的滚动，允许使用更多的定位操作，如 `FIRST`、`LAST`、`PRIOR`、`NEXT`、`RELATIVE`、`ABSOLUTE` 等。

3. **STATIC / KEYSET / DYNAMIC / FAST_FORWARD**：
   - **STATIC**：游标读取的数据是静态的，数据的变化不会影响已经提取的数据。此类游标将会将查询结果存储在临时表中，数据的变化无法反映。
   - **KEYSET**：游标使用键值（唯一标识）来识别数据，每次提取数据时，基于初始结果集的数据顺序进行定位。该类型的游标对表的变化有一定的反应。
   - **DYNAMIC**：游标能够实时反映表中的数据变化，包括数据的插入、删除或更新。它是最灵活的，但也最占用资源。
   - **FAST_FORWARD**：这是一个针对 `FORWARD_ONLY` 且 `READ_ONLY` 类型游标的优化选项，旨在提高性能。如果使用了 `SCROLL` 或 `FOR_UPDATE`，则无法使用此选项。

4. **READ_ONLY / SCROLL_LOCKS / OPTIMISTIC**：
   - **READ_ONLY**：游标只能读取数据，不能修改。
   - **SCROLL_LOCKS**：在游标提取数据时，会对数据加锁，确保在游标作用范围内不会发生冲突。这对于并发修改非常重要，但也会导致性能问题。
   - **OPTIMISTIC**：如果游标数据已经发生变化，更新或删除时可能会失败。此选项在并发环境下有用，但不适合高并发修改的场景。

5. **TYPE_WARNING**：如果游标类型与用户定义的类型不一致，将会发送警告信息给客户端。

#### 游标的使用场景：
游标一般用于以下情况：
- **逐行处理查询结果**：比如在处理查询返回的数据时，需要对每一行数据进行特殊处理。
- **复杂数据操作**：如当涉及到多表连接、复杂聚合等操作时，游标可以简化程序逻辑。
- **事务控制**：游标在处理数据时，通常会配合事务使用，以确保数据的原子性、一致性、隔离性和持久性（ACID特性）。

## 例子
```sql
-- 声明一个名为Stu_Cur的游标，是只读的，游标只能从头到尾顺序读取数据。
USE COLLEGE 
GO
DECLARE Stu_Cur CURSOR
FOR
SELECT StudentID,Name,Sex,SchoolName
FROM Student,School
WHERE Student.SchoolID=School.SchoolID
AND SchoolName='计算机学院'
FOR READ ONLY
GO

--声明一个名为Pro_Cur的游标。该游标与单个表的查询结果集关联，是动态的，可前后滚动，其中Name列数据可以修改。
USE PUBLISH 
GO
DECLARE Pro_Cur CURSOR
DYNAMIC
FOR
SELECT Name,Sex
FROM Author
WHERE Provinces='北京'
FOR UPDATE OF Name
GO
```

# 使用游标
## 打开游标
```sql
OPEN [GLOBAL] cursor_name
-- 
USE COLLEGE
GO
OPEN Stu_Cur
```

## 读取游标
```sql
FETCH
[ [ NEXT | PRIOR | FIRST | LAST
| ABSOLUTE { n | @nvar }
| RELATIVE { n | @nvar }
]
FROM
]
{ { [ GLOBAL ] cursor_name } | @cursor_variable_name }
[ INTO @variable_name [ ,...n ] ]

USE COLLEGE
GO
FETCH NEXT FROM Stu_Cur
GO

USE PUBLISH
GO
FETCH NEXT FROM Pro_Cur
FETCH FIRST FROM Pro_Cur
FETCH LAST FROM Pro_Cur
FETCH PRIOR FROM Pro_Cur
FETCH RELATIVE 3 FROM Pro_Cur
GO
```

## 关闭游标
```sql
CLOSE curso_name

CLOSE Stu_Cur
```

## 删除游标
```sql
DEALLOCATE curso _name

USE PUBLISH
GO
CLOSE Pro_Cur
DEALLOCATE Pro_Cur
GO
```

# 用户权限管理
## 创建用户
```sql
-- 新建一个名字为“cheng”的账号，密码是“123456”
CREATE LOGIN cheng WITH PASSWORD = '123456'

--把账号“cheng”授予数据库PUBLISH，成为该数据库用户
-- 运行后，重新以“cheng”账号连接登录服务器，可以查看PUBLISH数据库，但看不到该数据库中的表，也不能进行其他用户
USE PUBLISH
GO
CREATE USER cheng FOR LOGIN cheng
GO
```

## 分配用户权限
`GRANT`语句用于将某些权限授予一个或多个主体（如用户、角色等）以允许他们在特定的安全对象（如数据库、表、视图、存储过程等）上执行特定的操作
### 语法
```sql
GRANT { ALL [ PRIVILEGES ] }
    | permission [ ( column [ ,...n ] ) ] [ ,...n ]
    [ ON [ class :: ] securable ] TO principal [ ,...n ] 
    [ WITH GRANT OPTION ] [ AS principal ]
```



#### 主要组成部分：
1. **ALL [ PRIVILEGES ]**:
   - **ALL** 代表授予所有权限。不同类型的安全对象（如数据库、表、视图等）有不同的“ALL”权限组合。比如，对于表而言，“ALL”意味着授予 `DELETE`、`INSERT`、`REFERENCES`、`SELECT` 和 `UPDATE` 权限

2. **permission [ ( column [ ,...n ] ) ] [ ,...n ]**:
   - **permission** 是你授予主体的权限名称。例如，`SELECT`、`INSERT`、`UPDATE`、`DELETE` 等。
   - 你可以指定具体的 **列**（`column`），而不仅仅是授予对整个表或视图的权限。这对于控制权限粒度非常有用。如果指定了列，则权限只在指定的列上有效。

3. **ON [ class :: ] securable**:
   - **class**：指示授予权限的对象类型（例如，`TABLE`、`VIEW`、`PROCEDURE`、`DATABASE` 等）。该部分可以使用范围限定符 `::` 来明确指定对象类型。
   - **securable**：具体的安全对象，可以是表、视图、函数、数据库等。

4. **TO principal [ ,...n ]**:
   - **principal**：指授予权限的主体（用户或角色）的名称。主体可以是一个或多个，可以用逗号分隔。
   - 例如，如果你要把权限授予用户 `user1` 和角色 `role1`，可以指定：`TO user1, role1`。

5. **WITH GRANT OPTION**:
   - **WITH GRANT OPTION** 允许被授权的主体在获取权限的同时，还能将该权限进一步授予其他主体。
   - 如果没有这个选项，被授权的主体只能使用所授予的权限，而不能再将其转授给其他主体。

6. **AS principal**:
   - **AS principal** 允许你以某个指定的主体身份执行 `GRANT` 语句。这意味着，授予权限的操作是由某个不同的主体来执行的，而非当前的数据库用户。
   - 这种方式常用于需要以系统管理员身份执行操作时，模拟其他主体来授予权限。

### 例子

1. **授予用户对表的SELECT和INSERT权限**：
   ```sql
   GRANT SELECT, INSERT ON Employees TO user1;
   ```
   这个语句授予 `user1` 对 `Employees` 表的 `SELECT` 和 `INSERT` 权限。

2. **授予用户对某些列的权限**：
   ```sql
   GRANT SELECT (name, age) ON Employees TO user1;
   ```
   这个语句授予 `user1` 仅对 `Employees` 表的 `name` 和 `age` 列的 `SELECT` 权限。

3. **授予用户对数据库的所有权限**：
   ```sql
   GRANT ALL ON DATABASE MyDatabase TO user1;
   ```
   这个语句授予 `user1` 对 `MyDatabase` 数据库的所有权限。

4. **使用GRANT OPTION允许转授权**：
   ```sql
   GRANT SELECT ON Employees TO user1 WITH GRANT OPTION;
   ```
   这个语句不仅授予 `user1` 对 `Employees` 表的 `SELECT` 权限，还允许 `user1` 将该权限授予其他用户。

5. **以系统管理员身份执行GRANT**：
   ```sql
   GRANT SELECT ON Employees TO user1 AS sysadmin;
   ```
   这个语句表示当前的数据库管理员 `sysadmin` 以其身份授予 `user1` 对 `Employees` 表的 `SELECT` 权限。

## 收回用户权限
### 语法
```sql
REVOKE [ GRANT OPTION FOR ]
      { 
        [ ALL [ PRIVILEGES ] ]
        |
                permission [ ( column [ ,...n ] ) ] [ ,...n ]
      }
      [ ON [ class :: ] securable ] 
      { TO | FROM } principal [ ,...n ] 
      [ CASCADE] [ AS principal ]
```

你提供的是 SQL Server 2012 中 `REVOKE` 语句的语法与说明，其作用是**撤销一个主体（如用户、角色等）对数据库对象的权限**。下面我将对这条语句进行详细介绍，并在最后补充一些实用示例和注意事项。

---

### 一、REVOKE 语句语法解析

```sql
REVOKE [ GRANT OPTION FOR ]
   { 
     [ ALL [ PRIVILEGES ] ]
     |
     permission [ ( column [ ,...n ] ) ] [ ,...n ]
   }
   [ ON [ class :: ] securable ] 
   { TO | FROM } principal [ ,...n ] 
   [ CASCADE ] 
   [ AS principal ]
```

#### 参数说明：

1. **`GRANT OPTION FOR`**
   - 表示撤销的是“授予他人权限”的能力（而非直接使用该权限的能力）。
   - 如果某用户 A 被授予了某权限，并且带有 GRANT OPTION，那么 A 可以将该权限再授予其他用户 B。
   - 如果要撤销这个“传递权限”的能力，需要加上 `GRANT OPTION FOR`。

2. **`ALL [ PRIVILEGES ]`**
   - 撤销该主体对目标对象的**所有权限**。
   - `PRIVILEGES` 是可选的装饰词。

3. **`permission [ (column [...]) ]`**
   - 指定要撤销的权限，例如：`SELECT`、`INSERT`、`UPDATE`、`EXECUTE` 等。
   - 对于列级权限，可以指定特定的列。

4. **`ON [ class:: ] securable`**
   - 指定要撤销权限的**安全对象（securable）**，如：
     - `TABLE`、`DATABASE`、`SCHEMA`、`VIEW`、`STORED PROCEDURE` 等。
   - `class::` 是可选的分类说明词，比如 `OBJECT::MyTable`。

5. **`TO | FROM principal`**
   - 指定权限的**主体（principal）**，如数据库用户、角色、登录名等。
   - 在 `REVOKE` 中应该使用 `FROM`，因为是在撤销权限。

6. **`CASCADE`**
   - 表示权限撤销时，也要自动撤销由该主体传递给其他主体的权限（“级联撤销”）。
   - **只能在指定了 `GRANT OPTION FOR` 时使用**。

7. **`AS principal`**
   - 表示以某个主体的身份执行 `REVOKE`，用于跨数据库权限管理等高级场景。

### 例子

```sql
--把账号cheng修改Author表AuthorID列的权限收回。
REVOKE UPDATE(AuthorID)
ON Author
FROM cheng

--把账号cheng对Author表的INSERT权限收回。
REVOKE INSERT
ON Author
FROM cheng CASCADE

--收回所有账号对教师表的查询权限。
REVOKE SELECT
ON Author
FROM PUBLIC
```

## DENY 语句
用户可使用DENY语句,防止主体通过其组或角色成员身份继承权限。
即使权限是通过角色或其他用户继承的，DENY 也会覆盖所有权限。
### 语法
```sql
DENY { ALL [ PRIVILEGES ] }
      | permission [ ( column [ ,...n ] ) ] [ ,...n ]
      [ ON [ class :: ] securable ] TO principal [ ,...n ] 
      [ CASCADE] [ AS principal ]
```
如果某主体的该权限是通过指定GRANT OPTIONDENY获得的，那么，在撤销其该权限时，如果未指定CASCADE，则DENY将失败。
### 例子
```sql
--拒绝账号cheng对Author表的SELECT权限。
DENY SELECT ON Author TO cheng
```

# 事物的概念

## ACID原则
ACID原则是数据库管理系统（DBMS）在事务处理中必须遵循的四个基本特性，它保证了数据库操作的可靠性和一致性。

1. **原子性（Atomicity）**：
   - **定义**：事务是数据库操作的基本单位。事务中的所有操作要么全部执行，要么全部不执行。换句话说，事务要么成功完成（提交），要么完全回滚（失败）。如果事务执行过程中出现了错误，已经执行的操作需要恢复到事务开始前的状态。
   - **举例**：假设你正在进行银行转账操作，假如你从A账户转账到B账户，若在转账过程中网络中断或者出现其他故障，原子性要求A账户的扣款和B账户的存款操作要么都成功，要么都不做。

2. **一致性（Consistency）**：
   - **定义**：数据库在事务执行前后必须处于一致的状态。也就是说，事务的执行不能违反数据库的完整性约束条件。无论事务执行是否成功，数据库的状态必须从一个一致的状态转换到另一个一致的状态。
   - **举例**：在进行银行转账时，账户的余额不应该为负数，且交易金额必须在账户余额范围内。如果发生了这种不一致的情况，事务应当回滚并恢复数据库的原始状态。

3. **隔离性（Isolation）**：
   - **定义**：一个事务的执行不应受到其他事务的干扰。多个事务并发执行时，一个事务的中间状态对其他事务是不可见的，直到该事务提交（成功）或者回滚（失败）。这样可以避免并发事务引发的数据不一致问题。
   - **举例**：假设有两个银行转账事务同时进行，隔离性保证在事务执行过程中，A账户的余额更新在事务提交之前，其他事务不能看到这个中间状态，也无法对A账户进行修改。

4. **持久性（Durability）**：
   - **定义**：事务一旦提交，其结果就会被永久保存在数据库中，即使系统发生崩溃或断电，数据也不应丢失。
   - **举例**：在银行转账操作成功提交后，无论系统发生什么故障，已转账的金额依然存在于数据库中。

## 事务分类

SQL Server 2012根据事务的设置和用途将事务分为不同类型。这里具体介绍了两类事务：**系统事务** 和 **用户定义的事务**。

### 1. **系统事务**：
   - **定义**：系统事务是由数据库系统自动管理和控制的事务。执行某些数据库操作时，SQL Server会自动为这些操作管理事务。你无需显式地开始、提交或回滚事务，SQL Server会在执行相关语句时自动处理事务。
   - **相关语句**：以下操作自动成为一个事务，并且其执行是自动提交的（即执行成功后自动提交事务）。
     - `ALTER TABLE`：修改表结构。
     - `CREATE`：创建数据库对象（如表、视图等）。
     - `DELETE`：删除数据。
     - `DROP`：删除数据库对象。
     - `FETCH`：在游标中获取数据。
     - `GRANT`：授权用户权限。
     - `INSERT`：插入数据。
     - `OPEN`：打开游标。
     - `REVOKE`：撤销授权。
     - `SELECT`：查询数据。
     - `UPDATE`：更新数据。
     - `TRUNCATE TABLE`：删除所有表数据，但不记录每一行的删除操作。

   这些系统提供的事务一般都会进行自动的提交或回滚操作，因此你不需要显式地管理事务。

### 2. **用户定义的事务**：
   - **定义**：用户定义的事务是由开发人员手动开始、提交或回滚的事务。通常用户会显式地使用 `BEGIN TRANSACTION`、`COMMIT TRANSACTION` 和 `ROLLBACK TRANSACTION` 来管理事务的开始、提交和回滚。
   - **特点**：
     - `BEGIN TRANSACTION`：表示开始一个事务。
     - `COMMIT TRANSACTION`：表示提交事务，使所有变更永久保存。
     - `ROLLBACK TRANSACTION`：表示回滚事务，撤销事务中对数据的所有更改。
  


# 用户定义事物
## `BEGIN TRANSACTION` 启动事务

### 语法
```sql
BEGIN TRANSACTION TranName;
```

### 分析：
- 启动一个事务，此后对数据库所做的更改都属于该事务。
- 可以命名事务以提高可读性。
- **嵌套事务**：SQL Server 允许嵌套事务，但只有**最外层事务的提交**才会实际生效。

### 示例：
```sql
BEGIN TRANSACTION Tran_UpdateSalary;
UPDATE Employees SET Salary = Salary * 1.1 WHERE Department = 'Sales';
```

## `COMMIT TRANSACTION` 提交事务

### 语法
```sql
COMMIT TRANSACTION TranName;
```

### 分析
- 将当前事务所做的所有更改**永久保存**到数据库。
- 嵌套事务中的`COMMIT`只会减少`@@TRANCOUNT`，最终外层`COMMIT`才生效。
- 如果事务成功执行，应显式提交。

### 例子
```sql
COMMIT TRANSACTION Tran_UpdateSalary;
```


## `ROLLBACK TRANSACTION` 回滚事务

### 语法
```sql
ROLLBACK TRANSACTION [TranName | SavepointName];
```

### 分析
- 取消自`BEGIN TRANSACTION`以来所做的所有更改。
- 如果指定保存点（savepoint），则回滚到该点，**保留之前的更改**。

### 例子
```sql
-- 回滚整个事务
ROLLBACK TRANSACTION Tran_UpdateSalary;

-- 部分回滚（结合保存点）
SAVE TRANSACTION Save_1;
DELETE FROM Employees WHERE Department = 'IT';
-- 发生错误
ROLLBACK TRANSACTION Save_1;
```

## `SAVE TRANSACTION` 设置保存点

### 语法
```sql
SAVE TRANSACTION SavepointName;
```

### 分析
- 在事务内部设定一个**可回滚的位置**。
- 用于**局部错误处理**，避免全部回滚。
- 通常结合`TRY...CATCH`结构使用。

### 例子
```sql
BEGIN TRANSACTION;
SAVE TRANSACTION Save_BeforeDelete;

BEGIN TRY
    DELETE FROM Employees WHERE Department = 'IT';
    COMMIT;
END TRY
BEGIN CATCH
    ROLLBACK TRANSACTION Save_BeforeDelete;
    PRINT 'Error occurred, changes rolled back to savepoint.';
    COMMIT;
END CATCH
```

## 完整例子
```sql
--定义一个事务，将所有图书类型TypeID为3的图书单价涨1.5元，并提交该事务。
USE PUBLISH
GO
DECLARE @b_price NCHAR(10)
SET @b_price='add_price'
BEGIN TRANSACTION @b_price
UPDATE Book
SET Price=Price+1.5
WHERE typeID=3
COMMIT TRANSACTION @b_price
GO

--定义一个事务，向Book表中添加记录。如果添加成功，则将TypeID号为8的类型名改为“艺术”。否则不操作。
USE PUBLISH
GO
BEGIN TRAN
INSERT INTO Book
VALUES('1436','SQL Server 2012','3081','32','1')
IF @@error=0
  BEGIN
    PRINT '添加成功！'
    UPDATE Type
    SET TypeName='艺术'
    WHERE TypeID='8'
    COMMIT TRAN
  END
ELSE
  BEGIN
    PRINT '添加失败！'
    ROLLBACK TRAN
  END

-- 将多个操作定义为一个事务 (批处理)
USE COLLEGE
GO
BEGIN TRANSACTION
UPDATE Mark
SET Score=Score-2
WHERE CourseID=5
INSERT INTO Course
VALUES('508','C#编程',4)
SELECT Name,Sex
FROM Student
WHERE Name LIKE '张%'
COMMIT TRANSACTION
```

## 事务控制流程图

```
BEGIN TRANSACTION
      ↓
  执行T-SQL操作
      ↓
-------------------------
| 正常执行 | 出现异常 |
| -------- | -------- |
| COMMIT   | ROLLBACK |
-------------------------
```

# 事物隔离等级

`SET TRANSACTION ISOLATION LEVEL` 语句用于设置当前会话的事务隔离级别。事务隔离级别决定了事务之间的并发行为，尤其是如何控制一个事务在执行过程中对其他事务的影响。这主要关系到数据一致性和并发性能。

### 事务隔离级别的分类
SQL Server 支持以下几种事务隔离级别，每个隔离级别都会对事务的执行方式产生不同的影响：

1. **READ UNCOMMITTED**
   - **定义**：允许读取未提交的数据（即脏读）。在这个隔离级别下，一个事务可以看到其他事务中尚未提交的更改。可能会导致脏读、不可重复读和幻读。
   - **适用场景**：对于对数据一致性要求不高的查询场景，或者一些对数据的读取要求较快，允许不一致数据的查询。
 
2. **READ COMMITTED**（默认隔离级别）
   - **定义**：只允许读取已经提交的数据。其他事务的更新如果尚未提交，当前事务不能看到。这避免了脏读，但仍然可能出现不可重复读和幻读。
   - **适用场景**：大多数情况下使用此隔离级别，它是默认的事务隔离级别。

3. **REPEATABLE READ**
   - **定义**：在一个事务期间，所有的数据读取操作将保持一致，即读取的数据在整个事务内是不可改变的。虽然防止了脏读和不可重复读，但可能会导致幻读。
   - **适用场景**：需要确保在整个事务中读取的数据一致，但不需要完全避免幻读的情况。

4. **SERIALIZABLE**
   - **定义**：最严格的事务隔离级别。在这个级别下，事务完全隔离，其他事务无法访问到正在被当前事务操作的数据。此级别防止了脏读、不可重复读和幻读。
   - **适用场景**：对事务一致性要求非常高的场景，例如银行系统的转账操作。

5. **SNAPSHOT**
   - **定义**：使用数据库的快照技术保证事务一致性。这避免了脏读、不可重复读和幻读的问题，但可能会增加内存消耗。
   - **适用场景**：需要确保数据一致性的同时，减少锁争用的场景。

### 例子

```sql
USE COLLEGE
GO
BEGIN TRAN
UPDATE Course
SET CourseName='足球'
WHERE CourseID=131
```
这里，`USE COLLEGE` 选择了数据库 `COLLEGE`，`BEGIN TRAN` 开启了一个事务，在这个事务中更新了 `Course` 表中 `CourseID = 131` 的记录的 `CourseName` 字段。此时事务并未提交，因此数据被锁定，其他事务无法看到这个修改。

然后在第二个查询窗口中执行：
```sql
USE COLLEGE
GO
SELECT *
FROM Course
GO
```
因为 `Course` 表中的数据尚未提交，这个查询会等待，显示“正在执行查询”的状态。由于存在未提交的事务，系统会锁定相关的数据。

### 设置隔离级别为 `READ UNCOMMITTED`
为了演示脏读，你使用了以下命令：
```sql
SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED
```
这条语句设置当前会话的事务隔离级别为 `READ UNCOMMITTED`，此时可以允许脏读，即即使其他事务没有提交，当前事务仍然能够读取到这些未提交的数据。

在这种隔离级别下，后续的查询会直接读取所有的数据，而不管它们是否已提交。这样即使第一个事务没有提交，第二个查询窗口的查询仍然可以看到更新后的数据（即便这些数据可能会被回滚）。这个行为使得“脏读”成为可能，即查询到的数据可能在后续回滚后不再有效。

```sql
SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED
```

### 补充内容

1. **脏读**：指的是一个事务读取了另一个事务中尚未提交的数据。这可能导致读取到的结果是无效的，因为另一个事务可能会回滚，这时候已读取的数据会被撤销。

2. **不可重复读**：指的是在一个事务中，重复读取同一数据时，数据的值发生了变化。这是因为另一个事务在当前事务读取数据后对数据进行了修改。

3. **幻读**：指的是在一个事务中读取的结果集与另一个事务并发修改数据时发生了变化。即在同一个事务中执行相同的查询时，结果集会发生变化。

4. **锁机制**：SQL Server 会根据事务隔离级别自动管理锁的粒度和锁的种类。在 `READ UNCOMMITTED` 级别下，不会对读取的数据加锁，因此其他事务可以自由修改这些数据。

5. **如何避免脏读**：如果应用程序中需要避免脏读，可以考虑使用 `READ COMMITTED` 或更高的事务隔离级别。常用的做法是选择 `READ COMMITTED`，它可以防止脏读，但可能会导致不可重复读。

# 锁
锁是防止其他事务访问指定的资源控制、实现并发控制的一种主要手段。为了提高系统的性能、加快事务的处理速度、缩短事务的等待时间，应该使锁定的资源最小化。

## 锁机制分类与意向锁详细说明

SQL Server 锁机制用于实现 **并发控制（Concurrency Control）**，避免 **脏读、不可重复读、幻读** 等问题。锁分类如下：

### 锁的分类（按操作类型）

| 锁类型           | 简称        | 用途                           |
| ---------------- | ----------- | ------------------------------ |
| 共享锁           | S           | 允许读操作，阻止写操作         |
| 排他锁           | X           | 写操作时使用，阻止任何其他访问 |
| 更新锁           | U           | 用于避免死锁的中间态（S→X）    |
| 意向锁           | IS/IX/SIX   | 表示将要在下层资源申请锁       |
| 架构锁           | Sch-S/Sch-M | DDL操作相关                    |
| 事务锁（元数据） | L           | 系统内部事务管理               |

### 意向锁（Intent Locks）

#### 定义：表示事务“**有意**”对更低层次的资源加锁（如对页或行），从而在高层（如表）加锁时避免冲突。

#### 类型与用途：

| 锁名                | 描述                                           |
| ------------------- | ---------------------------------------------- |
| IS（意向共享）      | 事务打算在底层资源加共享锁（如读取某行）       |
| IX（意向排他）      | 事务打算在底层资源加排他锁（如更新某行）       |
| SIX（共享意向排他） | 对高层加共享锁，同时打算对部分底层资源加排他锁 |

#### 示例：

```sql
-- 假设有一个事务读取表中某些行
BEGIN TRAN;
SELECT * FROM Orders WHERE OrderID = 100; -- 加 IS 锁在表上，加 S 锁在行上
COMMIT;
```

```sql
-- 假设有一个事务更新某行数据
BEGIN TRAN;
UPDATE Orders SET Amount = 500 WHERE OrderID = 100; 
-- 加 IX 锁在表上，加 X 锁在行上
COMMIT;
```

---

## 三、锁兼容性分析

| 请求/已有 | S   | X   | IS  | IX  | SIX |
| --------- | --- | --- | --- | --- | --- |
| **S**     | ✔️   | ❌   | ✔️   | ❌   | ❌   |
| **X**     | ❌   | ❌   | ❌   | ❌   | ❌   |
| **IS**    | ✔️   | ❌   | ✔️   | ✔️   | ✔️   |
| **IX**    | ❌   | ❌   | ✔️   | ✔️   | ❌   |
| **SIX**   | ❌   | ❌   | ✔️   | ❌   | ❌   |

---

## 死锁处理机制

死锁发生在两个或多个事务互相等待对方释放资源而无法继续执行。

### 预防死锁方法

1. **一次封锁法**：事务执行前一次性申请所有锁，失败则不执行。
2. **顺序封锁法**：规定资源访问顺序，所有事务必须按照相同顺序加锁。

### 解除死锁方法

| 方法         | 描述                                                               |
| ------------ | ------------------------------------------------------------------ |
| **超时法**   | 如果锁等待超时，则主动终止事务（适用于轻量死锁）                   |
| **等待图法** | 构建事务等待图，检测是否有环路存在，若有则中止某个事务（高级策略） |

---

## 锁的使用要求

为了提升数据库并发性能并减少锁争用：

1. **缩小锁定范围（粒度）**，如优先行锁而非表锁；
2. **尽量使用短事务**，减少持锁时间；
3. **合理设置索引**，避免全表扫描带来的大范围锁；
4. **避免交叉更新资源的事务**，减少死锁风险；
5. **监控锁等待、阻塞与死锁日志**，及时调整策略。
