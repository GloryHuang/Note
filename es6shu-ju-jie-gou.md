###ES6数据结构


 ####ES6 数据结构
 
 * Set的用法
 * WeakSet的用法
 * Map的用法
 * WeakMap的用法

    //数组也算是集合
    //Set集合中的元素不能重复,必须是唯一的
    //Map的Key可以是任意的数据类型

###Set

* Sst add   添加元素
* Set delete移除元素
* Set clear 清空元素
* Set has 判断集合中有没有这个元素

####Set has 判断集合中有没有这个元素
```js

    {

        let arr = ['add', 'delete', 'clear', 'has'];
        let list = new Set(arr);
        
        console.log('has', list.has('add'));
        //has true
        
        console.log('has', list.delete('add'), list);
        //has true Set { 'delete', 'clear', 'has' }
        
        list.clear();
        console.log(list);
        //Set {}
    
    }

```


####Set增加元素用add()方法

```js

    //Set增加元素用add()方法
    {
        let list = new Set();
        list.add(5);
        list.add(7);


        //查看当前set有多少个元素
        console.log('size', list.size);
        //size 2

    }
```
####Set的另一种定义方法
```js
    //set的另一种定义方法
    {
        let arr = [1, 2, 3, 4, 5];
        let list = new Set(arr);


        console.log('size', list.size);
        //size 5
    }

    //添加重复的元素是不会报错的
    //只是不会生效
    //去重！！！！
    {
        let list = new Set();
        list.add(1);
        list.add(2);
        list.add(1);

        console.log('list', list);
        //list Set { 1, 2 }
    }

```

####利用Set的特性实现去重

```js
    //利用Set的特性实现去重
    //转换元素的时候不会做数据类型的转换
    //去重的时候查看数据类型是否一致
    {
        let arr = [1, '2', 3, 1, 2, 3, 2, 4, 4, 1, 5];
        let list = new Set(arr);
        console.log('unique', list);
        //unique Set {1, "2", 3, 2, 4…}
    }

```



####Set遍历
```js
//Set遍历
{
    let arr = ['add', 'delete', 'clear', 'has'];
    let list = new Set(arr);

    //遍历Key值(键值)
    for (let key of list.keys()) {
        console.log('key', key);
        //key add
        //key delete
        //key clear
        //key has
    }

    //遍历Value(值)
    for (let values of list.values()) {
        console.log('values', values);
        //values add
        //values delete
        //values clear
        //values has

    }

    //for of 遍历
    for (let values of list) {
        console.log('list-values', values);
        //list-values add
        //list-values delete
        //list-values clear
        //list-values has

    }

    //entries遍历
    for (let [key, values] of list.entries()) {
        console.log('entries', key, values);
        //entries add add
        //entries delete delete
        //entries clear clear
        //entries has has

    }

    //foreach遍历
    list.forEach(function(item, index) {
        console.log('foreach', index, item);
        //foreach add add
        //foreach delete delete
        //foreach clear clear
        //foreach has has

    });

}

```


###WeakSet

* WeakSet和Set支持数据类型不一样
* WeakSet的元素必须是对象(不能是数值,boolean,字符串)
* WeakSet不进行垃圾回收检测
* WeakSet没有clear方法(仅有add、has、delete方法)
* WeakSet没有Set属性
* WeakSet不能遍历

```js
{
    let weaklist = new WeakSet();

    let arg = {};

    weaklist.add(arg);

    //Uncaught TypeError: Invalid value used in weak set
    //非法的值
    // weaklist.add(2);

    console.log('weaklist', weaklist);
    //weaklist WeakSet {}
}
```


###Map


* Map添加元素用set(),Set添加元素用add();
* Map的key值(键值)可以是任意数据类型
* Map获取值用get()
* Map获取长度size
* Map删除元素delete()
* Map清空元素clear()
* 遍历方式和Set一致


####Map第一种定义方法(不带参数)

```js
//第一种定义方法(不带参数)
{
    let map = new Map();
    let arr = ['123'];


    // set(key,value)
    map.set(arr, 456);


    console.log('map', map, map.get(arr));
    //map Map { [ '123' ] => 456 } 456
}

```
####Map第二种定义方法(带参数)

```js
{
    let map = new Map([
        ['a', '213'],
        ['b', 456]
    ]);
    console.log('map args', map);
    //map args Map { 'a' => '213', 'b' => 456 }
    
    console.log('size', map.size);
    //size 2
    
    console.log('delete', map.delete('a'), map);
    //delete true Map { 'b' => 456 }
}
```

###WeakMap

 * WeakMap接受的key值只能是对象
 * WeakMap没有clear
 * WeakMap不能遍历
 * 与WeakSet类似


```js
{
    let weakmap = new WeakMap();

    let o = {};

    weakmap.set(o, 123);
    console.log('weakmap', weakmap.get(o));
    //weakmap 123
}

```

