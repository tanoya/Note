# !Play framework 中request 和 transaction的关系
在 `!Play framework` 中, 服务器接收到一个request, 就相当于开启了一个事务. 在处理request的时候, 虽然会出现 `Model.save();` 语句,但是在整个request处理结束**之前**,也就是在 **事务提交** *之前* `transaction.commit();`, 数据库的内容是不会变化的。这样的情形在多线程并发的情况下，对于数据的控制**不是** 很美好。
#### *例如：*
```
/**
*这是请求处理函数
*/
public static void action(){ 
	handle(args ...); //这是数据处理函数
}

/**
*这是数据处理函数
*/ 
public static sychronized void handle(args ...){ //使用同步
	//TO DO SOMETHING HERE
	//HANDLE DATA
	Order order = Order.getOrderByOrderNo(cOrderNo, iCorpId); //其中 order.cStatusCode="SOMECODE"
	
	if("SOMECODE".equals(order.cStatusCode)){
		order.cStatusCode = "ANOTHERCODE";
		order.save();
	}
} 

/**
*这是另一个处理函数
*/
pbulic static void anotherHandle(args ...){
	//TO DO SOMETHING HERE
	//HANDLE DATA
}

```
现在有两个线程分别去执行 `action()` 方法, 虽然在 `handle()` 方法中使用了synchronized 关键字，但是并没有达到互斥的效果，两者两者都会进入代码块
```
if("SOMECODE".equals(order.cStatusCode)){
	order.cStatusCode = "ANOTHERCODE";
	order.save();
}
```
**注意** 
这是因为，线程1在执行 `Order order = Order.getOrderByOrderNo(cOrderNo, iCorpId);` 的时候，拿到的数据 `order.cStatusCode="SOMECODE"` 可以进入代码块。虽然执行了` order.save();`, 但是现在线程1的请求没有执行完毕，所以并没有提交该事务，数据库中的数据就没有修改(<font color="LightSkyBlue">跟数据库的事务级别有关系</font>)。因此，线程2此时正好也执行到了 `handle()` 互斥代码块，在执行Order数据库查询的时候，查询出来的数据仍然是 `order.cStatusCode="SOMECODE"`, 因此也会去执行代码块中的代码。
##结论
在!Play中,这种情况使用<font color="red">synchronized</font>关键字无法实现线程互斥控制。 