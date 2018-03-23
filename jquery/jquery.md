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


