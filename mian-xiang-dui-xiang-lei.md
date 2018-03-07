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

* 如何实现继承

     * 借助构造函数实现继承
     
```js
     function Parent1(){
          this.name='parent1';
     }
     
     function Child1(){
          Parent1.call(this);//apply(改变函数运行的上下文)
          this.type='child1';
     }
     
     console.log(new Child1);
```
     


* 继承的几种方式   
    