# java *Thread* implements
java中创建线程，一般使用两种方式：
####一、继承Thread类
此方法必须要复写父类Thread中的**run**方法
```
public class MyThread extends Thread{
	@Override
	public void run(){
		//TO DO SOMETHING HERE
	}	
}
```
####二、实现Runnable接口
此方法必须实现Runnable中的**run** 方法
```
public class MyThread implements Runnable{
	public void run(){
		//TO DO SOMETHING HERE
	}
}
```
##方法线程类的创建方式
####第一种方法的线程类创建方式
```
public class Run{
	public static void main(String args[]){
		MyThread mt = new MyThread();
		mt.start(); // 系统自动运行和调度线程
	}
}
```
####第二种方法的线程类的调用方式
```
public class Run{
	public static void main(String args[]){
		MyThread mt = new MyThread();
		Thread thread = new Thread(mt);
		thread.start();
	}
}
```