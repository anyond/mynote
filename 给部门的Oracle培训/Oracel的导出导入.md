1. exp/imp导出导入

其中expdp/impdp比exp/imp多了用户及其权限
2. expdp/impdp导出导入
一、新建逻辑目录
最好以system等管理员创建逻辑目录，Oracle不会自动创建实际的物理目录“D:\oracleData”（务必手动创建此目录），仅仅是进行定义逻辑路径dump_dir；
     sql> conn system/123456a?@orcl as sysdba;
     sql>create directory dump_dir as 'D:\oracleData';
二、查看管理员目录（同时查看操作系统是否存在该目录，因为oracle并不关心该目录是否存在，假如不存在，则出错）
     sql>select * from dba_directories;
三、用expdp导出数据
1)导出用户及其对象
expdp scott/tiger@orcl schemas=scott dumpfile=expdp.dmp directory=dump_dir;
2)导出指定表
expdp scott/tiger@orcl tables=emp,dept dumpfile=expdp.dmp directory=dump_dir;
3)按查询条件导
expdp scott/tiger@orcl directory=dump_dir dumpfile=expdp.dmp tables=empquery='where deptno=20';
4)按表空间导
expdp system/manager@orcl directory=dump_dir dumpfile=tablespace.dmp tablespaces=temp,example;
5)导整个数据库
expdp system/manager@orcl directory=dump_dir dumpfile=full.dmp full=y;
四、用impdp导入数据
在正式导入数据前，要先确保要导入的用户已存在，如果没有存在，请先用下述命令进行新建用户
--创建表空间
create tablespace tb_name datafile 'D:\tablespace\tb_name.dbf' size 1024m AUTOEXTEND ON;
--创建用户
create user user_name identified by A123456a default tablespace tb_name temporary tablespace TEMP;
--给用户授权
其实问题的核心不在于dba权限，而在于 EXP_FULL_DATABASE / IMP_FULL_DATABASE 角色。
sql>grant read,write on directory dump_dir to user_name;
sql>grant dba,resource,unlimited tablespace to user_name;
1)导入用户（从用户scott导入到用户scott）
impdp scott/tiger@orcl directory=dump_dir dumpfile=expdp.dmp schemas=scott;
2)导入表（从scott用户中把表dept和emp导入到system用户中）
impdp system/manager@orcl directory=dump_dir dumpfile=expdp.dmptables=scott.dept,scott.emp remap_schema=scott:system;
3)导入表空间
impdp system/manager@orcl directory=dump_dir dumpfile=tablespace.dmp tablespaces=example;
4)导入数据库
impdb system/manager@orcl directory=dump_dir dumpfile=full.dmp full=y;
5)追加数据
impdp system/manager@orcl directory=dump_dir dumpfile=expdp.dmp schemas=systemtable_exists_action
3. sql导出导入
4. 文本导出导入