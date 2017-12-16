###数值扩展



####数值扩展
    //数值扩展
    {
        //10进制的2进制表示
        console.log('B', 0B111110111);

        //8进制的2进制表示
        console.log(0o767);

    }

####判断数组的元素是否是有界的

    //判断数组的元素是否是有界的
    {
        console.log('15', Number.isFinite(15));
        console.log('NaN', Number.isFinite(NaN));
        console.log('1/0', Number.isFinite('true' / 0));
        console.log('NaN', Number.isNaN(NaN));
        console.log('NaN', Number.isNaN(0));
    }

####检查是否整数

    //检查是否整数
    {
        console.log('25', Number.isInteger(25));
        console.log('25', Number.isInteger(25.0));
        console.log('25', Number.isInteger(25.1));
        console.log('25', Number.isInteger('25.0'));
    }
####判断是否整数

    //判断是否整数
    {
        console.log(Number.MAX_SAFE_INTEGER, Number.MIN_SAFE_INTEGER)
        console.log('10', Number.isSafeInteger(10));
        console.log('a', Number.isSafeInteger('a'));
    }


####取小数的整数部分

    //取小数的整数部分
    {
        console.log('4.1', Math.trunc(4.1));
        console.log('4.9', Math.trunc(4.9));
    }


####//判断一个数是正数、负数、还是0

    {
        console.log('-5', Math.sign(-5));
        console.log('0', Math.sign(0));
        console.log('5', Math.sign(5));
        console.log('50', Math.sign('50'));
        console.log('foo', Math.sign('foo'));
    }
    
####立方根的计算

    //立方根的计算
    {
        console.log('-1', Math.cbrt(-1));
        console.log('8', Math.cbrt(8));
    }


