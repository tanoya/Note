#Java *Interface*
####*注意*
1. 在进行接口定义的时候，接口中可以有字段，**例如** 
```
public interface MyInterface{
	public String name="john"; // 此时name字段，类型相当于 public static final name="john" , 因此属性必须初始化
	public int code=0;	// 同上
}
```
2. 接口中不能有构造函数
3. 实现 **MyInterface** 的子类，不能修改接口中定义的属性的值， *例如*
```
public MyClass implements MyInterface{
	public MyClass(String name, int code){
		<del>this.name = name;</del> // 语法错误，会提示：The final field MyInterface.name cannot be assigned
		<del>this.code = code;</del> // 也就是提示 修改了 constant 变量
	}
}
```