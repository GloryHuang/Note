
      
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
      <meta http-equiv="refresh" content="http://www.baidu.com"> 
```

###告诉搜索引擎你的站点的作者是谁

```css
   <meta http-equiv="Author" content="你的姓名">
```

###让你的网页被搜索引擎以什么样的方式抓取


```css
   <meta http-equiv="Robots" content="all|none|index|noindex|follow|nofollow">
   
   all:文件被检索,页面上的链接可以被查询
   none:文件不被检索,而且页面上上的链接不可以被查询
   index:文件将被检索
   follow:页面上的链接可以被查询
   noindex:文件将不被检索,但页面上的链接可以被查询
   nofollow:文件将不被检索,页面上的链接可以被查询
   
```

