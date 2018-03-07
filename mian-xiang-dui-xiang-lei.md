###面向对象类


####类与实例

* 类的声明

 * 在ES5中声明
```js
     function Animal(){
        this.name='name';
     }
 ```   
 
 * 在ES6中声明
    
```js
      class Animal2{
           construtor(){
                this.name=name;
           }
      }
 
``` 
    
* 生成实例(实例化)

```js
     console.log(new Animal(),new Animal2());
```
####类与继承

#### 如何实现继承

     * 借助构造函数实现继承
          * 缺点：实现了部分继承,如果说父类上的属性都在构造函数里面,可以实现继承,但是如果父类的原型对象上还有方法,子类是拿不到这些方法的
     
```js
     function Parent1(){
          this.name='parent1';
     }
     
     
     Parent1.prototype.say=function(){};//缺点:child1没有继承Parent1原型对象的方法
     
     //将父级的构造函数的this,指向子构造函数的实例上去,导致父级构造函数的属性在子构造函数里都有
     function Child1(){
          Parent1.call(this);//apply(改变函数运行的上下文)
          this.type='child1';
     }
     
     console.log(new Child1(),new Child1().say());


```
![](/assets/QQ图片20180307161349.png)


     * 借助原型链实现继承
     
         * 缺点:一个实例改变另一个实例也会跟着改变
     
     
```js

     function Parent2(){
          this.name='parent2';
          this.play=[1,2,3];
     }
     
     function Child2(){
          this.type='child2';
     }
     
     Child2.prototype=new Parent2();
     
     console.log(new Child2());
     
     var s1=new Child1();
     var s2=new Child2();
     console.log(s1.play,s2.play);
     s1.play.push(4);//缺点：s1改变，s2也会跟着改变(原型链上的原型对象是共用的)
     
```
![](/assets/20171028132954306.png)
![](/assets/20171028133711941.png)



* 继承的几种方式   
    