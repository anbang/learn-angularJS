#模块

一切是从模块开始，module就是容器,其它的元素都挂在module里面.

module
config filter directive factory controller
routes service
provider
value

#模块之间如何依赖 依赖注入
        
        // 传递参数不止一个,代表新建模块;空数组代表该模块不依赖其他模块
        var createModule = angular.module("myModule", []);
        
        // 只有一个参数(模块名),代表获取模块
        // 如果模块不存在,angular框架会抛异常
        var getModule = angular.module("myModule");
        
该函数既可以创建新的模块，也可以获取已有模块，是创建还是获取，通过参数的个数来区分。

    angular.module(name, [requires], [configFn]);
    
    - name：字符串类型，代表模块的名称；
    - requires：字符串的数组，代表该模块依赖的其他模块列表，如果不依赖其他模块，用空数组即可；
    - configFn：用来对该模块进行一些配置。
    
模块是一些功能的集合，如控制器、服务、过滤器、指令等子元素组成的整体。

