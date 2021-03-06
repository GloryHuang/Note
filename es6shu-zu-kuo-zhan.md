###ES6数组扩展


####Array.of
```js
    //Array.of方法用于将一组值，转换为数组。Array.of总是返回参数值组成的数组。如果没有参数，就返回一个空数组。
     {
        let arr = Array.of(3, 4, 7, 9, 11);
        console.log('arr=', arr);
        //arr= [ 3, 4, 7, 9, 11 ]
        
        let empty = Array.of();
        console.log('empty=', empty);
        //empty= []
    }
```
####Array.from把伪数组或者一些集合转换成数组

```js
    //把伪数组或者一些集合转换成数组
    //伪数组不支持foreach
    {
        let p = document.querySelectorAll('p');
        let pArr = Array.from(p);
        pArr.forEach(function(item, index) {
        console.log(item.textContent, index);
        });
        //映射关系
        console.log(Array.from([1, 3, 5], function(item) {
        return item * 2
        }));
    }
```
####将数组中的元素替换成指定的数
```js
    //将数组中的元素替换成指定的数
    {
        console.log('fill-7', [1, 'a', undefined].fill(7));
        //fill-7 [ 7, 7, 7 ]
        
        //从起始位置到结束位置替换
        console.log('fill,post', ['a', 'b', 'c'].fill(7, 1, 3));
        //fill,post [ 'a', 7, 7 ]
    }
```
####key返回操作
```js
    //key返回
    {
        for (let index of ['1', 'c', 'ks'].keys()) {
            console.log('keys', index)
            //keys 0
            //keys 1
            //keys 2
        }


        for (let values of ['1', 'c', 'ks'].values()) {
            console.log('values', values)
            //1
            //c
            //ks
        }

        //不存在兼容性问题
        //entries 方法
        //返回一个迭代器，它返回数组的键/值对。

        for (let [index, values] of ['1', 'c', 'ks'].entries()) {
            console.log('entries', index, values)
            //entries 0 1
            //entries 1 c
            //entries 2 ks
        }
    }
```

####数组替换位置
```js
    //替换的位置从0开始.读取的位置从3开始,截止位置是4
    {
        console.log([1, 2, 3, 4, 5].copyWithin(0, 3, 4));
        //[ 4, 2, 3, 4, 5 ]
    }
```

####查找一个元素是否在数组中
```js
    //查找一个元素是否在数组中
    //后面跟函数
    {
        //find只找到满足条件的第一个,之后就不往下继续查找
        console.log([1, 2, 3, 4, 5, 6].find(function(item) {
            return item > 3;
            //4
        }))

        console.log([1, 2, 3, 4, 5, 6].find((value) => {
            return value == 2;
            //2
        }));

        //找到满足条件的数组下标
        console.log([1, 2, 3, 4, 5, 6].findIndex(function(item) {
            return item > 3;
            //3
        }))
    }
```
####查找数组中是否包含当前元素
```js
    //查找数组中是否包含当前元素
    //后面直接输入值
    {
        console.log('number', [1, 2, NaN].includes(1));
        //number true
        console.log('number', [1, 2, NaN].includes(NaN));
        //number true
    }
```
