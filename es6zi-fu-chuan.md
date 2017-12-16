###ES6字符串操作

####字符串操作

    //字符串操作
    
    {

        console.log('a', `\u0061`);
        console.log('s', `\u20BB7`);

        console.log('s', `\u{20BB7}`);

    }


    //charAt() 方法可返回指定位置的字符。
    //charCodeAt() 方法可返回指定位置的字符的 Unicode 编码
    //ES6提供了codePointAt方法，能够正确处理4个字节储存的字符，返回一个字符的码点。
    //codePointAt方法是测试一个字符由两个字节还是由四个字节组成的最简单方法。
    //
    {
        let s = '𠮷';

        console.log('length', s.length);
        console.log('0', s.charAt(0));
        console.log('1', s.charAt(1));
        console.log('at0', s.charCodeAt(0));
        console.log('at1', s.charCodeAt(1));


        let s1 = '𠮷a';
        console.log(s1.length);
        console.log('code0', s1.codePointAt(0));
        console.log('code0', s1.codePointAt(0).toString(16));
        console.log('code1', s1.codePointAt(1));
        console.log('code2', s1.codePointAt(2));

    }


    //fromCharCode() 可接受一个指定的 Unicode 值，然后返回一个字符串。
    {
        console.log('fromCharCode',String.fromCharCode('0x20bb7'));
        console.log('fromCharCode',String.fromCodePoint('0x20bb7'));
    }

####遍历字符串


* 遍历字符串

```js
    {
        let str = '\u{20bb7}abc';
        //ES5遍历不出字节长度大于2的字符(否则会乱码)
        for (let i = 0; i < str.length; i++) {
            // console.log('ES5',str[i]);
        }
```

* ES6遍历当前字符串(不乱码)

```js 
    //ES6遍历当前字符串(不乱码)
    for (let code of str) {
            console.log('ES6', code);
        }
    }

```

####查看是否有包含查找的字符串

    //查看是否有包含查找的字符串
    //starsWith() 查看字符是否以查询的字段开头
    //endWith()	  查看字符是否以查询的字段结尾
    {
        let str = 'string';
        console.log('include', str.includes('s')); //返回true

        let str1 = 'hello';
        console.log('includes', str1.includes('w')); //返回false
        console.log('starts', str.startsWith('str'));
        console.log('ends', str.endsWith('ing'));
        console.log('ends', str.endsWith('g'));
    }

####复制字符串

    //复制字符串
    {
        let str = 'abc';
        console.log('Strng', str.repeat(2));
    }

####字符串模板

    //字符串模板
    {
        let name = 'list';
        let info = 'Hello World!';
        let m = `I am a ${name},${info}`;
        console.log(m);
    }



####补白
    //补白的作用
    {
        //指定长度,长度如果不足用设置的‘值’补偿

        //向前补
        console.log('1'.padStart(2, '0'));
        //向后补
        console.log('1'.padEnd(2, '0'));
    }

    {
	console.log('================');
        for (let i = 0; i <= 10; i++) {
            console.log(i.toString().padStart(2,'0'));
    }
    
####raw转译斜杠(添加\斜杠)
    //raw转译斜杠(添加\斜杠)
    {
	console.log(String.raw`Hi\n${1+2}`);
	console.log(`Hi\n${1+2}`);
    }