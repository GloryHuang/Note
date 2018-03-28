###HTML5

* < !DOCTYPE html>
* 语义化标签




###新语义化标签

 * < nav> 表示导航
 * < header> 表示页眉
 * < footer> 表示页脚
 * < section> 表示区块
 * < article> 表示文章 如文章、评论、帖子、博客
 * < aside> 表示侧边栏 如文章的侧栏
 * < figure> 表示媒介内容分组
 * < mark> 表示标记
 * < progress> 表示进度
 * < time> 表示日期
 
#####尽量避免全局使用header、footer、aside等语义标签


####兼容处理

 *  在不支持HTML5新标签的浏览器里，会将这些新的标签解析成行内元素(inline)对待，所以我们只需要将其转换成块元素(block)即可使用，但是在IE9版本以下，并不能正常解析这些新标签，但是却可以识别通过document.createElement('tagName')创建的自定义标签，于是我们的解决方案就是将HTML5的新标签全部通过document.createElement('tagName')来创建一遍，这样IE低版本也能正常解析HTML5新标签了
 
 * 在实际开发中我们更多采用的是通过检测IE浏览器的版本来加载三方的一个JS库来解决兼容问题

```js
    <!-- 条件注释 只有ie能够识别 -->
    <!--[if lte ie 8]>
        <script src="html5shiv.min.js"></script>
    <![endif]-->
```
 