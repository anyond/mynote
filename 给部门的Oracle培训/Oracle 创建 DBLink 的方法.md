当用户要跨本地数据库，访问另外一个数据库表中的数据时，本地数据库中必须创建了远程数据库的dblink,通过dblink本地数据库可以像访问本地数据库一样访问远程数据库表中的数据。
```
create database link TestDblink
 connect to dbName identified by dbPassword
  using '(DESCRIPTION =(ADDRESS_LIST =(ADDRESS =(PROTOCOL = TCP)(HOST = 192.168.2.158)(PORT = 1521)))(CONNECT_DATA =(SERVICE_NAME = orcl)))';
```
 
TestDblink ： 表示dblink名字
dbName ：表示 远程数据库的用户
dbPassword：表示 远程数据库的密码
HOST ： 表示远程数据库IP
PORT ： 表示远程数据库端口
SERVICE_NAME ： 远程数据库的实例名

-- 查询、删除和插入数据和操作本地的数据库是一样的，只不过表名需要写成“表名@dblink服务器”而已。 

select * from db.tb_test@TestDblink;