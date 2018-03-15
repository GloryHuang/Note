####ES6

###构建ES6的开发环境


#####构建工具

+ gulp(任务自动化)
- babel(编译工具)
* webpack(编译工具)
- npm





#####ES6强制开启严格模式

'use strict'

    严格模式的注意点:
        变量未声明不能引用,否则会报引用错误



##let 

    1.在块作用域声明的let变量只在当前声明的块作用域内有效。
    2.使用let变量不能重复定义变量
    
    
##const

    1.使用const声明的常量是不能修改的,但是在引用类型内,返回的是存储的指针,指针不变,但是对象本身是可以变得。
    2.const和let在块作用域使用的方法是相同的。
    3.const声明的时候必须赋值。



##解构赋值
   
    声明没有赋值,没有配对成功返回undefind.
    
    
```js
    {
        let a, b, rest;
        [a, b] = [1, 2];
        console.log(a, b)
        //1,2
    }
    
    //数组解构赋值
    {
        let a, b, rest;
        [a, b, ...rest] = [1, 2, 3, 4, 5, 6];
        console.log(a, b, rest);
        //1,2,[3,4,5,6]
    }



    //对象解构赋值
    {
        let a, b;
        ({ a, b } = { a: 1, b: 2 })
        console.log(a, b);
        //1,2
    }



    //声明赋值
    {
        let a, b, c, rest;
        [a, b, c = 3] = [1, 2];
        console.log(a, b, c);
        //1,2,3
    }


    {
        let a = 1;
        let b = 2;
        [a, b] = [b, a];
        console.log(a, b);
        //2,1
    }


    {
        function fc() {
            return [5, 6];
        }
        let a, b;
        [a, b] = fc();
        console.log(a, b);
        //5,6
    }


    {
        function f() {
            return [1, 2, 3, 4, 5]
        }
        let a, b, c;
        [a, , , b] = f();
        console.log(a, b);
        //1,4
    }



    //不知道返回数组的长度
    {
        function f() {
            return [1, 2, 3, 4, 5]
        }
        let a, b, c;
        [a,... b] = f();
        console.log(a, b);
        //1,[2,3,4,5]
    }

    //还可以混合使用
    {
        function f() {
            return [1, 2, 3, 4, 5]
        }
        let a, b, c;
        [a,,... b] = f();
        console.log(a, b);
        //1,[3,4,5]
    }

    {
	let o={p:24,q:true};
	let {p,q}=o;
	console.log(p,q);
        //24,true
    }

    {
	let {a=10,b=5}={a:3};
	console.log(a,b);
        //3,5
    }


    {
	let metaData={
		title:'abc',
		test:[{
			title:'test',
			desec:'description'
		}]
	}
	let {title:esTitle,test:[{title:cnTitle}]}=metaData;
	console.log(esTitle,cnTitle);
    }
    
    
    
```


##正则扩展
```js
    新增y,u修饰符
    
    let regex = new RegExp('xyz', 'i');
    let regex2 = new RegExp(/xyz/i);


    console.log(regex.test('xyz123'), regex2.test('xyz123'));

    let regex3 = new RegExp(/xyz/ig, 'i');


    console.log(regex3.flags);
    输出i
    
    ES6中以此方式生成构造函数,在ES6允许第一个参数以正则表达式的形式,第二个参数的修饰符会覆盖第一个参数表达式的修饰符
    
    
    flags  获取正则对象的修饰符  igm
    sticky 查看是否开启粘黏模式  开启了 true
   ``` 
    
####y修饰符

    g和y修饰符：
    
        相同点：
        
             都是全局匹配
             
        不同点:
             g修饰符是从上一次匹配的位置开始继续找
             y匹配的字符必须是紧跟的第一个才算匹配成功
             
####u修饰符(Unicode的缩写)

* 如果表达式里放的是Unicode编码想要被识别就必须要用修饰符u

* 如果字符串中有的字符是大于2个字节的一定要加上u修饰符,否则无法正确处理。
    
    
    .匹配小于2个字节长度的字符
    
     //a的Unicode编码是\u61
    //根据Unicode编码进行正则匹配
    console.log(/\u{61}/.test('a')); //返回 false
    console.log(/\u{61}/u.test('a')); //返回 true
    


    