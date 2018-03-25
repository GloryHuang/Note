###Webpack

####webpack介绍

- webpack是一个资源的打包工具，分为1.0和2.0版本，可以将 .js,  .css , image等静态资源当做一个模块来进行打包，那么每一种模块都是有一个对应的 loader来实现
- webpack 1.0版本官网：https://webpack.github.io/docs/usage.html
- webpack 2.0版本官网：https://webpack.js.org/

####node环境的安装

* webpack是基于nodejs运行的，所以在安装webpack之前必须先安装nodejs环境,安装步骤如下

  1、去 https://nodejs.org/en/ 中下载当前操作系统匹配的版本,windows下软件名称通常叫做 node.exe
  
  2、双击node.exe一路安装好，由于node.exe已经包含了npm工具，所以npm也能正常使用了
      
  3、由于直接使用npm install 安装第三方包是去国外网站上下载，有可能会被墙而安装失败，所以我们要将下载源切换到国内淘宝上因此需要利用 npm install nrm -g安装一个全局的nrm
  
  4、安装好nrm以后，在cmd命令面板中输入： nrm use taobao 将下载源切换到淘宝，可以使用 nrm ls 查看当前使用的下载源
  
  5、也可安装淘宝提供的类似于npm的工具 cnpm来替代npm安装node包,安装包命令和npm一样，安装cnpm命令： npm install cnpm -g
  
####webpack的安装

 * 第一种安装方式： 
        在cmd命令行面板中 执行： npm install webpack@1.14.0 -g 将webpack1.14.0版本安装为全局就能够在cmd命令行面板中使用webpack指令了   
        
 * 第二种安装方式： 
        在cmd命令行面板中 执行： cnpm install webpack@1.14.0 -g 将webpack1.14.0版本安装为全局就能够在cmd命令行面板中使用webpack指令了 
        
           
####webpack常用指令和webpack.config.js配置文件   

* webpack常用指令

```js
      webpack 入口文件.js 输出文件.js
      webpack         // 最基本的启动webpack的方法，默认查找名称为 webpack.config.js文件
      webpack --config webpack.config.js    // 指定配置文件    
	  
      webpack -p      // 对打包后的文件进行压缩
      webpack -d      // 提供source map，方便调式代码
```
* webpack.config.js配置文件的作用

 * 如果只在cmd命令面板中输入 webpack指令，后面不跟任何参数的话，则默认查找的是 webpack.config.js文件，在这个文件中可以配置入口文件，输出文件以及相关loader和插件等,以增强webpack的功能
 


####一个常用webpack1.0版本的webpack.config.js文件结构：

```js

  // 导入html-webpack-plugin 包，用来根据模板自动生成index.html
  var htmlwp = require('html-webpack-plugin');

  module.exports={	
  
	entry:'./src/main.js', // 1.0 定义打包的入口文件路径
	output:{
		path:'./dist',   //打包以后的文件存放目录
		filename:'build.js'  // 打包以后生成的文件名称
	},
	module:{
		loaders:[
			{
				// 将当前项目中所有的.js文件都要进行es6转es5操作，node_moudels除外
				test:/\.js$/,   //表示当前要打包的文件的后缀正则表达式
				// loader:'babel-loader?presets[]=es2015', //如果写到这里，将来在打包.vue文件的时候会报错，表示先利用css-loader解析.css文件，再调用style-loader打包
				loader:'babel-loader',
				exclude:/node_modules/  //node_modules中的所有.js文件不去转换，提高打包性能
			}			
		]
	},
	babel:{
		 presets: ['es2015'],  //表示es6转es5
		 plugins: ['transform-runtime']  //这句代码就是为了解决打包.vue文件不报错
	},
	plugins:[
        new htmlwp({
          title: '首页',  //生成的页面标题
          filename: 'index.html', //webpack-dev-server在内存中生成的文件名称，自动将build注入到这个页面底部，才能实现自动刷新功能
          template: 'index1.html' //根据index1.html这个模板来生成(这个文件请你自己生成)
        })
    ]
}
    
```

###webpack中loader介绍

 * webpack本身不支持css,less,sass,js,image等相关资源的打包工作的，它仅仅提供了一个基础的框架，在这个框架上借助于相关的loader才可以实现css,less,sass,js,image等相关资源的打包工作
 
####webpack相关配置

* 在使用loader之前需要在当前项目目录下打开cmd命令面板，输入: npm init 初始化一个 package.json文件来存放相关的 loader包

####打包css资源

* webpack中使用css-loader和style-loader这两个loader来处理css资源的打包工作，所以使用前必须在项目中先安装这两个包:
npm i css-loader style-loader --save-dev

* 在webpack.config.js中配置这两个loader

![](/assets/d4-11.png)

* 在项目中建立一个site.css文件，并且在main.js中导入

![](/assets/d4-12.png)

* 在cmd中执行webpack命令

![](/assets/d4-13.png)

###打包sass资源

* webpack中使用sass-loader，css-loader，style-loader来处理.scss文件的打包工作,而sass-loader需要依赖于node-sass所以使用前必须在项目中先安装这些包，
并且node-sass的某些文件下载是需要去google上的，为了防止被墙而导致安装失败，所以建议使用cnpm来安装：
cnpm install node-sass sass-loader css-loader style-loader --save-dev


 * 在webpack.config.js中配置这两个loader
 
 ![](/assets/d4-14.png)

 * 在项目中建立一个site1.scss文件，并且在main.js中导入
 
 ![](/assets/d4-15.png)

 * 在cmd中执行webpack命令
 
 * 在项目根目录下打开cmd命令面板，输入：webpack  回车即可打包完成
  此时检查build.js文件的内容，sass语法是变成了css语法表示打包成功
  
###打包less资源

* 需要安装的node包有：

  * css-loader：  编译css
  * style-loader：编译css
  * less-loader： 编译less
  * less:  less-loader的依赖包
  
	
* 在项目根目录下打开cmd命令面板，输入：

   * npm install less less-loader style-loader css-loader --save-dev 回车即可完成安装
 