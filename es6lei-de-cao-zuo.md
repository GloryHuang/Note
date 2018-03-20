###ES6类操作

####类(Class)

 * 类的基本概念
 * 基本语法
 * 类的继承
 * 静态方法
 * 静态属性
 * getter
 * setter


    //constructor 构造函数
    //相当于functor(){}



####基本定义和生成实例

```js
//基本定义和生成实例
{

    class Parent {
        constructor(name = 'mukewang') {
            this.name = name;
        }
    }
    let v_parent = new Parent('小明');

    console.log('构造函数和实例', v_parent);
    //构造函数和实例 Parent { name: '小明' }
}

```

```js
//继承
{
    //继承传递参数
    class Parent {
        constructor(name = 'mukewang') {
            this.name = name;
        }
    }


    //子类覆盖父类默认的值
    //super()
    //super的参数列表就是父类Parent中 constructor中的参数列表
    //super()在子类中没有传值,父类的所有都会使用父类中默认的值
    class Child extends Parent {
        constructor(name = 'child') {
            super(name);
            //给子类添加属性或者方法
            this.type = 'child';
        }
    }

    //注意点:
    //1.在继承关系中子类的构造函数如果用super传递传参数的过程中
    //super一定是放在构造函数的第一行


    console.log('继承', new Child());
    //继承 Child { name: 'child', type: 'child' }
    
    console.log('继承', new Child('hello'));
    //继承 Child { name: 'hello', type: 'child' }
}

```


```js
//getter,setter
{
    class Parent {
        constructor(name = 'mukewang') {
            this.name = name;
        }

        //属性
        get longName() {
            return 'mk ' + this.name;
        }

        set longName(value) {
            this.name = value;
        }
    }


    let v = new Parent();
    console.log('getter', v.longName);
    //getter mk mukewang
    
    //setter操作
    //赋值就相当于是setter操作
    v.longName = 'hello';
    console.log('setter', v.longName);
    //setter mk hello
}

```
####静态方法
```js
//静态方法
{
    class Parent {
        constructor(name = 'wukewang') {
            this.name = name;
        }

        //静态方法
        //是通过类去调用,而不是通过类的实例去调用
        static tell() {
            console.log('tell');
        }
    }

    Parent.tell();
    //tell

}
```

####静态属性
```js
//静态属性
{
    class Parent {
        constructor(name = 'wukewang') {
            this.name = name;
        }
        static tell() {
            console.log('tell');
        }
    }


    Parent.type = 'test';
    console.log('静态属性', Parent.type);
    //静态属性 test
}
```