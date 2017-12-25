# Java类加载器
- #### 类加载器的分类
- ##### BootstrapClassloader
引导类加载器，又称启动类加载器，是最顶层的类加载器，主要用来加载Java核心类，如 `rt.jar` `resources.jar` `charset.jar`  等。
- ##### ExtClassloader
扩展类加载器，主要负责加载Java的扩展类库，默认加载`JAVA_HOME/jre/lib/ext/`目下的所有jar包或者由`java.ext.dirs`系统属性指定的jar包。放入这个目录下的jar包对所有`AppClassloader`都是可见的（后面会知道`ExtClassloader`是`AppClassloader`的父加载器)
- ##### AppClassloader(SystemClassloader)
系统类加载器，又称应用加载器，本文说的`SystemClassloader`和`APPClassloader`是一个东西，它负责在`JVM`启动时，加载来自在命令java中的`-classpath`或者`java.class.path`系统属性或者 CLASSPATH操作系统属性所指定的JAR类包和类路径。调用`ClassLoader.getSystemClassLoader()`可以获取该类加载器。如果没有特别指定，则用户自定义的任何类加载器都将该类加载器作为它的父加载器.
- #### 三种类加载器的联系
Bootstraploader > ExtClassloader > UserClassloader ( `>` 符号代表优先级优先)
用户自定义的无参加载器的父类加载器默认是`AppClassloader`加载器，而`AppClassloader`加载器的父加载器是`ExtClassloader`.
一般我们都认为`ExtClassloader`的父类加载器是`BootStarpClassloader`，但是其实他们之间根本是没有父子关系的，只是在`ExtClassloader`找不到要加载类时候会去委托`BootStrapClassLoader`加载器去加载
- #### 类加载器原理
Java类加载器使用的是`委托`机制，也就是子类加载器在加载一个类时候会让父类来加载，那么问题来了，为啥使用这种方式那?因为这样可以避免重复加载，当父亲已经加载了该类的时候，就没有必要子`ClassLoader`再加载一次。考虑到安全因素，我们试想一下，如果不使用这种委托模式，那我们就可以随时使用自定义的`String`来动态替代java核心api中定义的类型，这样会存在非常大的安全隐患，而`双亲委托`的方式，就可以避免这种情况，因为String已经在启动时就被引导类加载器（`Bootstrcp ClassLoader`）加载，所以用户自定义的`ClassLoader`永远也无法加载一个自己写的String，除非你改变JDK中ClassLoader搜索类的默认算法。
- #### 总结
总结下Java应用启动过程是首先`BootstarpClassloader`加载`rt.jar`包里面的`sun.misc.Launcher`类，而该类内部使用`BootstarpClassloader`加载器构建和初始化Java中三种类加载和线程上下文类加载器，然后在根据不同场景去使用这些类加载器去自己的类查找路径去加载类。
