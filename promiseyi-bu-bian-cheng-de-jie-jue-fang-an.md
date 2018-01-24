####Promise异步编程的解决方案


####ES5回调函数
```js
{
    //ES5回调函数
    //基本定义
    let ajax = function(callback) {
        console.log('执行');
        setTimeout(function() {
            callback && callback.call();
        }, 1000);
    };

    ajax(function() {
        console.log('timeout1');
    })

}

```


####ES6中的回调函数

    * resolve:执行下一步的操作
    * reject:中断当前的操作

```js
{
    //ES6回调函数
    let ajax = function() {
        console.log('执行2');
        return new Promise(function(resolve, reject) {
            setTimeout(function() {
                resolve();
            }, 1000)
        })
    };

    //为什么要.then()?
    //ajax()方法返回了一个Promise实例,而Promise有.then()方法表示执行下一步,
    //
    ajax().then(function() {
        console.log('promise', 'timeout2');
    })

}

{

    let ajax = function() {
        console.log('执行3');
        return new Promise(function(resolve, reject) {
            setTimeout(function() {
                resolve();
            }, 1000)
        })
    };


    ajax()
        .then(function() {
            return new Promise(function(resolve, reject) {
                setTimeout(function() {
                    resolve();
                }, 2000)
            })
        })
        .then(function() {
            console.log('timeout3')
        })
}
```
####捕获错误

```js
//捕获错误
{
    let ajax = function(num) {
        console.log('执行4');
        return new Promise(function(resolve, reject) {
            if (num > 5) {
                resolve();
            } else {
                throw new Error('出错了');
            }
        })
    }

    ajax(6).then(function() {
        console.log('log', 6);
    }).catch(function(err) {
        console.log('catch', err);
    });

    ajax(3).then(function() {
        console.log('log', 3);
    }).catch(function(err) {
        console.log('error', err);
    })
}
```


####Promise的高级方法

```js
//Promise的高级方法
//所有的图片加载完成再添加到页面
{
    function lodImg(src) {
        return new Promise((resolve, reject) => {
            let img = document.createElement('img');
            img.src = src;
            img.onload = function() {
                resolve(img);
            }
            img.onerror = function(err) {
                reject(err);
            }
        })
    }



    function showImgs(imgs) {
        imgs.forEach(function(img) {
            document.body.appendChild(img);
        })
    }


    Promise.all([
        lodImg('https://gloryhuang.github.io/XiaoMi/img/star2.png'),
        lodImg('https://gloryhuang.github.io/XiaoMi/img/item-2.jpg'),
        lodImg('https://gloryhuang.github.io/XiaoMi/img/item-4.jpg')
    ]).then(showImgs);
}



//
{
    //有一个图片加载完成就添加到页面
    function lodImg(src) {
        return new Promise((resolve, reject) => {
            let img = document.createElement('img');
            img.src = src;
            img.onload = function() {
                resolve(img);
            }
            img.onerror = function(err) {
                reject(err);
            }
        })
    }



    function showImgs(img) {
        let p = document.createElement('p');
        p.appendChild(img);
        document.body.appendChild(p);
    }


    Promise.race([
        lodImg('https://gloryhuang.github.io/XiaoMi/img/star2.png'),
        lodImg('https://gloryhuang.github.io/XiaoMi/img/item-2.jpg'),
        lodImg('https://gloryhuang.github.io/XiaoMi/img/item-4.jpg')
    ]).then(showImgs);

}

```