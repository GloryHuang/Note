### 转换成字符串类型

##### 1.toString() 简单类型转换成String
 
 * Null和undefined无toString方法

```js
    var age = 18;

    var ageString = age.toString();
    console.log(ageString);  // 结果 "18"
    var result = true;
    var resultString = result.toString();
    console.log(resultString);//结果"true" 数值类型的toString()，可以携带一个参数，输出对应进值

    var num = 10;
    console.log(num.toString()); 
    //"10" 默认是10进制
    console.log(num.toString(10));//"10"
    console.log(num.toString(8)); //"12"
    console.log(num.toString(16));//"a"
    console.log(num.toString(2)); //"1010"

```
##### 2.String()

```js

    var age = 18; 

    console.log(String(age)); //结果 "18"

    var result = true;

    console.log(String(result)); //结果 "true"

    console.log(String(undefined)); 
    //结果"undefined"

    String()函数存在的意义：有些值没有toString()，这个时候可以使用String()。比如：undefined和null

```

##### 3.拼接字符串

```js
例如1： var age = 18; 

var str = age + "岁";

console.log(str);

例如2：

var str = "" + 18; //结果是"18"
```



### 转换成数值类型
 
 * 此转换容易产生NaN，一旦被转换的变量中含有非数字字符，都容易出现NaN
```js
三个把值转换成数值类型的函数：
Number()、 parseInt()、 parseFloat()
```

##### 1.number\(\)

```js
Number\(\)可以把任意值转换成数值，如果要转换的字符串中有一个不是数值的字符，返回NaN
例如：
var num1 = Number\(true\); \/\/true返回1  false返回0
var num2 = Number\(undefined\); \/\/返回NaN
var num3 = Number\("hello"\);  \/\/返回NaN
var num4 = Number\("   "\); \/\/如果是空字符串返回0
var num5 = Number\(123\); \/\/返回123，如果是数字，简单返回
var num6 = Number\("123abc"\);  \/\/NaN
var num7 = Number\("abc123"\);  \/\/NaN
```

##### 2.parseInt\(\)

```js
parseInt()把字符串转换成整数
var num1 = parseInt("12.3abc");  //返回12，如果第一个字符是数字会解析知道遇到非数字结束
var num2 = parseInt("abc123");  //返回NaN，如果第一个字符不是数字或者符号就返回NaN
var num3 = parseInt("");        //空字符串返回    NaN，Number("")返回0
var num5 = parseInt("10");      //返回10
var num4 = parseInt("0xA");     //返回10
```

##### 3.parseFloat\(\)

```js
parseFloat()把字符串转换成浮点数
parseFloat()和parseInt非常相似，不同之处在与
parseFloat会解析第一个. 遇到第二个.或者非数字结束
parseFloat不支持第二个参数，只能解析10进制数
如果解析的内容里只有整数，解析成整数
```

### 转换成布尔类型

```js
Boolean()函数
例如：
 var b = Boolean("123");   //返回yes
流程控制语句会把后面的值隐式转换成布尔类型
例如：
var message;
if (message) {     //会自动把message转换成false
//todo...
}

转换为false的值：false、""、0和NaN、null、undefined

 //转换为true 非空字符串 非0数字 true 任何对象 

 //转换成false 空字符串 0 false null undefined
```

