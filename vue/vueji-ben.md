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

####v-cloak

```js
    
     v-cloak指令保持在元素上直到关联实例结束编译后自动移除，v-cloak和 CSS 规则如 [v-cloak] { display: none } 一起用时，这个指令可以隐藏未编译的 Mustache 标签直到实例准备完毕。
    通常用来防止{{}}表达式闪烁问题
    例如：
    <style>
     [v-cloak] { display: none } 
    </style>
    
     <!-- 在span上加上 v-cloak和css样式控制以后，浏览器在加载的时候会先把span隐藏起来，知道 Vue实例化完毕以后，才会将v-cloak从span上移除，那么css就会失去作用而将span中的内容呈现给用户 -->
    <span v-cloak>{{msg}}</span>    
    
     new Vue({
              data:{
                  msg:'hello ivan'
                }
          })

```

####v-model以及双向数据绑定


```js
    
    1、在表单控件或者组件上创建双向绑定
    
    2、v-model仅能在如下元素中使用：
       input
       select
       textarea
       components（Vue中的组件）
       
    3、举例：
       <input type="text" v-model="uname" />
       
     new Vue({
              data:{
                  uname:'' //这个属性值和input元素的值相互一一对应，二者任何一个的改变都会联动的改变对方
                }
          })
          
    4、修饰符（了解）：
        .lazy - 取代 input 监听 change 事件
        .number - 自动将输入的字符串转为数字
        .trim - 自动将输入的内容首尾空格去掉




```

####v-bind


```js

    1、作用：可以给html元素或者组件动态地绑定一个或多个特性，例如动态绑定style和class
    
    2、举例：
        <img v-bind:src="imageSrc">   
        <div v-bind:class="{ red: isRed }"></div>
        <div v-bind:class="[classA, classB]"></div>
        <div v-bind:class="[classA, { classB: isB, classC: isC }]">
        <div v-bind:style="{ fontSize: size + 'px' }"></div>
        <div v-bind:style="[styleObjectA, styleObjectB]"></div>
           
    3、缩写形式
        <img :src="imageSrc">
        <div :class="{ red: isRed }"></div>
        <div :class="[classA, classB]"></div>
        <div :class="[classA, { classB: isB, classC: isC }]">
        <div :style="{ fontSize: size + 'px' }"></div>
        <div :style="[styleObjectA, styleObjectB]"></div>



```


####v-for

```js

      1、作用：通常是根据数组中的元素遍历指定模板内容生成内容
      
      2、用法举例：
          <div v-for="item in items">
              {{ item.text }}
            </div>
            new Vuew({
                data:{
                    items:[{text:'1'},{text:'2'}]                
                    }
            });
      3、可以为数组索引指定别名（或者用于对象的键）：
          Vue1.0写法:
            <div v-for="(index,item) in items"></div>
            <div v-for="(key,val) in user"></div>
              new Vue({
                data:{
                    items:[{text:'1'},{text:'2'}],
                    user:{uname:'ivan',age:32}
                    }
            });
            
          Vue2.0写法:
            <div v-for="(item, index) in items"></div>
            <div v-for="(val, key) in user"></div>
            <div v-for="(val, key, index) in user"></div>            
             new Vue({
                data:{
                    items:[{text:'1'},{text:'2'}],
                    user:{uname:'ivan',age:32}
                    }
            });
            
       4、v-for 默认行为试着不改变整体(为了性能考虑的设计)，而是替换元素。迫使其重新排序的元素,在Vue2.0版本中需要提供一个 key 的特殊属性，在Vue1.0版本中需要提供一个 track-by="$index":
       
       Vue2.0写法：
       <div v-for="item in items" :key="item.id">
          {{ item.text }}
        </div>
        
       Vue1.0写法：
       <div v-for="item in items" track-by="$index">
          {{ item.text }}
        </div>
        
      5、vue1.0与vue2.0对于v-for使用区别总结：
          1、vue1.0中有$index ，而vue2.0中将$index移除
          2、vue1.0中 (index,item) in list  而 vue2.0 变成了 (item,index) in list的写法
          3、vue1.0中使用 track-by来标记dom对象的唯一性，vue2.0中改成了 :key
          






```

