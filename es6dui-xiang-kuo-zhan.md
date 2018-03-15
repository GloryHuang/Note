###ES6对象扩展

 * 简洁表示法
 * 属性表达式
 * 扩展运算符
 * Object新增方法



####简洁表示法
```js
    //简洁表示法
    {

        let o = 1;
        let k = 2;
        let es5 = {
            o: o,
            k: k
        };
        //简洁表示法
        let es6 = {
            o,
            k
        };
        console.log(es5, es6);



        let es5_menthod = {
            hello: function() {
                console.log('Hello');
            }
        }

        let es6_menthod = {
            hello() {
                console.log('Hello');
            }
        };


        console.log(es5_menthod.hello(), es6_menthod.hello());
    }

```


####属性表达式
```js
    //属性表达式
    {

        let a = 'b';
        let es5_obj = {
            a: 'c',
            b: 'c'
        };

        let es6_obj = {
            [a]: 'c'
        }

        console.log(es5_obj, es6_obj);
    }
```


####Object新增API
```js
    //Object新增API
    {
        //is()和===的功能没有区别
        console.log('字符串', Object.is('abc', 'abc'));
        //两个数组引用的是不用的地址
        console.log('数组', Object.is([], [])); //false

        //拷贝的功能
        //拷贝的属性是有限制的,浅拷贝(修改地址不是改变值)
        //不会拷贝继承、不可枚举的属性
        console.log('拷贝', Object.assign({ a: 'a' }, { b: 'b' }));

        let test = { k: 123, o: 456 };
        for (let [key, value] of Object.entries(test)) {
            console.log([key, value]);
        }
    }

```

####扩展运算符

```js
    //扩展运算符
    //无法识别babel支持不友好
    // {
    	    // let {a,b,...c}={a:'test',b:'kill',c:'ddd',d:'ccc'};

	    //解析后
	    // c={
		// c:'ddd',
		// d:'ccc'
		// ....
	    // }
    // }
```