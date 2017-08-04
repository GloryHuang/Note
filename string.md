### 转换成字符串的方法

##### 1.toString\(\)

```js
    var age = 18;

    var ageString = age.toString();
    console.log(ageString);  // 结果 "18"
    var result = true;
    var resultString = result.toString();
    console.log(resultString);//结果"true" 数值类
型的toString()，可以携带一个参数，输出对应进值

    var num = 10;
    console.log(num.toString()); 
    //"10" 默认是10进制
    console.log(num.toString(10));//"10"
    console.log(num.toString(8)); //"12"
    console.log(num.toString(16));//"a"
    console.log(num.toString(2)); //"1010"

```

```js
##### 2.String()
    var age = 18; 

    console.log(String(age)); //结果 "18"

    var result = true;

    console.log(String(result)); //结果 "true"

    console.log(String(undefined)); 
    //结果"undefined"

    •String()函数存在的意义：有些值没有toString()，这个时候可以使用String()。比如：undefined和null

```

##### 3.拼接字符串

```js
•例如1： var age = 18; 

var str = age + "岁";

console.log(str);

•例如2：

var str = "" + 18; //结果是"18"
```



### 装换成数值类型

```js
三个把值转换成数值类型的函数：
Number()、 parseInt()、 parseFloat()
```

##### 1.number\(\)

Number\(\)可以把任意值转换成数值，如果要转换的字符串中有一个不是数值的字符，返回NaN

##### 2.parseInt\(\)

```
parseInt()把字符串转换成整数
var num1 = parseInt("12.3abc");  //返回12，如果第一个字符是数字会解析知道遇到非数字结束
var num2 = parseInt("abc123");  //返回NaN，如果第一个字符不是数字或者符号就返回NaN
var num3 = parseInt("");        //空字符串返回    NaN，Number("")返回0
var num5 = parseInt("10");      //返回10
var num4 = parseInt("0xA");     //返回10
```

