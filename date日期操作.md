####日期操作

```js

    Date-引用类型，JavaScript中的内置对象
    获取当前时间
    var date = new Date();   //UTC的时间
```

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


####Date方法

```js
    
    toString()
    valueOf()   -- 返回时间对象对应的毫秒数字，因此可以直接使用 >  < 判断两个时期的大小

    toDateString()
    toTimeString()
    toLocaleDateString()
    toLocaleTimeString()
    不同的浏览器，各种toString()返回的结果不一致

```

####获取时间

```js

    getTime()  返回毫秒数和valueOf()结果一样
    getMilliseconds() 
    getSeconds()  返回0-59
    getMinutes()  返回0-59
    getHours()   返回0-23
    getDay()     返回星期几 0周日   6周6
    getDate()    返回当前月的第几天
    getMonth()   返回月份，从0开始
    getFullYear()   返回4位的年份  如 2016
    
```

####设置时间的形式

```js

    //第一种
     var date1 = new Date();
     console.log(date1);
     //Fri Feb 10 2017 12: 52: 20 GMT + 0800(中国标准时间)

    //第二种：设置指定时间(兼容性最强)
     var date2 = new Date("2017/2/10 00:00:00");
     console.log(date2);
     //Fri Feb 10 2017 00:00:00 GMT+0800 (中国标准时间)

    //第三种
     var date3 = new Date('Fri Feb 10 2017 12: 52: 20 GMT');
     console.log(date3);
     //Invalid Date

    //第四种
     var date4 = new Date(2016, 1, 27);
     console.log(date4);
     //Sat Feb 27 2016 00:00:00 GMT+0800 (中国标准时间)

```
####获取日期和时间

```js
    
     getDate()                 获取日 1-31
     getDay ()                 获取星期 0-6（0代表周日）
     getMonth ()             获取月 0-11（1月从0开始）
     getFullYear ()	       获取完整年份（浏览器都支持）
     getHours ()	       获取小时 0-23
     getMinutes ()	       获取分钟 0-59
     getSeconds ()	       获取秒  0-59
     getMilliseconds ()    获取毫秒 （1s = 1000ms）
     getTime ()	       返回累计毫秒数(从1970/1/1午夜)



     console.log(date1.getDate()); //获取日 1 - 31 
     console.log(date1.getDay()); //获取星期 0 - 6（ 0 代表周日）
     console.log(date1.getMonth()); //获取月 0 - 11（ 1 月从0开始）
     console.log(date1.getFullYear()); //获取完整年份（ 浏览器都支持）
     console.log(date1.getHours()); //获取小时 0 - 23
     console.log(date1.getMinutes()); //获取分钟 0 - 59
     console.log(date1.getSeconds()); //获取秒 0 - 59
     console.log(date1.getMilliseconds()); //获取毫秒（ 1 s = 1000 ms）
     console.log(date1.getTime()); //返回累计毫秒数(从1970 / 1 / 1 午夜)



    //获取当前时间距1979/01/01的毫秒值
     var date11 = Date.now();
     var date22 = +new Date();
     var date33 = new Date().getTime();
     var date44 = new Date().valueOf();

     console.log(date11);
     console.log(date22);
     console.log(date33);
     console.log(date44);

```

#####倒计时程序
    
     function getTimeString(d) {
            //如果date不是日期对象，返回
            if (!date instanceof Date) {
                return;
            }

            var year,month,date,hour,minute,second;
            year = d.getFullYear();
            month = d.getMonth() + 1;
            date = d.getDate();
            hour = d.getHours();
            minute = d.getMinutes();
            second = d.getSeconds();
	    month = month < 10? "0" + month : month;
            date = date < 10?"0"+date:date;
            hour = hour < 10?"0"+hour:hour;
            minute = minute < 10?"0"+minute:minute;
            second = second < 10?"0"+second:second;
            return year + "-" + month + "-" + date + " " + hour + ":" + minute + ":" + second;
        }



