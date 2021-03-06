# 深入理解Java的栈与堆栈
1. 栈（stack）和堆（heap）都是java用来在ram中存放数据的地方，不同于C/C++，java自动管理栈和堆，程序员不能直接设置。
2. 栈存取快，仅此于==寄存器==，数据的大小和生存周期是确定的，数据可以共享。
3. 堆，动态分配内存，所以存取相对慢，生存期也不需要告诉编辑器，GC会自动收走不再使用的数据。
4. 寄存器位于CPU内部，数量有限，不能进行控制，甚至不能感知到他的存在。
5. 基本类型int,short,long,byte,float,double,boolean,char存在栈中。
6. 包装类数据Integer,Short,Long,Byte,Float,Double,Boolean,Character，java对象存在堆中。
7. java的对象引用存在栈中，对象存在堆中。
8. 静态存储，对象中的static元素。
9. 常量存储，常量存储在程序代码内部。嵌入式有时可以放在ROM中。
10. 非Ram存储，程序之外，不运行也存在（文件？）
11.  引用变量就相当于是为数组或对象起的一个名称，以后就可以在程序中使用栈中的引用变量来访问堆中的数组或对象。
12. String是一个特殊的包装类数据。可以用：  
```
String str = new String("abc");  
String str = "abc"; 
```
两种的形式来创建，第一种是用new()来新建对象的，它会在存放于堆中。每调用一次就会创建一个新的对象。  
而第二种是先在栈中创建一个对String类的对象引用变量str，然后查找栈中有没有存放"abc"，如果没有，则将"abc"存放进栈，并令str指向”abc”，如果已经有”abc” 则直接令str指向“abc”。  
比较类里面的数值是否相等时，用equals()方法；当测试两个包装类的引用是否指向同一个对象时，用==

## 缓冲机制
1. JDK API文档中对这个新的valueOf方法有明确的解释： 
如果不需要新的 Integer 实例，则通常应优先使用该方法，而不是构造方法 Integer(int)，因为该方法有可能通过缓存经常请求的值而显著提高空间和时间性能 
查看Integer的valueOf方法的：
```
    public static Integer valueOf(int i) {
        assert IntegerCache.high >= 127;
        //static final int low = -128;
        //当-128=<i<=127的时候，就直接在缓存中取出 i de  Integer 类型对象
        if (i >= IntegerCache.low && i <= IntegerCache.high)
            return IntegerCache.cache[i + (-IntegerCache.low)];
        //否则就在堆内存中创建
        return new Integer(i);
    }
```
看出对于范围 [-128,127] 的整数，valueOf 方法做了特殊处理。采用IntegerCache.cache[i + (-IntegerCache.low)]; 这个方法
2.其他的包装器: 	
Boolean： (全部缓存) 
Byte： (全部缓存)

Character ( <=127 缓存) 
Short (-128~127 缓存) 
Long (-128~127 缓存)

Float (没有缓存) 
Doulbe (没有缓存)