# ThreadLocal
程序运行过程中，有一些变量是要线程本身持有的，不可共享的，这在多线程编程中很重要，这就像是在多线程程序中的`private`关键字作用，自己持有的 ThreadLocal 变量对其他的线程是不可见的。

#### 实现方式
Thread 类中有 ThreadLocalMap 变量。
```
	class Thread{
		ThreadLocal.ThreadLocalMap threadLocals = null;
	}
```

ThreadLocal 在我们自定义的类中
```
class ThreadLocal<T>{
	T get(){
		Thread t = Thread.currentThread();
		ThreadLocalMap map = getMap(t);
		if(map != null){
			ThreadLocalMap.Entry e = map.getEntry(this);
			...
		}
	}
}
```
代码中可以看的出来线程是持有了自己所独有的变量，利于变量的私有化,在多线程中不能被其他线程访问到