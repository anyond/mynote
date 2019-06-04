1. exp/imp导出导入

2. expdp/impdp导出导入
一、新建逻辑目录
最好以system等管理员创建逻辑目录，Oracle不会自动创建实际的物理目录“D:\oracleData”（务必手动创建此目录），仅仅是进行定义逻辑路径dump_dir；
     sql> conn system/123456a?@orcl as sysdba;
     sql>create directory dump_dir as 'D:\oracleData';

3. sql导出导入
4. 文本导出导入