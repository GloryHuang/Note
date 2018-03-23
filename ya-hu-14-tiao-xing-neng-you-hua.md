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