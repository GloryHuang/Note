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

//长轮询
{
    let ajax = function*() {
        yield new Promise((resolve, reject) => {


            //重写接口
            setTimeout(function() {
                resolve({ code: 1 })
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