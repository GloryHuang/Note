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

