###构建工具

 * 构建工具是指通过简单配置就可以帮我们实现合并、压缩、校验、预处理等一系列任务的软件工具
 
 * 常见的构建工具包括：Grunt、Gulp、F.I.S（百度出品）、webpack 

###Gulp

 * Gulp是基于Nodejs开发的一个构建工具，借助gulp插件可以实现不同的构建任务，以其简洁的配置和卓越的性能成为目前主流的构建工具。
 

####Gulp的使用

 * 全局安装 npm install -g gulp

 * 本地安装gulp 
 
   * 进入项目根目录执行npm install gulp --save-dev（添加--save-dev会在package.json记录依赖关系）。
  
  
 *  任务清单
 
  * 在项目根目录中创建gulpfile.js（这是一个配置文件）
  

   ![](/assets/gulp.png)

 * 定义任务
 
  * 在gulpfile.js定义构建任务，如压缩、合并，Gulp自身并不执行任何任务，是通过调用具体插件来完成的。
  
  * 以编译LESS为例，安装npm install gulp-less，如下图定义任务
 
  ![](/assets/task.png)


 * 执行任务
   
   * 输入命令 gulp less LESS文件便会编译成CSS了
   
   
   ![](/assets/gulps.png)
  
  
####Gulp工作原理

* 通过不同的插件实现构建任务，Gulp只是按着配置文件调用执行了这些插件。

 ![](/assets/gulpdef.png)
 
####Gulp API 

* Gulp是基于NodeJS的，通过require可以引入一个NodeJS的包（模块），其作用类似于浏览器中的script标签引入资源，被引入的包存放在node_modules目录下。

* 引入gulp包（模块）后返回一个对象，习惯赋值给变量gulp，通过该对象提供的方法（API）完成任务的配置。


 * gulp.task() 定义各种不同的任务，如下图有两个参数

  ![](/assets/task1.png)
  
  * 不同任务间存在依赖关系时，可以指定依赖
  
  
   ![](/assets/task3.png)
   
 * gulp.src() 需要构建资源的路径，字符串或数组（可以正则方式书写）
 
   ![](/assets/task4.png)
   
 * gulp.pipe() 管道，将需要构建的资源“输送”给插件。
  
   ![](/assets/task5.png)
   
 * gulp.dest() 构建任务完成后资源存放的路径（会自动创建）
 
   ![](/assets/task6.png)
  
 * gulp.watch() 
 
 
####常用Gulp插件

 * gulp-less 编译LESS文件
 * gulp-autoprefixer 添加CSS私有前缀
 * gulp-cssmin 压缩CSS
 * gulp-rname重命名
 * gulp-imagemin 图片压缩
 * gulp-uglify 压缩Javascript
 * gulp-concat 合并
 * gulp-htmlmin 压缩HTML
 * gulp-rev 添加版本号
 * gulp-rev-collector 内容替换
 * gulp-useref
 * gulp-if
 
 
####实例
```js
//引入本地安装的gulp
var myGup = require('gulp');

//引入解析less的插件
var less = require('gulp-less');

//引入压缩css的插件
var cssmin = require('gulp-cssmin');

//引入压缩image的插件
var imgmin = require('gulp-imagemin');

//引入压缩JS的插件
var jsurg = require('gulp-uglify');

//引入合并JS文件的插件
var jscat = require('gulp-concat');

//返回值gulp是一个对象,借助此对象可以实现任务清单的定制
//通过一系列的方法实现

//定义任务(将less转成css)
myGup.task('less', function() {

    //借助gulp.src来指定less文件位置
    myGup.src('./public/less/*.less')
    
        //借助于gulp的插件实现less转css的操作
        .pipe(less())
        .pipe(cssmin())
        
        //通过gulp.dest进行存储
        .pipe(myGup.dest('./release/public/css'));
});

//压缩CSS代码
myGup.task('csmin', function() {
    myGup.src('./release/public/*.css')
        .pipe(cssmin())
        .pipe(myGup.dest('./min/public/css'));

});

//处理图片(压缩图片)
myGup.task('image', function() {
    myGup.src('./public/images/*')
        //myGup.src('./public/images/**')不管当前文件夹下有多少个文件夹都会被匹配
        .pipe(imgmin())
        .pipe(myGup.dest('./release/public/images'));
});

//丑化JS代码(压缩JS代码)
myGup.task('jsug', function() {
    myGup.src('./scripts/*.js')
        .pipe(jscat('all.js'))
        .pipe(jsurg())
        .pipe(myGup.dest('./release/script'))

});
```


