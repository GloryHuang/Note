###ES6函数参数

####函数参数默认值

```js
    //函数参数默认值
    //默认值后面不能跟没有默认值的变量
    {
        function test(x, y = 'world') {
            console.log('默认值', x, y);
        }
        test('hello');
        test('hello', 'kill');
    }



    {
        let x = 'test';

        function test2(x, y = x) {
            console.log('作用域', x, y);
        }
        test2('kill'); //上面的x取得是这里的x
    }

```

####....rest参数

```js
    //....rest参数
    //将输入的参数(离散的值)转换成数组
    //不会有arguments的第一个参数的问题
    //后面不能有其他参数
    {
        function test3(...arg) {
            for (let v of arg) {
                console.log('rest', v);
            }
        }
        test3(1, 2, 3, 4, 'a');
    }
```

####扩展运算符

```js
    //扩展运算符
    //把数组装换成离散的值
    {
        console.log(...[1, 2, 4]);
        console.log('a', ...[1, 2, 4]);
    }
    
```


####箭头函数
```js

    //箭头函数
    {
        let arrow = v => v * 2;

        let arrow2 = () => 5;

        console.log(arrow(3));
        console.log(arrow2());
    }
```

####伪调用
```js
    //伪调用
    //函数的最后一句话是不是函数
    //提升性能
    {
	    function tail (x) {
    	    	console.log('tail',x);
	    }

	    function fx (x) {
	    	return tail(x);
	    }

	    fx(123);
    }
```