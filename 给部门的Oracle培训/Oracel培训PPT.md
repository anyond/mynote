# Oracle内置函数
|序号|函数|作用|用法演示|
|-|-|-|-|
|content1|content2|content3|

--- 
# Oracle 基本使用
DQL语句
 DML（Data Manipulation Language，数据操作语言）：用于检索或者修改数据。
    DML包括：  SELECT：用于检索数据；
        INSERT：用于增加数据到数据库；
        UPDATE：用于从数据库中修改现存的数据 
        DELETE：用于从数据库中删除数据。

需要commit

查询，左连接，右链接

DDL（Data Definition Language，数据定义语言）： 用于定义数据的结构，比如 创建、修改或者删除数据库对象。
    DDL包括：DDL语句可以用于创建用户和重建数据库对象。下面是DDL命令：
        CREATE TABLE：创建表
        ALTER TABLE
        DROP TABLE：删除表
        CREATE INDEX
        DROP INDEX
DCL（Data Control Language，数据控制语言）：用于定义数据库用户的权限。
    DCL包括：
        ALTER PASSWORD 
        GRANT 
        REVOKE 
        CREATE SYNONYM
插入
正常插入
字段不一致的表如何插入

更新

删除

DML指令
创建表
授权
DBA权限

drop trunc create

DCL

DBLINK

---
# Oracle查询优化
索引
解释计划
使用索引
其他注意的点
程序编写要尽量减少数据库访问次数

AWR报告

---
Oracle 导入 导出 
特殊符号的密码 ''' ''''
---
plsql的使用
保存密码，快捷输入
---
# 存储过程
试用场景

---
# Oracle的配置文件
---
# 常见问题
锁表如何处理
跨服务器如何连接qlsql或者其他的工具?是不是必须在应用服务器安装Oracle客户端呢?
在Oracle中,监听到底是起到什么作用?
listener.ora和tnsnames.ora怎么配置,除了这两个文件,还有没有其他涉及配置监听的底层文件呢?
经常用的连接数据库的工具,如plsql,toad等等,对于初级学者,建议哪款较合适?

新建的数据库隔段时间有时候，就登录不了了

---
# 练习
