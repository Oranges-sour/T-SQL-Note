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
    - [例子：](#例子)
  - [2. 变量赋值](#2-变量赋值)
    - [例子:](#例子-1)
  - [3. 变量输出](#3-变量输出)
    - [例子：](#例子-2)
- [注释](#注释)
- [LEN(·) 函数](#len-函数)
    - [例子：](#例子-3)
- [DATALENGTH(·) 函数](#datalength-函数)
    - [例子：](#例子-4)
- [创建数据库](#创建数据库)
  - [语法](#语法)
  - [1. filespec 数据文件](#1-filespec-数据文件)
    - [文件后缀：](#文件后缀)
    - [格式：](#格式)
    - [例子：](#例子-5)
  - [2. filegroup 文件组](#2-filegroup-文件组)
    - [文件后缀：  `.ndf`](#文件后缀--ndf)
    - [格式：](#格式-1)
    - [例子：](#例子-6)
  - [3. 日志文件](#3-日志文件)
    - [文件后缀：`.ldf`](#文件后缀ldf)
    - [格式：](#格式-2)
    - [例子：](#例子-7)
  - [4. 完整例子：](#4-完整例子)
- [修改数据库](#修改数据库)
  - [语法](#语法-1)
  - [1. add\_or\_modify\_files 添加或修改文件](#1-add_or_modify_files-添加或修改文件)
    - [格式：](#格式-3)
    - [例子：](#例子-8)
  - [2. add\_or\_modify\_filegroups 添加或修改文件组](#2-add_or_modify_filegroups-添加或修改文件组)
    - [格式：](#格式-4)
    - [例子:](#例子-9)
  - [完整例子：](#完整例子)
- [删除数据库](#删除数据库)
  - [语法：](#语法-2)
  - [完整例子：](#完整例子-1)
- [分离数据库](#分离数据库)
  - [语法：](#语法-3)
  - [分离时获得数据库独占权限](#分离时获得数据库独占权限)
  - [完整例子](#完整例子-2)
- [附加数据库](#附加数据库)
  - [语法：](#语法-4)
  - [完整例子：](#完整例子-3)
- [创建表](#创建表)
  - [语法：](#语法-5)
  - [1. column\_definition 列定义](#1-column_definition-列定义)
    - [格式：](#格式-5)
    - [例子：](#例子-10)
  - [2. column\_constraint 列约束](#2-column_constraint-列约束)
    - [格式](#格式-6)
    - [例子](#例子-11)
  - [完整例子：](#完整例子-4)
- [修改表](#修改表)
  - [语法：](#语法-6)
  - [完整例子：](#完整例子-5)
- [删除表](#删除表)
  - [语法：](#语法-7)
  - [完整例子：](#完整例子-6)

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
### 例子：  
```SQL
DECLARE @a INT  
DECLARE @b NCHAR(10)
```  

## 2. 变量赋值  
   `SET @变量名 = 值`  
### 例子:  
```SQL
SET @a = 5
SET @b = 'abc'
```  
## 3. 变量输出  
   `PRINT @变量名`  
### 例子：  
```SQL
PRINT @a
```
# 注释  
   单行注释 `-- xxxx`  
   多行注释 `/*  xxxx  */`

# LEN(·) 函数
   返回字符串的字符数  
### 例子：  
 `LEN('abc123你好!') = 9`  
 `LEN('') = 0`

# DATALENGTH(·) 函数
   返回变量的字节数
### 例子：
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
### 格式：
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
### 例子：  
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
### 格式：
   ```SQL
   FILEGROUP 文件组名称 <filespec> [ ,...n ]
   ```
### 例子：  
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
### 格式：
```SQL
[ LOG ON { < filespec > [ ,...n ] } ]
```  
### 例子：  
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

## 4. 完整例子：
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
### 格式：
```SQL
ADD FILE <filespec> [ ,...n ]  --添加数据文件
      [ TO FILEGROUP { filegroup_name } ] --可选的加入文件组
| ADD LOG FILE <filespec> [ ,...n ] --添加日志文件
| REMOVE FILE logical_file_name  --删除文件 
| MODIFY FILE <filespec> --修改文件
```
### 例子：
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
### 格式：
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
### 例子:
```SQL
ADD FILEGROUP Group3
MODIFY FILEGROUP Group3 READONLY
MODIFY FILEGROUP Group3 NAME = Group666
```  

## 完整例子：
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

## 语法：
```SQL
DROP DATABASE { 数据库名称 | 数据库快照名称 } [,...n ] 
```

## 完整例子：

```SQL
DROP DATABASE MyDatabase;
```
# 分离数据库

## 语法：
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

## 语法：
```SQL
CREATE DATABASE 数据库名称
ON
(
FILENAME = '主数据文件物理路径'
)
FOR ATTACH
```

## 完整例子：
```SQL
CREATE DATABASE MyDatabase1
ON
(
   FILENAME = 'C:\\MyDatabase1.mdf'
)
FOR ATTACH;
```

# 创建表

## 语法：
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
### 格式：
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
### 例子：
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

## 完整例子：
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

# 修改表

## 语法：
```SQL
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
}
```

## 完整例子：
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

-- 为表增加CHECK属性
ALTER TABLE MyClass
WITH CHECK;

-- 增加列Score，总长10，小数精度2的DECIMAL
ALTER TABLE MyClass
ADD Score DECIMAL(10,2) NOT NULL;

-- 增加列约束
ALTER TABLE MyClass
ADD CONSTRAINT ConsScoreCheck CHECK (Score >= 0 AND Score <= 150);

-- 删除列
ALTER TABLE MyClass
DROP COLUMN Score;
```

# 删除表

## 语法：
```SQL
DROP TABLE [ 数据库名 . [ 架构名 ] . | 架构名 . ]
      表名 [ ,...n ]
;
```

## 完整例子：
```SQL
DROP TABLE MyDatabase1.dbo.MyClass;
```
