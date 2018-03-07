###原型链类

####创建对象有几种方法


* 对象字面量创建对象(通过new Object声明一个对象)

    * var o1={name:'o1'};
    * var o11=new Object({name:'o11'});
    
    
    
* 使用构造函数创建对象  

    * var M=function(){this.name='o2'};
    * var o2=new M();
      
      
* Object.creat()创建对象   
 
    * var P={name:'o3'};
    * var o3=Object.creat(P);

####原型、构造函数、实例、原型链

![](/assets/QQ截图20180307112217.png)

![](/assets/20171028122825495.png)


####instanceof的原理
![](/assets/QQ截图20180307150215.png)

![](/assets/20171028124228441.png)


####new运算符

* 一个对象被创建,它继承自foo.prototype
    
* 构造函数foo被执行.执行的时候,相应的传参会被传入,同时上下文(this)会被指定为这个新实例.new foo等同于new foo(),只能用在不传递任何参数的情况
    
* 如果构造函数返回了一个“对象”,那么这个对象会取代整个new出来的结果.如果构造函数没有返回对象,那么new出来的结果为步骤1创建的对象
    
    
####new运算符背后的工作原理(模拟new过程)

```js

    var new2=function(func){ 

    var o=Object.create(func.prototype); 
    
    var k=func.call(o); 

    if(typeof k===’object’){

        return k; 

    }else{

        return o; 

    }
```
原理:
    * 创建空对象,空对象要关联构造函数的原型对象
    * 执行构造函数
    * 判断构造函数的运行结果是不是对象类型
    
    
    