###ES6中的数据结构对比

     * Map与Array的对比
     * Set与Array的对比




####Map与Array的对比
```js
//Map与Array的对比
//数据结构横向对比, 增,删,改,查
{
    let map = new Map();
    let array = Array();


    //增
    map.set('t', 1);
    array.push({ t: 1 });
    console.info('map-array', map, array);


    //查
    let map_exist = map.has('t');
    let array_exist = array.find(item => item.t);
    console.info('map-array', map_exist, array_exist);

    //改
    map.set('t', 2);
    array.forEach(item => item.t ? item.t = 2 : '');
    console.info('map-array-modify', map, array);

    //删
    map.delete('t');
    let index = array.findIndex(item => item.t);
    array.splice(index, 1);
    console.info('map - array - empty', map, array)
}


```

####Set与Array的对比

```js
//Set与Array的对比

{
    let set = new Set();
    let array = [];



    //增
    set.add({ t: 1 });
    array.push({ t: 1 });
    console.info('set-array', set, array);


    //查
    let set_exist = set.has({ t: 1 }); //false
    let array_exist = array.find(item => item.t);
    console.info('set-array', set_exist, array_exist);

    //改
    set.forEach(item => item.t ? item.t = 2 : '');
    array.forEach(item => item.t ? item.t = 2 : '');
    console.info('set-array-modify', set, array);

    //删
    set.forEach(item => item.t ? set.delete(item) : '');
    let index = array.findIndex(item => item.t);
    array.splice(index, 1);
    console.info('set - array - empty', set, array)
}


```

####Map与Set和Object的对比
```js
//Map和Object的对比
//Set和Object的对比

{
    let item = { t: 1 };
    let map = new Map();
    let set = new Set();
    let obj = {};


    //增
    map.set('t', 1);
    set.add(item);
    obj['t'] = 1;
    console.info('map-set-Object', map, set, obj);


    //查
    console.info({
        map_exist: map.has('t'),
        set_exist: set.has(item),
        obj_exit: 't' in obj
    });


    //改
    map.set('t', 2);
    item.t = 2;
    obj['t'] = 2;
    console.info('map-set-Object-Modify', map, set, obj);

    //删
    map.delete('t');
    set.delete(item);
    delete obj['t'];
    console.info('map-set-Object-Delete', map, set, obj);

}
```

结论:
    * Map和set的效率最好
    * Map的成本最低



```js
//总结：
//
//能使用Map,不使用数组
//复杂的数据结构放弃使用数组,使用Map数据结构
//如果对数据结构存储的要求的唯一性,考虑使用Set
```


#####//优先使用Map,如果对数据要求比较高,保证数据的唯一性,考虑使用Set,放弃使用Object和Array