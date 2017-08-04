### 转换成字符串的方法

##### 1.toString
```
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

```
##### 2.String
    var age = 18; 

    console.log(String(age)); //结果 "18"

    var result = true;

    console.log(String(result)); //结果 "true"

    console.log(String(undefined)); 
    //结果"undefined"

    •String()函数存在的意义：有些值没有toString()，
这个时候可以使用String()。比如：undefined和null

```

##### 3.拼接字符串

    •例如1： var age = 18; 

    var str = age + "岁";

    console.log(str);

    •例如2：

    var str = "" + 18; //结果是"18"

 

###装换成数值类型






