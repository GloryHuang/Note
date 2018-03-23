###雅虎14条优化规则

* 减少 HTTP 请求次数
    
  * CSS Sprites 是更好的方法。它可以组合页面中的图片到单个文件中，并使用 CSS 的 background-image 和 background-position 属性来实现所需的部分图片。
  
  * Inline images 使用 data: URL scheme 来在页面中内嵌图片。这将增大 HTML 文件的大小。组合 inline images 到你的（缓存）样式表是既能较少 HTTP 请求， 又能避免加大 HTML 文件大小的方法。 
  
  * Combined files 通过组合多个脚本文件到单一文件来减少 HTTP 请求次数。当页面之间脚本和样式表变化 很大时，该方式将遇到很大的挑战，但如果做到的话，将能加快响应时间
  
*  使用 CDN(Content Delivery Network, 内容分发网络 ) 

* 增加 Expires Header 

* 压缩页面元素 

* 把样式表放在头上 

* 把脚本文件放在底部 

* 避免 CSS 表达式 

* 把 JavaScript 和 CSS 放到外部文件中 

* 减少 DNS 查询次数 

* 最小化 JavaScript代码 

 * 最小化 JavaScript 代码指在 JS 代码中删除不必要的字符，从而降低下载时间。 
 
 
* 避免重定向 

  * 重定向的主要问题是降低了 用户体验。 一种最耗费资源、经常发生而很容易被忽视的重定向是 URL 的最后缺少/，如访 问 http://astrology.yahoo.com/astrology 将被重定向到 http://astrology.yahoo.com/astrology/。在 Apache 下，可以通过 Alias，mod_rewrite 或 DirectorySlash 等方式来解决该问题。 
  
  
* 删除重复的脚本文件
 
  * 一个避免重复的脚本文件的方式是使用模板系统来建立脚本管理模块。 除了防止 重复的脚本文件外，该模块还可以实现依赖性检查和增加版本号到脚本文件名 中，从而实现超长的过期时间。