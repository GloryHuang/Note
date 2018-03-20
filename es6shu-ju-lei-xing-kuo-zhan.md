###ES6数据类型扩展

####ES6新增数据类型


* Symbol

    Symbol它就是提供一个独一无二的值
    Symbol声明的值不重复,不相等(保证是唯一的独一无二的)

####Symbol

```js
    {
        //声明

        //声明方式1
        let a1 = Symbol();
        let a2 = Symbol();

        //永远是独一无二的
        console.log(a1 === a2); //false
        

        //声明方式2
        let a3 = Symbol.for('a3');
        // for(key值) ,key值如果没有注册过(不存在),就直接生成一个独一无二的值
        //				key值如果注册过(存在),直接调用那个值
        let a4 = Symbol.for('a3');
        console.log(a3 === a4); //true
    }


    //作用
    {
        //不造成冲突
        let a1 = Symbol.for('abc');
        let obj = {
            [a1]: '123',
            'abc': '345',
            'c': '456'
        }
        console.log('obj', obj);
        //obj { abc: '345', c: '456', [Symbol(abc)]: '123' }

        //for in for of遍历取不到Symbol的值
        for (let [key, value] of Object.entries(obj)) {
            console.log('let of ', key, value);
            //let of  abc 345
            //let of  c 456
        }    

        //这个方法得到一个数组
        //使得foreach 可以遍历出symbol的值 只取得symbol的值
        Object.getOwnPropertySymbols(obj).forEach(function(item, index) {
            console.log('getOwnPropertySymbols', item);
            //getOwnPropertySymbols Symbol(abc)
        });


        //返回了symbol和非symbol的值,返回的是一个数组
        Reflect.ownKeys(obj).forEach(function(item, index) {
    	    console.log('ownKeys',index,item);
            //ownKeys 0 abc
            //ownKeys 1 c
            //ownKeys 2 Symbol(abc)
        });


    }
```