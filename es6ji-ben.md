####ES6

###构建ES6的开发环境


#####构建工具

+ gulp(任务自动化)
- babel(编译工具)
* webpack(编译工具)
- npm





#####ES6强制开启严格模式

'use strict'

    严格模式的注意点:
        变量未声明不能引用,否则会报引用错误



##let 

    1.在块作用域声明的let变量只在当前声明的块作用域内有效。
    2.使用let变量不能重复定义变量
    
    
##const

    1.使用const声明的常量是不能修改的,但是在引用类型内,返回的是存储的指针,指针不变,但是对象本身是可以变得。
    2.const和let在块作用域使用的方法是相同的。
    3.const声明的时候必须赋值。



###解构赋值
   
    声明没有赋值,没有配对成功返回undefind.


###正则扩展

    新增s、y修饰符
    
    let regex = new RegExp('xyz', 'i');
    let regex2 = new RegExp(/xyz/i);


    console.log(regex.test('xyz123'), regex2.test('xyz123'));

    let regex3 = new RegExp(/xyz/ig, 'i');


    console.log(regex3.flags);
    输出i
    
    ES6中以此方式生成构造函数,在ES6允许第一个参数以正则表达式的形式,第二个参数的修饰符会覆盖第一个参数表达式的修饰符
    
    
    flags  获取正则对象的修饰符  igm
    sticky 查看是否开启粘黏模式
    
    g和y修饰符：
    
        相同点：
        
             都是全局匹配
             g修饰符是从上一次匹配的位置开始继续找
             y匹配的字符必须是紧跟的第一个才算匹配成功
             
    