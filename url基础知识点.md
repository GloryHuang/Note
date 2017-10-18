####URL基础知识点
    protocol:表示url采用的什么协议
    slashes:表示是否有斜线
    host：表示主机
    post:端口（默认80端口不显示）
    hostname:主机名称
    hash:指的是#号后的内容包含#<br>（锚点）
    search：指的是？后#前的内容，包含？（查询字符串参数）
    query：指的是search不包含？的内容(给http服务器发送数据)
    pathname:指的是路径名称，一般指主域名之后的内容（'/返回自己的路径名/'）
    path：路径
    href：代表未解析的url地址
            参数可选参数1设置为true,对象中query解析出，
            可选参数2设置为true,对象中host正确解析,pathname正确解!!!协议protocal未明确。
  
    url.parse(urlString,bool,bool): 将定位符解析成对象,
    url.format(urlObj): 将对象解析成定位符（也就是URL）
    url.resolve(from, to):将一个基本URL和指定超链接目标URL合并


####绝对URI
    http://user:pass@www.example.com:80/dir/index.html?uid=1#ch1
    协议   登录信息  服务器地址     端口  文件路径    查询字符串 片段标示符

    
    URI ：Uniform Resource Identifier，统一资源标识符；
    URL：Uniform Resource Locator，统一资源定位符；
    URN：Uniform Resource Name，统一资源名称。


    其中，URL,URN是URI的子集。


    url.parse(urlString,bool,bool): 将定位符解析成对象,识别无协议的url


        第二个参数决定query部分以字符串返回还是以对象形式返回，默认为字符串返回即第二个参数默认为false;
        第三个参数表示在没有完整协议串的时候（即无http:/https:）的时候‘//’之后的字符如何解释，若为false即将‘//’之后的当做路径解释，若为true则会将‘//’与‘/’之间的字符串解释为主机