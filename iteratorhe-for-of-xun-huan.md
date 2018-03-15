####iterator和for..of.....循环

 * 什么是iterator接口
 * iterator的基本用法
 * for.....of


####iterator
```js
{
    let arr = ['hello', 'world'];
    let map = arr[Symbol.iterator]();
    console.log(map.next());
    console.log(map.next());
    console.log(map.next());
}
```

####iterato遍历
```js
//先遍历start,再遍历end
{
    let obj = {
        start: [1, 3, 2],
        end: [7, 9, 8],
        [Symbol.iterator]() {
            let self = this;
            let index = 0;
            let arr = self.start.concat(self.end);
            let len = arr.length;
            // console.log('self',self);
            return {
                next() {
                    if (index < len) {
                        return {
                            value: arr[index++],
                            done: false
                        }
                    } else {
                        return {
                            value: arr[index++],
                            done: true
                        }
                    }
                }
            }
        }
    }
    for (let key of obj) {
        console.log(key);
    }
}
```

####for....of
```js
//for...of循环的过程就是不断调用iterator接口来实现循环
{
    let arr = ['hello', 'world'];
    for (let value of arr) {
        console.log('value', value);
    }
}
```