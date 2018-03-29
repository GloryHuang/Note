###AngularJS

 * AngularJS是一款由Google公司开发维护的前端MVC框架，其克服了HTML在构建应用上的诸多不足，从而降低了开发成本提升了开发效率。
 
###特点
 
 * AngularJS是一个框架（诸多类库的集合）以数据和逻辑做为驱动（核心）,框架对开发的流程和模式做了约束，开发者遵照约束进行开发,更注重的实际的业务逻辑。

 
AngularJS特性：
  
 * 模块化
 * 双向数据绑定
 * 语义化标签
 * 依赖注入
 
####MVC
 
 * MVC是一种开发模式，由模型（Model）、视图（View）、控制器（Controller）3部分构成，采用这种开发模式为合理组织代码提供了方便、降低了代码间的耦合度、功能结构清晰可见。
 
   * 模型（Model）一般用来处理数据（读取/设置），一般指操作数据库。
   * 视图（View）一般用来展示数据，比如通过HTML展示。
   * 控制器（Controller）一般用做连接模型和视图的桥梁。
   
    ![](/assets/MVC.gif)
    
* MVC更多应用在后端开发程序里，后被引入到前端开发中，由于受到前端技术的限制便有了一些细节的调整，进而出现了很多MVC的衍生版（子集）如MVVM、MVW、MVP、MV*等。

###AngularJS结构

![](/assets/AngularJS结构.jpg)


###模块化
 
* 使用AngularJS构建应用（App）时是以模块化（Module）的方式组织的，即将整个应用划分成若干模块，每个模块都有各自的职责，最终组合成一个整体。

* 采用模块化的组织方式，可以最大程度的实现代码的复用，

####定义方式

 ```js
<!--为html标签添加ng-app表明整个文档都是应用-->
<!--ng-app属性都不可以赋值,但是要关联相应模块时必须赋值-->
<html lang="en" ng-app="App">
```

####定义模块
 * AngularJS提供了一个全局对象angular，在此全局对象下存在若干的方法，其中angular.module()方法用来定义一个模块。
 
 ```js
//通过module方法定义模块
//需要传递两个参数,第1个表示模块的名称
//第2个表示此模块依赖的其它模块
var App=angular.module('App',{});
```

####定义控制器

 * 控制器（Controller）作为连接模型（Model）和视图（View）的桥梁存在，所以当我们定义好了控制器以后也就定义好了模型和视图。
 
 ```js
 //APP是一个模块实例对象
 //通过这个实例对象定义控制器
 //需要两个参数,第1个参数表示控制器名称
 //第2个参数是一个数组,这个数组除最后1个单元是函数外
 //其余都是字符串
 app.controller('StudentController',[$scope,function($scope){
          //模型(Model)
          $scope.stus=[
             {name:'张三',sex:'男',age:20},
             {name:'李四',sex:'男',age:20}，
             {name:'王五',sex:'男',age:20}，
             {name:'赵四',sex:'男',age:20}
          ];
 }])
 ```
 
 * 模型（Model）数据是要展示到视图（View）上的，所以需要将控制器（Controller）关联到视图（View）上，通过为HTML标签添加ng-controller属性并赋值相应的控制器（Controller）的名称，就确立了关联关系。

```js
        <table ng-controller="StudentController">
		<thead>
			<tr>
				<th>姓名</th>
				<th>性别</th>
				<th>年龄</th>
			</tr>
		</thead>
		<tbody>
			<tr ng-repeat="stu in stus">
				<td>{{stu .name}}</td>
				<td>{{stu .sex}}</td>
				<td>{{stu .age}}</td>
			</tr>
		</tbody>
	</table>
```

###指令

 * HTML在构建应用（App）时存在诸多不足之处，AngularJS通过扩展一系列的HTML属性或标签来弥补这些缺陷，所谓指令就是AngularJS自定义的HTML属性或标签，这些指令都是以ng-做为前缀的，例如ng-app、ng-controller、ng-repeat等。
 
####内置指令

* ng-app 指定应用根元素，至少有一个元素指定了此属性。
* ng-controller 指定控制器
* ng-show控制元素是否显示，true显示、false不显示
* ng-hide控制元素是否隐藏，true隐藏、false不隐藏
* ng-if控制元素是否“存在”，true存在、false不存在
* ng-src增强图片路径
* ng-href增强地址
* ng-class控制类名
* ng-include引入模板
* ng-disabled表单禁用
* ng-readonly表单只读
* ng-checked单/复选框表单选中
* ng-selected下拉框表单选中

####自定义指令
 
 * AngularJS允许根据实际业务需要自定义指令，通过angular全局对象下的directive方法实现。
 
 ```js
  var App = angular.module('App', []);

    //通过模块实例化对象的directive方法可以自定义指令
    App.directive('tag', function() {

        //返回一个对象,这个对象就是自定义指令相关内容
        return {
        
            //自定义指令的类型 E、A、C、M
            //E element
            //A attribute
            //C class
            //M mark replace 必须为true
            restrict: 'ECMA', //E 可做标签使用 A 可做属性使用 C 可做类使用
            
            //指令模板
            //template:'<ul><li>首页</li><li>列表</li></ul>',
            templateUrl: 'list.html',
            
            //是否替换原有标签
            replace:true
        }
    });
 
 ```
###数据绑定