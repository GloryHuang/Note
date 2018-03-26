###页面布局


题目:假设高度已知,请写出三栏布局,其中左栏、右栏宽度各位300px,中间自适应
    
####浮动解决方案
    
```js
     <!-- 浮动解决方案 -->
    <section class="layout float">
        <style>
        .layout.float .left {
            float: left;
            width: 300px;
            background-color: red;
        }

        .layout.float .right {
            float: right;
            width: 300px;
            background-color: blue;
        }

        .layout.float .center {

            background-color: yellow;
        }
        </style>
        <article class="left-right-center">
            <div class="left"></div>
            <div class="right"></div>
            <div class="center">
                <h1>浮动解决方案</h1> 1.这是三栏布局中间部分 1.这是三栏布局中间部分
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
            </div>
        </article>
    </section>
```

####绝对定位解决方案
```js
     <!-- 绝对定位解决方案 -->
    <section class="layout absolute">
        <style>
        .layout.absolute .left-center-right>div {
            position: absolute;
        }

        .layout.absolute .left {
            left: 0;
            width: 300px;
            background-color: red;
        }

        .layout.absolute .center {
            left: 300px;
            right: 300px;
            background-color: yellow;
    
        }

        .layout.absolute .right {
            right: 0;
            width: 300px;
            background-color: blue;
        }
        </style>
        <article class="left-center-right">
            <div class="left"></div>
            <div class="center">
                <h1>绝对定位解决方案</h1> 1.这是三栏布局中间部分 1.这是三栏布局中间部分
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
            </div>
            <div class="right"></div>
        </article>
    </section>

```

####flexbox解决方案 

```js
     <!-- flexbox解决方案 -->
    <section class="layout flexbox">
        <style>
        .layout.flexbox {
            margin-top: 140px;
        }

        .layout.flexbox .left-center-right {
            display: flex;
        }

        .layout.flexbox .left {
            width: 300px;
            background-color: red;
        }

        .layout.flexbox .center {
            flex: 1;
            background-color: yellow;
        }

        .layout.flexbox .right {
            width: 300px;
            background-color: blue;
        }
        </style>
        <article class="left-center-right">
            <div class="left"></div>
            <div class="center">
                <h1>flexbox解决方案</h1> 1.这是三栏布局中间部分 1.这是三栏布局中间部分
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
            </div>
            <div class="right"></div>
        </article>
    </section>
```



####表格布局解决方案

```js
     <!-- 表格布局解决方案 -->
    <section class="layout table">
        <style>
        .layout.table .left-center-right {
            width: 100%;
            display: table;
            height: 100px;
        }

        .layout.table .left-center-right>div {
            display: table-cell;
        }

        .layout.table .left {
            width: 300px;
            background-color: red;
        }

        .layout.table .center {
            background-color: yellow;
        }

        .layout.table .right {
            width: 300px;
            background-color: blue;
        }
        </style>
        <article class="left-center-right">
            <div class="left"></div>
            <div class="center">
                <h1>table解决方案</h1> 1.这是三栏布局中间部分 1.这是三栏布局中间部分
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
            </div>
            <div class="right"></div>
        </article>
    </section>
```


####网格布局解决方案

```js
     <!-- 网格布局解决方案 -->
    <section class="layout grid">
        <style>
        .layout.grid .left-center-right {
            display: grid;
            width: 100%;
            grid-template-rows: 100px;
            grid-template-columns: 300px auto 300px;
        }

        .layout.grid .left {
            background-color: red;
        }

        .layout.grid .center {
            background-color: yellow;
        }

        .layout.grid .right {
            background-color: blue;
        }
        </style>
        <article class="left-center-right">
            <div class="left"></div>
            <div class="center">
                <h1>网格布局解决方案</h1> 1.这是三栏布局中间部分 1.这是三栏布局中间部分
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
                <p>增加高度</p>
            </div>
            <div class="right"></div>
        </article>
    </section>
```


###总结:
    
#####（1）五种方案的优缺点?
    * float:
        浮动脱离文档流,要处理好浮动
        兼容性好
    * position:
        布局脱离了文档流,下面的子元素也脱离了文档流,可使用性比较差
        快捷,不容易出问题
    * display:flex:
        IE8不支持flex
        解决了上述布局方式的不足出现的,比较完美的,移动端基本上是flex布局
    * display:table:
        table操作比较繁琐,对SEO不友好
        兼容性非常好,如果flex解决不了可以考虑使用表格布局
    * display:grid:
        代码量少,新技术
        
#####(2)如果中间高度不固定,那个还可以用?
    
    * float不能用，中间的内容被左侧挡住，因为撑开高度以后，左侧没有了遮挡物，就会流向左侧。 
    解决方案：创建BFC
    * absolute不能用
    * flex可以使用。
    * table-ceil可以使用。
    * grid不能用 
        
    
    
        
        