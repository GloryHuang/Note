###ES6正则扩展


####正则表达式的声明

```js
    //在ES6中声明正则表达式
    {
        //ES5中声明正则表达式的方法
        let regex = new RegExp('xyz', 'i');
        let regex2 = new RegExp(/xyz/i);
        console.log(regex.test('xyz123'), regex2.test('xyz123'));
        //true true

        //ES6中声明正则表达式的方法
        let regex3 = new RegExp(/xyz/ig, 'i');
        //flags
        //查看当前正则表达式使用的修饰符是什么
        console.log(regex3.flags);
        //i

    }
```


####ES6新增修饰符

```js
    //ES6新增的 y 修饰符
    //y修饰符必须在开始的位置匹配
    //exec()返回一个数组，其中存放匹配的结果。如果未找到匹配，则返回值为 null。
    {
        let s = 'bbb_bb_b';
        let a1 = /b+/g;
        let a2 = /b+/y;
        console.log('One', a1.exec(s), a2.exec(s));
        //One [ 'bbb', index: 0, input: 'bbb_bb_b' ] [ 'bbb', index: 0, input: 'bbb_bb_b'

        console.log('Two', a1.exec(s), a2.exec(s));
        //Two [ 'bb', index: 4, input: 'bbb_bb_b' ] null

        //sticky属性
        //判断正则是否设置了y修饰符。
        //返回布尔值。
        console.log(a1.sticky, a2.sticky);
        //false true
        
    }


    {
         console.log('u-1', /^\uD83D$/.test('\uD83D\uDC2A'));
        //u-1 false

        console.log('u-2', /^\uD83D$/u.test('\uD83D\uDC2A'));
        //u-2 false


        //a的Unicode编码是\u61
        //根据Unicode编码进行正则匹配
        console.log(/\u{61}/.test('a'));
        //返回 false

        console.log(/\u{61}/u.test('a'));
        //返回 true



        console.log('\u{20BB7}');
        //false

        let s = '𠮷';

        console.log('u', /^.$/.test(s));
        // true

        console.log('u-2', /^.$/u.test(s));
        //𠮷

        console.log('test', /𠮷{2}/.test('𠮷𠮷'));
        // test false


        console.log('test-2', /𠮷{2}/u.test('𠮷𠮷'));
        // test-2 true
        }
    
```