
      
####告诉IE浏览器，无论是否用DTD声明文档标准，IE8/9都会以IE7引擎来渲染页面。 

```css

      <meta http-equiv="X-UA-Compatible" content="IE=7"> 
      
```


####告诉IE浏览器，IE8/9都会以IE8引擎来渲染页面。 

```css
 
      <meta http-equiv="X-UA-Compatible" content="IE=8">
```


####告诉IE浏览器，IE8/9及以后的版本都会以最高版本IE来渲染页面。 


 ```css

      <meta http-equiv="X-UA-Compatible" content="IE=edge"> 
     
```
 

####IE=edge告诉IE使用最新的引擎渲染网页，chrome=1则可以激活Chrome Frame.



```css
      <meta http-equiv="X-UA-Compatible" content="IE=7,IE=9"> 
      <meta http-equiv="X-UA-Compatible" content="IE=7,9"> 
      <meta http-equiv="X-UA-Compatible" content="IE=Edge,chrome=1"> 
```



####创建一个“视口”

```css
      <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">

```

###网页重定向

```css

      <meta http-equiv="refresh" content="5; http://www.baidu.com">
      
```


