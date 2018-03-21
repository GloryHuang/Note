###Ajax

####Get

```js
	// ajax get 五部曲
	function ajax_get(url,data) {
	// 异步对象
	var ajax = new XMLHttpRequest();

	// url 方法
	// 如果是get发送数据 发送的格式为 xxx.php?name=jack&age=18
	// 所以 这里 需要拼接 url
	if (data) {
		// 如果有值 需要拼接字符串 
		// 拼接为xxx.php?name=jack&age=18
		url+='?';
		url+=data;
	}else{
	}

	ajax.open('get',url);
	// 发送
	ajax.send();

	// 注册事件
	ajax.onreadystatechange = function () {
		// 在事件中 获取数据 并修改界面显示
		if (ajax.readyState==4&& ajax.status==200) {
			console.log(ajax.responseText);
		}
	 }
    }
```


####Post

```js
	// ajax_post五部曲
	function ajax_post(url,data) {
	// 异步对象
	var ajax = new XMLHttpRequest();

	// url 方法
	ajax.open('post',url);

	// 设置 请求报文 
	ajax.setRequestHeader("Content-type","application/x-www-form-urlencoded");

	// 发送
	if (data) {
		// 如果 有值 post请求 是在 send中 发送给服务器
		ajax.send(data);
	}else{
		ajax.send();
	}
	

	// 注册事件
	ajax.onreadystatechange = function () {
		// 在事件中 获取数据 并修改界面显示
		if (ajax.readyState==4&&ajax.status==200) {
			console.log(ajax.responseText);
		}
	}

  }
```

####Post和Get封装

```js
// 将 get 跟post 封装到一起
/*
	参数1:url
	参数2:数据
	参数3:请求的方法
	参数4:数据成功获取以后 调用的方法
*/
function ajax_tool(url,data,method,success) {
	// 异步对象
	var ajax = new XMLHttpRequest();

	// get 跟post  需要分别写不同的代码
	if (method=='get') {
		// get请求
		if (data) {
			// 如果有值
			url+='?';
			url+=data;
		}else{

		}
		// 设置 方法 以及 url
		ajax.open(method,url);

		// send即可
		ajax.send();
	}else{
		// post请求
		// post请求 url 是不需要改变
		ajax.open(method,url);

		// 需要设置请求报文
		ajax.setRequestHeader("Content-type","application/x-www-form-urlencoded");

		// 判断data send发送数据
		if (data) {
			// 如果有值 从send发送
			ajax.send(data);
		}else{
			// 木有值 直接发送即可
			ajax.send();
		}
	}

	// 注册事件
	ajax.onreadystatechange = function () {
		// 在事件中 获取数据 并修改界面显示
		if (ajax.readyState==4&&ajax.status==200) {
			// console.log(ajax.responseText);

			// 将 数据 让 外面可以使用
			// return ajax.responseText;

			// 当 onreadystatechange 调用时 说明 数据回来了
			// ajax.responseText;

			// 如果说 外面可以传入一个 function 作为参数 success
			success(ajax.responseText);
		}
	}

 }

```

###进阶版

```js

    function ajax_tools_pro(obj) {

    var ajax = new XMLHttpRequest();

    if (obj.method == 'get') {

        if (obj.data) {
            obj.url += '?';
            obj.url += obj.data;
        } else {

        }
        ajax.open(obj.method, obj.url);
        ajax.send();
    } else {
        ajax.open(obj.method, obj.url);
        ajax.setRequestHeader("Content-type", "application/x-www-form-urlencoded");

        if (obj.data) {
            ajax.send(obj.data);
        } else {
            ajax.send();
        }
    }


    ajax.onreadystatechange = function () {

        if (ajax.readyState == 4 && ajax.status == 200) {
            obj.success(ajax.responseText);
        }


    }

}



```

###参数格式化

```js

	function ajax(option) {
  // 创建对象
  var xmlRequest ;
  if (XMLHttpRequest) {
      xmlRequest = new XMLHttpRequest();
  }else{
      xmlRequest = new ActiveXObject("Microsoft.XMLHTTP");

  }

  // 格式化传入的数据为name=fox&age=18这样的格式
  var formatStr = "";
  for(var item in option.data){
      // 获取属性名,属性值,进行拼接
      formatStr+=item;// 属性名
      formatStr+="=";//等号
      formatStr+=option.data[item];//属性值
      formatStr+="&";//分隔符
  }

  // 去除最后一个&
  formatStr = formatStr.slice(0,-1);

  // open方法 如果是get方法,那么url之后需要添加数据
  if(option.method == "get"){
      option.url = option.url+"?"+formatStr;
      option.data = null;
  }
  // 调用open方法
  xmlRequest.open(option.method,option.url)

  // 如果是post设置HTTP协议头
  if (option.method=="post") {
      xmlRequest.setRequestHeader("Content-type","application/x-www-form-urlencoded");
  }

  // send方法 这里的data已经是修改过的,如果使用的是get方法,那么data为null
      xmlRequest.send(option.data);

  // 判断状态改变,调用方法
  xmlRequest.onreadystatechange = function () {
  // 这步为判断服务器是否正确响应
  if (xhr.readyState == 4 && xhr.status == 200) {
             option.success(这里的数据是ajax获取的);  
     } 
  };
}





```