# Java 初始化顺序
这篇笔记简单的说一下java类在被加载的时候，初始化的顺序
这里先先写两个使用到的类, 基类 BaseClass 和子类 SubClass 
```
public class BaseClass{
    public static int param = init(); // (1)

    // 静态代码块
    static{ // (2)
        System.out.println("static code"); 
    }

    private static int init(){
        System.out.println("init");
        return 0;
    }

    public BaseClass(){ // (3)
        System.out.println("constructor");
    }

}

public class SubClass{
    public static int param = init(); // (1)

    // 静态代码块
    static{ // (2)
        System.out.println("static code ----->!"); 
    }

    private static int init(){
        System.out.println("init ----->!");
        return 0;
    }

    public BaseClass(){ // (3)
        System.out.println("constructor ----->!");
    }

    public static void main(String []args){
        new SubClass(); // (4)
        new BaseClass(); // (5)
    }
}
```

如果注释掉 （4），只执行（5）
*结果*
>init
>static code
>constructor

如果注释掉 （5），只执行 （4）
*结果*
>init
>static code
>init ----->!
>static code ----->!
>constructor
>constructor ----->!

结果很明显了

- 如果类没有继承机制，那么，类会先执行静态常量的加载，然后再执行构造器。而且静态常量和静态块的加载顺序和他们的位置有关系。谁在前先加载谁。而静态常量和构造器顺序无关，总是先加载静态常量。
- 如果类中存在继承机制，那么先加载基类的静态常量和静态块，然后再加载子类中的静态常量和静态块。然后才是基类的构造函数和子类的构造函数。



