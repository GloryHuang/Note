###ES6正则扩展


####正则表达式的声明

//在ES6中声明正则表达式
{
    //ES5中声明正则表达式的方法
    let regex = new RegExp('xyz', 'i');
    let regex2 = new RegExp(/xyz/i);
    console.log(regex.test('xyz123'), regex2.test('xyz123'));


    //ES6中声明正则表达式的方法
    let regex3 = new RegExp(/xyz/ig, 'i');
    //查看当前正则表达式使用的修饰符是什么
    console.log(regex3.flags);

}

//ES6新增的 y 修饰符
//y修饰符必须在开始的位置匹配
//exec()返回一个数组，其中存放匹配的结果。如果未找到匹配，则返回值为 null。
{
    let s = 'bbb_bb_b';
    let a1 = /b+/g;
    let a2 = /b+/y;
    console.log('One', a1.exec(s), a2.exec(s));
    console.log('Two', a1.exec(s), a2.exec(s));

    console.log(a1.sticky, a2.sticky);
}


{
    console.log('u-1', /^\uD83D$/.test('\uD83D\uDC2A'));
    console.log('u-2', /^\uD83D$/u.test('\uD83D\uDC2A'));

    //a的Unicode编码是\u61
    //根据Unicode编码进行正则匹配
    console.log(/\u{61}/.test('a')); //返回 false
    console.log(/\u{61}/u.test('a')); //返回 true



    console.log('\u{20BB7}');

    let s = '𠮷';

    console.log('u',/^.$/.test(s));
    console.log('u-2',/^.$/u.test(s));


    console.log('test',/𠮷{2}/.test('𠮷𠮷'));
    console.log('test-2',/𠮷{2}/u.test('𠮷𠮷'));
}