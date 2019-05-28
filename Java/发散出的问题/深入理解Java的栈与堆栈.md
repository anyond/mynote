# 深入理解Java的栈与堆栈
1. 栈（stack）和堆（heap）都是java用来在ram中存放数据的地方，不同于C/C++，java自动管理栈和堆，程序员不能直接设置。
2. 栈存取快，仅此于==寄存器==，数据的大小和生存周期是确定的，数据可以共享。
3. 堆，动态分配内存，所以存取相对慢，生存期也不需要告诉编辑器，GC会自动收走不再使用的数据。
4. 寄存器位于CPU内部，数量有限，不能进行控制，甚至不能感知到他的存在。
5. 基本类型int,short,long,byte,float,double,boolean,char存在栈中。
6. 包装类数据Integer,Short,Long,Byte,Float,Double,Boolean,Character，java对象存在堆中。
7. java的