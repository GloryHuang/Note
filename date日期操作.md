####日期操作



    Date-引用类型，JavaScript中的内置对象
    获取当前时间
    var date = new Date();   //UTC的时间

    //返回数字，时间的毫秒形式
    var date = Date.now();   //HTML5，IE9+
    var date = +new Date();  //不支持now方法的时候


    var date = new Date(2005,10,1); 
    可以接受三种参数
    2005，10，1日期的每一部分
    "2005-10-1"  字符串的日期格式
    表示日期的毫秒形式1128096000000
     var date = Date.parse("2005-10-1");
    把字符串或2005，10，1日期的每一部分转换成日期的毫秒形式，如果字符串的格式不是时间的正确格式返回NaN


    
    toString()
    valueOf()   -- 返回时间对象对应的毫秒数字，因此可以直接使用 >  < 判断两个时期的大小

    toDateString()
    toTimeString()
    toLocaleDateString()
    toLocaleTimeString()
    不同的浏览器，各种toString()返回的结果不一致

















    //第一种
    // var date1 = new Date();
    // console.log(date1);

    //第二种：设置指定时间(兼容性最强)
    // var date2 = new Date("2017/2/10 00:00:00");
    // console.log(date2);

    //第三种
    // var date3 = new Date('Fri Feb 10 2017 12: 52: 20 GMT + 0800(中国标准时间)');
    // console.log(date3);

    //第四种
    // var date4 = new Date(2016, 1, 27);
    // console.log(date4);

    // 获取日期和时间
    // getDate()                 获取日 1-31
    // getDay ()                 获取星期 0-6（0代表周日）
    // getMonth ()             获取月 0-11（1月从0开始）
    // getFullYear ()	       获取完整年份（浏览器都支持）
    // getHours ()	       获取小时 0-23
    // getMinutes ()	       获取分钟 0-59
    // getSeconds ()	       获取秒  0-59
    // getMilliseconds ()    获取毫秒 （1s = 1000ms）
    // getTime ()	       返回累计毫秒数(从1970/1/1午夜)


    //获取日期和时间
    // console.log(date1.getDate()); //获取日 1 - 31
    // console.log(date1.getDay()); //获取星期 0 - 6（ 0 代表周日）
    // console.log(date1.getMonth()); //获取月 0 - 11（ 1 月从0开始）
    // console.log(date1.getFullYear()); //获取完整年份（ 浏览器都支持）
    // console.log(date1.getHours()); //获取小时 0 - 23
    // console.log(date1.getMinutes()); //获取分钟 0 - 59
    // console.log(date1.getSeconds()); //获取秒 0 - 59
    // console.log(date1.getMilliseconds()); //获取毫秒（ 1 s = 1000 ms）
    // console.log(date1.getTime()); //返回累计毫秒数(从1970 / 1 / 1 午夜)



    //获取当前时间距1979/01/01的毫秒值
    // var date11 = Date.now();
    // var date22 = +new Date();
    // var date33 = new Date().getTime();
    // var date44 = new Date().valueOf();

    // console.log(date11);
    // console.log(date22);
    console.log(date33);
    // console.log(date44);