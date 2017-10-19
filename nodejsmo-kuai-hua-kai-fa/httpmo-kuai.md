####Http模块

####Http性能测试

    1.如果没有安装Apache的话，首先要安装Apache
    2.window系统到apache安装目录的bin文件，然后命令行执行ab -n1000 -c10 http://localhost:2015/
    
    3.找到 apache的bin目录 ab -n1000 -c10 http://www.imooc.com/ 输入
    
        -n1000 总请求数1000 默认值1
        -c10 并发数10  默认值1
        -t 测试的时间
        -p post数据文件1.如果没有安装Apache的话，首先要安装Apache

  