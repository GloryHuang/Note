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

#### 绝对定位解决方案
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

####

```js

```



####

```js

```


####

```js

```