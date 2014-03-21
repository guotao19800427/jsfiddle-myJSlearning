jsfiddle-myJSlearning
=====================

some  JS example writen by self to help me to understand the plane JS theory

Class - self deep copy : http://jsfiddle.net/FKFZ4/16/

simplest HTML5 template : http://jsfiddle.net/tonyguo/CeHBC/

$.Deferred simplest example : http://jsfiddle.net/tonyguo/tEx2A/

another $.Deferred example : http://jsfiddle.net/tonyguo/tEx2A/1/

JS 不支持后发断言(只能用先发断言或者别的方案替代):  http://jsfiddle.net/tonyguo/ar7M4/4/

正则表达式 \1\2\n 中的1,2，n表示捕获分组的分组号： http://jsfiddle.net/tonyguo/ar7M4/5/

如何系统学习细节多而杂项也多的前端： http://www.zhihu.com/question/19834302

JS中的继承 ： http://www.cnblogs.com/qiantuwuliang/archive/2011/01/08/1930548.html

组件化例子一： http://jsfiddle.net/tonyguo/VmYAr/6/

组件化例子二： http://jsfiddle.net/tonyguo/VmYAr/5/

我自己理解的继承：http://jsfiddle.net/tonyguo/jHQ7P/6/
一般我在项目里会这样实现组件化:
1) 用匿名自执行函数封装一个执行环境
2）在这个环境中建立构造函数，并为这个构造函数添加公有方法和属性，也就是prototype方法和prototype属性
3）将一些能够独立出来的功能点归纳成独立的函数，这里可以利用函数式编程，这里的函数将会最可能被第2步的构造函数利用，其实这也就是常说的封装，将功能点独立处理，为了自己的代码易读，易维护，易扩展。
4）在最后，也就是这个执行环境的最后，绑定我们需要的操作，最常见的就是DOM的操作。


深copy更深入的理解 ：http://jsfiddle.net/tonyguo/xA5zT/

说不尽的原型链 ： http://www.cnblogs.com/vinqon/archive/2011/04/01/2031392.html
