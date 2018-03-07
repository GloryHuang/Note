###CSS兼容问题

####CSS Hack


#####CSS Hack大致有3种表现形式，CSS类内部Hack、选择器Hack以及HTML头部引用(if IE)Hack，CSS Hack主要针对类内部Hack：比如 IE6能识别下划线"_"和星号" * "，IE7能识别星号" * "，但不能识别下划线"_"，而firefox两个都不能认识。    

####头部hack(条件注释)


* 说明：在标准模式中

```css
   
    
    “-″减号是IE6专有的hack
    “\9″ IE6/IE7/IE8/IE9/IE10都生效
    “\0″ IE8/IE9/IE10都生效，是IE8/9/10的hack
    “\9\0″ 只对IE9/IE10生效，是IE9/10的hack
    
```
    
####其他兼容

```css
    <!-- HTML5 shim and Respond.js for IE8 support of HTML5 elements and media queries -->
    <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
    <!--[if lt IE 9]>
      <script src="https://cdn.bootcss.com/html5shiv/3.7.3/html5shiv.min.js"></script>
      <script src="https://cdn.bootcss.com/respond.js/1.4.2/respond.min.js"></script> 
    <![endif]-->
```