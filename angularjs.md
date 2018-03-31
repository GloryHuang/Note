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

 * AngularJS是以数据做为驱动的MVC框架，所有模型（Model）里的数据经由控制器（Controller）展示到视图（View）中。

 * 所谓数据绑定指的就是将模型（Model）中的数据与相应的视图（View）进行关联，分为**单向绑定**和**双向绑定**两种方式。

####单向绑定

 * 单向数据绑定是指将模型（Model）数据，按着写好的视图（View）模板生成HTML标签，然后追加到DOM中显示
 
  ![](/assets/one-way Data Binding.png)
  
####双向绑定

 * 双向绑定则可以实现模型（Model）数据和视图（View）模板的双向传递
 
 ![](/assets/Two Way  Data Binding.png)
  
####相关指令

* 在AngularJS中通过“{ { } }”和ng-bind指令来实现模型（Model）数据向视图模板（View）的绑定，模型数据通过一个内置服务$scope来提供，这个$scope是一个空对象，通过为这个对象添加属性或者方法便可以在相应的视图(View)模板里被访问。

* ng-cloak

 * 注：“{ { } }”是ng-bind的简写形式，其区别在于通过“{ { } }”绑定数据时会有“闪烁”现象，添加ng-cloak也可以解决“闪烁”现象，通过ng-bind-template可以绑定多个数据。

   ```html
    <ul ng-controller="DemoController">
        <li ng-bind="name"></li>
        <li ng-cloak>{{name}}{{age}}</li>
        <li ng-bind-template="{{name}}{{age}}"></li>
    </ul>
 
   ```

* ng-model
 
 * 通过为表单元素添加ng-model指令实现视图（View）模板向模型（Model）数据的绑定。
 
   ```html
   <div ng-controller="MyController">
        <!-- 要实现数据从视图向模型传递需要借助于表单元素 -->
        <input type="text" ng-model="msg">
        <button ng-click="show()">显示</button>
        <div>{{msg}}</div>
        ng-bind:<span ng-bind="msg"></span>
    </div>
    <script src="lib/angular.min.js"></script>
   ```
   ```js
    var app = angular.module('App', []);

    app.controller('MyController', ['$scope', function($scope) {

        //$scope Model
        $scope.show = function() {
            alert($scope.msg);
        }
    }])
   
   ```
   
* ng-init

 * 通过ng-init可以初始化模型（Model）也就是$scope。
 
   ```html
      <div ng-controller="MyAppController">
        <div ng-init="msg='Hello World!';
        age=10;sex='Man'" ng-cloak>
            <h1>{{msg}}</h1>
            <h1>{{age}}</h1>
            <h1>{{sex}}</h1>
        </div>
    </div>
   ```
   ```js
    var app = angular.module('App', []);
    app.controller('MyAppController', ['$scope', function($scope) {
        // $scope.msg = "";
        $scope.msg = "new World";
        $scope.age = "12";
        $scope.age = "woman";
    }])
    </script>
   ```
   
* ng-事件名

   * AngularJS对事件也进行了扩展，无需显式的获取DOM元素便可以添加事件，易用性变的更强。通过在原有事件名称基础上添加ng-做为前缀，然后以属性的形式添加到相应的HTML标签上即可。如ng-click、ng-dblclick、ng-blur等   
   
   ```html
     <div ng-controller="MyController">
        <ul>
            <li ng-click="click()">这里是ng-click事件</li>
            <li ng-dblclick="dbclick()">这里是dbclick事件</li>
            <li>
                <input type="text" value="Hello World!" ng-focus="focus()">
            </li>
        </ul>
        <div class="box" ng-mouseenter="enter()" ng-mouseleave="leav()">
        </div>
    </div>
   ```
   
   ```js
   var　 app = angular.module('MyApp', []);

   app.controller('MyController', ['$scope', function($scope) {
             $scope.click = function() {
                    alert('这里是ng-click事件');
                  }
            $scope.dbclick = function() {
                    alert('这里是dbclick事件');
                  }
            $scope.focus = function() {
                    alert('这里是fouce事件');
                  }
            $scope.enter = function() {
                    console.log('鼠标移入!')
                  }
            $scope.leav = function() {
                    console.log('鼠标移出!')
                  }
      }]);
   ```
   
* ng-repeat
 
  * 通过ng-repeat可以将数组或对象数据迭代到视图模板中，ng-switch、on、ng-switch-when可以对数据进行筛选。
  
     ```html
    <body ng-app="MyApp">
    <div ng-controller="MyController">
        <ul ng-repeat="starts in start">
            <li>{{starts.name}}</li>
            <li>{{starts.age}}</li>
            <li>{{starts.gender}}</li>
        </ul>
        <ul>
            <li ng-repeat="item in items" ng-switch on="item">
                <span ng-switch-when="CSS">{{item}}</span>
            </li>
        </ul>
    </div>
  
    </body>
    ```
  
  
     ```js
    App.controller('MyController', ['$scope', function($scope) {
        $scope.start = [{
            name: '张三',
            age: 18,
            gender: 'Man'
        }, {
            name: '李四',
            age: 19,
            gender: 'Woman'
        }, {
            name: '王老五',
            age: 20,
            gender: 'Man'
        }, ];

        $scope.items = ['Html', 'CSS', 'JavaScript','CSS1'];
    }])

    ```
    
###作用域

 * 通常AngularJS中应用（App）是由若干个视图（View）组合成而成的，而视图（View）又都是HTML元素，并且HTML元素是可以互相嵌套的，另一方面视图都隶属于某个控制器（Controller），进而控制器之间也必然会产生嵌套关系。
 * 每个控制器（Controller）又都对应一个模型（Model）也就是$scope对象，不同层级控制器（Controller）下的$scope便产生了作用域。

####根作用域

 * 一个AngularJS的应用（App）在启动时会自动创建一个根作用域$rootScope，这个根作用域在整个应用范围（ng-app所在标签以内）都是可以被访问到的。
 
 ```html
 <!--指定一个普通的DIV为应用的根元素,这个根元素对应的便是$rootScope-->
 <!--通过ng-init为$rootScope添加数据-->
 <div ng-arr="App" ng-init=name="zhangsang;age=10">
      <span>{{age}}{{name}}</span>
 ```
 
####子作用域

 * 通过ng-controller指令可以创建一个子作用域，新建的作用域可以访问其父作用域的数据。
 

###过滤器

 *  在AngularJS中使用过滤器格式化展示数据，在“{ { } }”中使用“|”来调用过滤器，使用“:”传递参数
 
####内置过滤器

* currency将数值格式化为货币格式

* date日期格式化,年(y)、月(M)、日(d)、星期(EEEE/EEE)、时(H/h)、分(m)、秒(s)、毫秒(.sss)也可以组合一起使用。

* filter在给定数组中选择满足条件的一个子集，并返回一个新数组，其条件可以是一个字符串、对象、函数

* json将Javascrip对象转成JSON字符串。

* limitTo取出字符串或数组的前（正数）几位或后（负数）几位

* lowercase将文本转换成小写格式

* uppercase将文本转换成大写格式

* number数字格式化，可控制小位位数

* orderBy对数组进行排序，第2个参数可控制方向

####自定义过滤器

* 除了使用AngularJS内建过滤器外，还可以根业务需要自定义过滤器，通过模块对象实例提供的filter方法自定义过滤器。
 
 ```html
  <body ng-app="MyApp">
    <div ng-controller="MyFilterController">
        <h1>{{info|Capitalize}}{{name}}</h1>
    </div>
 </body>
 ```
 
 ```js
    var App = angular.module('MyApp', []);
      //自定义控制器
    App.controller('MyFilterController', ['$scope', function($scope) {
    $scope.name = "xiaoming";
    $scope.info = "my name is ";
    }]);
     //自定义指令
     App.directive('name', function() {
         return {
           //
      }
    });
     //自定义过滤器
    App.filter('MyFilter', function() {
    //
    return function(input) {
        console.log('Hello' + input);

             return 'Hello ' + input;
      }
    });

    App.filter('Capitalize', function() {

       return function(input) {
            return input[0].toUpperCase() + input.slice(1);
      }
    });
  
 ```
 
###依赖注入

* AngularJS采用模块化的方式组织代码，将一些通用逻辑封装成一个对象或函数，实现最大程度的复用，这导致了使用   者和被使用者之间存在依赖关系。 

* 所谓依赖注入是指在运行时自动查找依赖关系，然后将查找到依赖传递给使用者的一种机制。

* 常见的AngularJS内置服务有$http、$location、$timeout、$rootScope等

####推断式注入

* 没有明确声明依赖，AngularJS会将函数参数名称当成是依赖的名称。

  ```js
     //控制器依赖$http、$rootScope服务
    //但并未明确声明依赖,这时会自动将函数里的参数名当成依赖对待
    App.controller('DemoController',function($http,$rootScope){
        //发送Ajax请求
       $http({
            method:'POST',
            url:'example.php',
            data{}
        });
    });

  ``` 
   #####这种方式会带来一个问题，当代码经过压缩后函数的参数被压缩，这样便会造成依赖无法找到。
  
* 行内注入  

 * 以数组形式明确声明依赖，数组元素都是包含依赖名称的字符串，数组最后一个元素是依赖注入的目标函数。
 
   ```js
    //控制器依赖$http、$rootScope服务
    //以数组形式进行声明,注意书写顺序
    App.controller('DemoController',['$http','$rootScope',function($http,$rootScope)
      {
        //发送Ajax请求
        $http({
           method:'POST',
           url:'example.php',
           data{}
       });
    }]);
   ```
   
###服务

 * 服务是一个对象或函数，对外提供特定的功能
 
####内置服务

 * $location是对原生Javascript中location对象属性和方法的封装
 
 ```js
    // $location内置对象
    var App = angular.module('App', []);
    
    // AngularJS 专门提供了一个帮你获URL地址一个服务

    App.controller('DemoController', ['$scope', '$location', function($scope, $location) {

            $scope.title = '$location服务';

            // $location就是AngularJS提前封装好的
            // 提供获取地址相关信息的服务

            //绝对路径
            $scope.absUrl = $location.absUrl();

            //url地址
            $scope.url = $location.url();

            //主机地址
            $scope.host = $location.host();

            //查询字符串
            $scope.search = $location.search();

            //哈希值
            $scope.hash = $location.hash();

            //协议
            $scope.protocol = $location.protocol();

            //端口
            $scope.port = $location.port();]
    });
 
 
 ```
