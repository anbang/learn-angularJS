#什么是控制器

AngularJS控制器控制AngularJS应用程序的数据，是常规的JavaScript对象。

ng-controller指令就是用来定义应用程序控制器的，并且同时创建了一个新的作用域关联到相应的DOM元素上。

所谓作用域就是一个指向应用模型的对象，它是表达式的执行环境，作用域有层次结构，这个层次和相应的DOM几乎是一样的，作用域能监控表达式和传递事件并且可以从父作用域继承属性。

每一个AngularJS应用都有一个绝对的根作用域。但也可能有多个子作用域。 一个应用可以有多个作用域，因为有一些指令会生成新的子作用域，当新作用域被创建的时候，他们会被当成子作用域添加到父作用域下，这使得作用域会变成一个和相应DOM结构一个的树状结构。

#控制器上的属性

现在我们就用ng-controller指令来创建一个简单的控制器定义，如下所示：

    <div ng-app="" ng-controller="MyController">
    
    请输入一个名字：<input type="text" ng-model="person.name"> 
    
    Hello <span ng-bind="person.name"></span> 
    
    </div>    
    
    <script>
    function MyController($scope) {
       $scope.person = {
          name: "zhu"
       };
    }
    </script>
    
如上所述，我们通过ng-controller指令创建了一个JavaScript对象 —— MyController并带有name属性，

我们就来解答MyController对象参数 —— $scope。

$scope就是把一个DOM元素连结到控制器上的对象，它提供一个绑定到DOM元素(以及其子元素)上的执行上下文。它也是一个JavaScript对象，指向应用程序作用域内的所有HTML元素和执行上下文。

要明确创建一个$scope对象，我们就要给DOM元素安上一个controller对象，使用的是ng-controller 指令属性。

所有$scope都遵循原型继承，这意味着它们都能访问父$scope们,对任何属性和方法，如果AngularJS在当前$scope上找不到，就会到父$scope上去找，如果在父$scope上也没找到，就会继续向上回溯，一直到$rootScope上，这个$rootScope是最顶级的$scope，它对应着含有 ng-app指令属性的那个DOM元素，也就是说根作用域关联的DOM就是ng-app指令定义的地方。

也就是说，拥有了$scope，我们就可以操作作用域内任何我们想要获取的对象数据。

#控制器还可以声明方法

    <div ng-app="" ng-controller="MyController">
         名称:
         <input type="text" ng-model="username">
         <button ng-click="sayHello()">打招呼</button>
         <hr>
         {{greeting}}
    </div>
    
    <script>
    function MyController($scope) {
      $scope.username = 'zhu';
      $scope.sayHello = function() {
        $scope.greeting= 'Hello ' + $scope.username + '!';
      };
    }
    </script>
    
    
#注意事项
- 不要试图去复用controller,一个控制器一般只负责一小块视图
- 不要在controller中操作DOM，这不是控制器的职责，是指令的职责。
- 不要在controller里做数据格式化，ng有很好用的过滤器实现此功能。
- 不要在controller里面做数据过滤操作，ng有$filter服务
- 一般来说，controller是不会互相调用的，控制器这间的交互是通过事件进行的。
