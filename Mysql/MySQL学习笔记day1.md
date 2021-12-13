# MySQL学习笔记day1

## 什么是数据库？

**数据库**，又称为数据管理系统，简而言之可视为[电子化](https://zh.wikipedia.org/w/index.php?title=電子化&action=edit&redlink=1)的[文件柜](https://zh.wikipedia.org/wiki/档案柜)——存储电子[文件](https://zh.wikipedia.org/wiki/檔案)的处所，用户可以对[文件](https://zh.wikipedia.org/wiki/檔案)中的资料执行新增、截取、更新、删除等操作[[1\]](https://zh.wikipedia.org/wiki/数据库#cite_note-1)。

所谓“数据库”是以**一定方式**储存在一起、能予多个用户[共享](https://zh.wikipedia.org/wiki/共享)、具有尽可能小的[冗余度](https://zh.wikipedia.org/wiki/数据冗余)、与应用程序彼此独立的数据[集合](https://zh.wikipedia.org/wiki/集合_(计算机科学))。一个数据库由多个表空间（[Tablespace](https://zh.wikipedia.org/wiki/Tablespace)）构成。

## 什么是数据库管理系统？

**数据库管理系统**（英语：**database management system**，[缩写](https://zh.wikipedia.org/wiki/缩写)：**DBMS**） 是一种针对[对象数据库](https://zh.wikipedia.org/wiki/对象数据库)，为管理[数据库](https://zh.wikipedia.org/wiki/数据库)而设计的大型电脑[软件](https://zh.wikipedia.org/wiki/软件)管理系统。具有代表性的数据管理系统有：[Oracle](https://zh.wikipedia.org/wiki/Oracle)、[Microsoft SQL Server](https://zh.wikipedia.org/wiki/Microsoft_SQL_Server)、[Access](https://zh.wikipedia.org/wiki/Access)、[MySQL](https://zh.wikipedia.org/wiki/MySQL)及[PostgreSQL](https://zh.wikipedia.org/wiki/PostgreSQL)等。通常数据库管理师会使用数据库管理系统来创建数据库系统。

现代DBMS使用不同的数据库模型追踪实体、属性和关系。在个人电脑、大型计算机和主机上应用最广泛的数据库管理系统是关系型DBMS（relational DBMS）。在[关系型数据库](https://zh.wikipedia.org/wiki/关系型数据库)中，用二维表格表示数据库中的数据。这些表格称为关系[[1\]](https://zh.wikipedia.org/wiki/数据库管理系统#cite_note-1)。

## 什么是SQL\结构化查询语言？
**SQL**（[![聆听](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/Speakerlink-new.svg/11px-Speakerlink-new.svg.png)](https://upload.wikimedia.org/wikipedia/commons/5/5f/En-us-SQL.ogg)**[i](https://zh.wikipedia.org/wiki/File:En-us-SQL.ogg)**[/ˈɛs kjuː ˈɛl/](https://zh.wikipedia.org/wiki/Help:英語國際音標)[[4\]](https://zh.wikipedia.org/wiki/SQL#cite_note-learningSQL-4)或[![聆听](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/Speakerlink-new.svg/11px-Speakerlink-new.svg.png)](https://upload.wikimedia.org/wikipedia/commons/7/7a/En-us-sequel.ogg)**[i](https://zh.wikipedia.org/wiki/File:En-us-sequel.ogg)**[/ˈsiːkwəl/](https://zh.wikipedia.org/wiki/Help:英語國際音標)[[5\]](https://zh.wikipedia.org/wiki/SQL#cite_note-5)，**Structured Query Language:结构化查询语言**[[6\]](https://zh.wikipedia.org/wiki/SQL#cite_note-6)[[7\]](https://zh.wikipedia.org/wiki/SQL#cite_note-7)[[8\]](https://zh.wikipedia.org/wiki/SQL#cite_note-8)[[9\]](https://zh.wikipedia.org/wiki/SQL#cite_note-9)）是一种[特定目的编程语言](https://zh.wikipedia.org/wiki/特定目的程式语言)，用于管理[关系数据库管理系统](https://zh.wikipedia.org/wiki/关系数据库管理系统)（RDBMS），或在[关系流数据管理系统](https://zh.wikipedia.org/wiki/关系流数据管理系统)（RDSMS）中进行流处理。



## sql语句分类

SQL语句可以分为以下四类：`数据操作语言(DML)`、`数据定义语言(DDL)`、`数据控制语言(DCL)`、`事务控制语言(TCL)`。

- 数据操作语言(DML：Data Manipulation Language)

  由数据库管理系统(DBMS) 提供，用于让用户或程序员使用，实现对数据库中数据的操作。 主要包含 `SELECT`、 `INSERT`、 `UPDATE`、 `DELETE`、 `MERGE`、 `CALL`、 `EXPLAIN PLAN`、 `LOCK TABLE`等语句。

- 数据定义语言(DDL：Data Definition Language)

  用于定义SQL模式、基本表、视图和索引的创建和撤消操作。 主要包含 `CREATE`、 `ALTER`、 `DROP`、 `TRUNCATE`、 `COMMENT`、 `REPLACE`(RENAME)等语句，一般不需要commit等事务操作。

- 数据控制语言(DCL：Data Control Language)

  用于数据库授权、角色控制等管理工作。 主要包含 `GRANT`、 `REVOKE`等语句。

- 事务控制语言(TCL：Transaction Control Language)

  用于数据库的事务管理。 主要包含 `SAVEPOINT`、 `ROLLBACK`、 `COMMIT`、 `SET TRANSACTION`等语句。

以上信息主要参考Oracle官方文档，和某些站点上的定义可能略有不同。 例如：在某些站点的介绍中，SELECT并不属于DDL，而是将其归为一个特别的语言类——数据查询语言(DQL：Data Query Language)。 想要了解Oracle SQL语句分类的更多信息，你可以参考Oracle官方文档http://docs.oracle.com/cd/B12037_01/server.101/b10759/statements_1001.htm
