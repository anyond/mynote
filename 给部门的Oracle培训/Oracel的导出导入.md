1. exp/imp导出导入

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
expdp system/manager@orcl directory=dump_dir dumpfile=tablespace.dmptablespaces=temp,example;
5)导整个数据库
expdp system/manager@orcl directory=dump_dir dumpfile=full.dmp full=y;
3. sql导出导入
4. 文本导出导入