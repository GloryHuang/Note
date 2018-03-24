###Vue

####MVVM模式

*  MVVM拆分解释为：

  - Model:负责数据存储
  - View:负责页面展示
  - View Model:负责业务逻辑处理（比如Ajax请求等），对数据进行加工后交给视图展示
  
    
- MVVM要解决的问题是将业务逻辑代码与视图代码进行完全分离，使各自的职责更加清晰，后期代码维护更加简单

- 用图解的形式分析Ajax请求回来数据后直接操作Dom来达到视图的更新的缺点，以及使用MVVM模式是如何来解决这个缺点的


![](/assets/d1-11.png)

####Vue的使用

![](/assets/d1-12.png)


###Vue常用指令

####差值表达式\{{}}:


```js


    数据绑定最常见的形式就是使用 “Mustache” 语法（双大括号）的文本插值        
    例如：<span>Message: {{ msg }}</span>
    Mustache 标签将会被替代为对应数据对象上 msg 属性（msg定义在data对象中）的值。
    无论何时，绑定的数据对象上 msg 属性发生了改变，插值处的内容都会更新。

    {{}}对JavaScript 表达式支持，例如：
    {{ number + 1 }}
    {{ ok ? 'YES' : 'NO' }}
    {{ message.split('').reverse().join('') }}

    但是有个限制就是，每个绑定都只能包含单个表达式，如下表达式无效：
    <!-- 这是语句，不是表达式 -->
    {{ var a = 1 }}
    <!-- 流控制也不会生效，请使用三元表达式 -->
    {{ if (ok) { return message } }}


```

####v-text

```js
    
     v-text可以将一个变量的值渲染到指定的元素中,例如：
        <div v-text="msg"></div>
        new Vue({
            data:{
                msg:'hello ivan'                                            
               }
        });
        
        输出结果：
        <div>hello ivan</div>        

```


v-html

```js

    双大括号和v-text会将数据解释为纯文本，而非 HTML 。
      为了输出真正的 HTML ，你需要使用 v-html 指令：
      例如：<div v-html="rawHtml"></div>
          new Vue({
              data:{
                  rawHtml:'<h1>hello ivan</h1>'
                }
          })
          
        被插入的内容都会被当做 HTML,但是对于没有HTML标签的数据绑定时作用同v-text和{{}}
        
    注意：使用v-html渲染数据可能会非常危险，因为它很容易导致 XSS（跨站脚本） 攻击，使用的时候请谨慎，能够使用{{}}或者v-text实现的不要使用v-html



```


