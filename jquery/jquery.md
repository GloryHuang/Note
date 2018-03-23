###jQuery


###事件操作


* 事件绑定

 * click()
 * bind()
 * delegate()
 * on()
 
 

####click()

 ```js
  
  click()事件不会重叠
  
  $().click(function(){});
  
  解绑：$().unbiind("click");
  
 ```
 
####bind()

```js

   bind()绑定（可以绑定多个事件）
   
   $().bind("click mouseenter",function(){});
   
   解绑：$().unbind("click");

```

####delegate()

```js

   delegate()绑定（元素，事件或者多个事件，函数）
   
   $().delegate("div","click mouseenter",function(){

    });

  解绑：$(document).undelegate(".box","mouseenter", fn);
       $(document).undelegate(".box","mouseenter", fn2);


  例如：
    // $(document).delegate(".box", "click mouseenter", function() {
        //     alert("2");
        // });


        // $(document).delegate(".box", "click mouseenter", fn);
        // $(document).delegate(".box", "click mouseenter", fn2);

        // function fn() {
        //     alert("1");
        // }

        // function fn2() {
        //     alert("2");
        // }


    解绑：$(document).undelegate(".box","mouseenter", fn);
         $(document).undelegate(".box","mouseenter", fn2);

```

####on()

```js
  
    
    on()绑定（元素，事件或者多个事件，数据(json)，函数）
    
    $().on("div","click mouseenter",{"name":111}function(e){
         e.data.name;
    });

    解绑：$().off("click);


```

###元素操作

```js
 
     设置属性
    1.attr("title",aaaa);
      attr("class",aaaa);

    2.prop("sectled/checked....",true);


```

###DOM操作


####添加元素

```js

 1. html();
 
 2. append();//在元素末尾添加
 
（要添加的元素）.appendTo("添加元素的位置")

 3. prepend();//在元素最前面添加

（要添加的元素）.prependTo("添加元素的位置")
 
 4. before();//在子元素前添加

 5. after();//在子元素后添加

```

####清空元素

 * html("");
 
 * empty();

####删除元素

 * remove();
 
####复制元素

 * clone();
 
```js
   var newUl = $(".box ul").clone();
            $(".box").append(newUl);
```



###动画操作

* 显示/隐藏动画

```js  

  show/hide();不带参数
  show/hide(2000)(带参数);毫秒值
  show/hide("fast"/"slow"/"normal");带字符串
  show/hide(1000,fn)//带回调方法
  
  切换  另附(推荐用法)：
  toggle();
  
```

* 滑入/滑出动画

```js

  slideUp/sildeDown();不带参数
  slideUp/sildeDown(2000);(带参数);毫秒值
  slideUp/sildeDown();("fast"/"slow"/"normal");带字符串
  slideUp/sildeDown();(1000,fn)//带回调方法

  切换 另附(推荐用法)：
  slideToggle();


```


* 淡入/淡出动画


```js

 fadedIn/fadeOut();不带参数
 fadedIn/fadeOut(2000);(带参数);毫秒值
 fadedIn/fadeOut();("fast"/"slow"/"normal");带字符串
 fadedIn/fadeOut();(1000,fn)//带回调方法

 切换 另附(推荐用法)：
 fadeToggle();

```


* 切换透明度动画

```js


 fadeTo()
 fadeTo();不带参数
 fadeTo(2000);(带参数);毫秒值
 fadeTo("fast"/"slow"/"normal");带字符串
 fadeTo(1000,透明度值,fn)//带回调方法

```

* 自定义动画


```js
自定义动画
        animate({json},speed,fn);

        animate()不支持背景色



      //animate自定义动画实现显示效果
       $("div").animate({"display": "none","opacity":0,"width":0,"height":0} , 2000);

         //animate自定义动画实现滑出效果
        // $("div").animate({"height": 0} , 2000);

        //animate自定义动画实现淡出效果
         $("div").animate({"opacity": 0} , 2000);

  //animate自定义动画实现改变透明度效果
        // $("div").animate({"opacity": 0.5} , 2000);
 



```