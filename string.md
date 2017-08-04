### 转换成字符串的方法

##### 1.toString

    var age = 18;
    
    var ageString = age.toString();
    console.log(ageString);  // 结果 "18"
    var result = true;
    var resultString = result.toString();
    console.log(resultString);// 结果 "true"
    数值类型的toString()，可以携带一个参数，输出对应进制值

    var num = 10;
    console.log(num.toString());  //"10" 默认是10进制
    console.log(num.toString(10));//"10"
    console.log(num.toString(8)); //"12"
    console.log(num.toString(16));//"a"
    console.log(num.toString(2)); //"1010"




