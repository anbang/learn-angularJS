#MVVM简介
MVVM模式是Model-View-ViewMode模式的简称。由模型(Model)、视图(View)、视图模型(ViewModel)三部分组成，通过这三部分实现UI逻辑、呈现逻辑和状态控制、数据与业务逻辑的分离。

Model将和ViewModel互动(通过$scope对象)，将监听Model的变化。这些可以通过View来发送和渲染，由HTML来展示你的 代码。

Model与MVC模式一样，Model用于封装与应用程序的业务逻辑相关的数据以及对数据的处理方法。它具有对数据直接访问的权利，例如对数据库的访问，Model不依赖于View和ViewModel，也就是说，模型不关心会被如何显示或是如何被操作，模型也不能包含任何用户使用的与界面相关的逻辑。

ViewModel是一个用来提供特别数据和方法从而维护指定view的对象,。ViewModel是$scope的对象，只存在于AnguarJS的应用中。$scope只是一个简单的js对象，这个对象使用简单的API来侦测和广播状态变化。

Controller负责设置初始状态和参数化$scope方法用以控制行为。需要指出的controller并不保存状态也不和远程服务互动。

View是AngularJS解析后渲染和绑定后生成的HTML。这个部分帮助你创建web应用的架构。$scope拥有一个针对数据的参考，controller定义行为，view处理布局和互动。

#使用MVVM模式有几大好处：

- 低耦合：View可以独立于Model变化和修改，一个ViewModel可以绑定到不同的View上，当View变化的时候Model可以不变，当Model变化的时候View也可以不变。

- 可重用性：可以把一些视图的逻辑放在ViewModel里面，让很多View重用这段视图逻辑。

- 独立开发：开发人员可以专注与业务逻辑和数据的开发(ViewModel)。设计人员可以专注于界面(View)的设计。

- 可测试性：可以针对ViewModel来对界面(View)进行测试。

