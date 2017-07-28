```js
     /*
        * html5新增了一个DOMContentLoaded事件，兼容IE9，
        * 这个事件会在DOM解析完毕后触发，
        * 通常这个事件要比onload快很多，
        * 但是也有很少的例外。
        * 备注：如果发生了例外，DOMContentLoaded事件和onload事件触发的间隔时间相差不会很大，
        * 所以可以认为DOMContentLoaded 比 onload要快，只监听DOMContentLoaded即可。
        * */

        window.onload = function() {
            var spans = document.querySelectorAll( 'span' );
            console.log( spans, 'onload' );
        };

        document.addEventListener( 'DOMContentLoaded', function() {
            var spans = document.querySelectorAll( 'span' );
            console.log( spans, 'DOMContentLoaded');
        } );

```

#####DOMContentLoaded事件兼容写法
```js
          /*
        * 在IE8中，所有的元素都有一个onreadystatechange事件，
        * 可以利用它代替DOMContentLoaded事件。
        * */

        window.onload = function() {
            var spans = document.querySelectorAll( 'span' );
            console.log( spans, 'onload' );
        };

        // IE8模拟DOMContentLoaded事件的方式
        document.attachEvent( 'onreadystatechange', function() {
            if ( document.readyState === 'complete' ) {
                var spans = document.querySelectorAll( 'span' );
                console.log( spans, 'DOMContentLoaded');
            }
        } );

```
