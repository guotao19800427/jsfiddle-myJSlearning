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

大白话解释deffered，when，promise，then这些玩意儿： http://www.ruanyifeng.com/blog/2011/08/a_detailed_explanation_of_jquery_deferred_object.html

我对闭包的理解，边想边写，然后再去网上验证是否正确：
首先闭包是个JS里再正常不过的东西，这就好像你在现实生活中，在马路上碰到一辆汽车一样，非常非常正常。
要理解闭包呢，我们先确定我们对JS里的另外两个再平常不过的东西是理解的。这两个东西是：作用域链（scope chain）和垃圾回收机制（浏览器有垃圾回收机制对吧，其他的‘程序运行装置’也有垃圾回收机制，我们先不管这些装置各自的怪癖，就先就标准的垃圾回收机制而言）。
OK 正题：
作用域链的总则： 局部变量对其父作用域是不可见的，而反过来，父作用域中的变量对其子作用域是可见的。再白话一下就是--当在一个作用域中寻找变量时，能找到就找到，找不到就去其父亲作用域中寻找（而绝不会去其子作用域中寻找），能找到就找到，找不到就再去问爷爷找，不行就再找曾爷爷，以此类推，直到全局作用域，找到ok找不到就返回undefined。

垃圾回收机制原则：一个函数开始执行时，会在内存中划分空间保存其中定义的变量以备函数的语句所用。等函数作用完毕，这些保存在内存空间中的变量就会被认为是无用的（术语叫做引用数为0），所以这些变量也就被回收了（其实是存放他们的内存空间被回收）。下次再执行这个函数时，就按照上面的规则再来一遍。这是很正常也很合理的。这中合理会在函数中有内嵌函数时，产生一个合理的issue， 例子：
function a(){
  var x = 100;
  return function(){
    alert(x);
  }
}
var b = a();
b();
a 函数内嵌了一个函数并且返回了这个函数,在b引用a函数执行并返回的结果的时候，按常规说这时a函数执行完毕了，那么a函数所用到的变量可以被回收了，但由于a函数执行完毕并返回了一个（匿名）函数，这个匿名函数里有对a函数（匿名函数的父作用域）的变量x的引用，所以变量x还不能被回收，不然的话函数本身不就运行不下去了吗？那JS还玩什么。所以呢，垃圾回收机制就是这样保证JS函数能正常运行的：当开始执行一个函数时，会把所有他用到得变量，包括他爸爸的，他爷爷的，他祖宗的，直到全局变量，都在内存空间划分空间进行存储。直到一个准则成立时再把他们释放，这个准则就是：引用数为0.
所以呢，当回收机制看到这句话：var b = a()时,a执行并执行完毕（执行就是瞬间的事情），但a函数中得变量x不能被回收，因为由b这个变量所引用的匿名函数里还有对x变量的引用呢。垃圾回收机制也不敢说b什么时会聒噪起来去调用变量x啊（除非b所在的函数被执行完毕了）。所以呢，x变量在内存所占用的空间就会被垃圾回收机制一直保留着。
啰嗦了半天，那谁是闭包呢？不敢说吗?哈哈，不，啰嗦半天是有原因的，我们这样定义闭包，能产生这种让其父作用域的变量不被回收的东西，在JS里就叫闭包。更漂亮一点儿的说法就是：当变量在其被包含的作用域‘死亡’后，自己却仍然活着，这种现象就叫闭包。如果我们简单粗暴一点，就可以吧上面a返回的匿名函数叫做闭包。


