###Generator异步编程的解决方式

 * 基本概念
 * next函数的用法
 * yield*的语法

####Generator的基本方式

```js
//Generator的基本方式
{
    let tell = function*() {
        yield 'a';
        yield 'b';
        return 'c'
    };

    let k = tell();

    console.log(k.next());
    console.log(k.next());
    console.log(k.next());
    console.log(k.next());
}



//object对象没有for....of...不能用,除非部署了iterator
{
    let obj = {};
    obj[Symbol.iterator] = function*() {
        yield 1;
        yield 2;
        yield 3;
    }
    for (let value of obj) {
        console.log('value', value);
    }
}



{
    let state = function*() {
        while (1) {
            yield 'A';
            yield 'B';
            yield 'C';
        }
    }
    let status = state();
    console.log('status', status.next());
    console.log('status', status.next());
    console.log('status', status.next());
    console.log('status', status.next());
    console.log('status', status.next());
    console.log('status', status.next());
}



// {
//     let state = async function() {
//         while (1) {
//             await 'A';
//             await 'B';
//             await 'C';
//         }
//     }
//     let status = state();
//     console.log('status', status.next());
//     console.log('status', status.next());
//     console.log('status', status.next());
//     console.log('status', status.next());
//     console.log('status', status.next());
//     console.log('status', status.next());
// }

```



####Demo
```js
//抽奖次数限制
{

    //抽奖次数限制
    let draw = function(count) {
        //具体抽奖逻辑

        console.info(`剩余${count}次`);
    }

    //执行具体的抽奖逻辑
    let residue = function*(count) {
        while (count > 0) {
            count--;
            yield draw(count);
        }
    }


    //执行抽奖环节
    let star = residue(5);
    let btn = document.createElement('button');
    btn.id = 'start';
    btn.textContent = '抽奖';
    document.body.appendChild(btn);
    document.getElementById('start').addEventListener('click', function() {
        star.next();
    }, false);
}

```
####长轮询

```js
//长轮询
{
    let ajax = function*() {
        yield new Promise((resolve, reject) => {


            //重写接口
            setTimeout(function() {
                resolve({ code: 0 })
            }, 200);




        });
    }


    let pull = function() {
        let generator = ajax();
        let step = generator.next();
        step.value.then(function(d) {
            if (d.code != 0) {
                setTimeout(function() {
                    console.info('wait');
                    pull();
                }, 1000);
            } else {
                console.info(d);
            }
        });
    }

    pull();
}
```