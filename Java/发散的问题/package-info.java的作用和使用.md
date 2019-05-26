# package-info.java的作用
1. 为标注在包上Annotation提供便利

2. 声明友好类和包常量
比如一个包中有很多的内部访问的类或常量，就可以统一的放到package-info类中，这样就方便，而且集中管理，减少friendly类到处游走的情况（文中原话）
   ```
   ```
//这里是包类，声明一个包使用的公共类，强调的是包访问权限
class PkgClass{
    public void test(){
    }
}
//包常量，只运行包内访问，适用于分“包”开发
class PkgConst{
    static final String PACAKGE_CONST="ABC";
}
```
需要注意的是Java中并没有Friendly类,只有Default（本包访问）。
3. 提供包的整体注释说明
为包加整体注释说明
![image.png](0)