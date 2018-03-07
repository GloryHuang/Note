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


####instanceof的原理
![](/assets/QQ截图20180307150215.png)


####new运算符


