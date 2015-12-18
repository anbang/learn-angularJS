# scope特点

- $scope 是一个 POJO （Plain Ordinary Java Object）简单的Java对象
- $scope 提供了一些工具方法$watch/$apply()
- $scope 是表达式的执行环境，或者说叫作用域
- $scope 是一个树型结构，与DOM标签平行
- 每一个angular应用都有一个根作用域 $rootScope, 位于ng-app上
- $scope可以传播事件，类似DOM事件，可以向上下可以向下
- $scope不仅是MVC的基础，也是后面实现双向数据绑定的基础,应用开始先找rootScope,然后把下级scope附加到rootScope上从而形成树型结构。
# scope生命周期

##创建(Creationd)
在创建控制器或指令时，angularjs会用$injector创建一个新的作用域，并在这个新建的控制器或指令时把作用域传进去

##链接
scope对象会附加或链接到视图。这些作用域将会注册当 angular上下文中发生变化时需要运行的函数
$watch->注册监控(Watcher registration)变化时执行的回调函数

##更新
事件循环执行时，顶级的$rootScope和每个子作用域都执行自己的脏值检查。每个监控函数监控变化，检测到变化后，$scope会触发指定的回调函数。

##销毁
当scope在视图中不在需要时，会清理和销毁自己。
$scope.$destroy();