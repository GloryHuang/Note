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