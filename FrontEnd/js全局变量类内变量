     在js中使用var关键字定义的变量是局部变量，不带var关键字则是全局变量。例如：
           function fn1(){
                _test = "Hello, World";
           }
           
          function fn2(){
               fn1();
               console.log( _test );
            }
         
            调用fn2()正常显示，能够打印出_test的值，如果将fn1() 改成 function fn1(){  var  _test = "Hello, World"  } , 那么在fn2() 中调用的时候会异常，因为没有找到 _test 变量。 那么说明 带 var关键字的是局部变量，不带var关键字则是全局变量。