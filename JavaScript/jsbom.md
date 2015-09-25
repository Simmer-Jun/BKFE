 ## JavaScript BOM 知多少？##

 * BOM的核心对象是window，它表示浏览器的一个实例。
 * window是ECMCScript规定的Global对象。
 * window也是通过javascript访问浏览器窗口的一个接口。
 * 什么是全局作用域？
 * window.a 和var a 有什么区别？前者可以通过delete操作符删除 IE9以下删除全局变量会发生错误
 * 尝试访问未声明的变量会抛出错误。属性查找找不到返回 undefined
 * 关于框架的一些tips：
       * 每个框架中的window对象值得都是当前的框架的特定实例，所以要用top.frames[index] or top.frames[‘frame name']
       * top 指向的都是当前框架的最顶层框架 于此相似的parent则指代代码所在框架的直接上层框架 最后一个与框架相关的则是self对象，引入self的作用仅仅是为了与top parent对象对应。 都是window的属性可以用类似window.top进行访问
 * 关于setTimeout() 该方法将会返回一个数值ID 表示超时调用，可以用它来取消超时调用。注意 超时调用代码是在全局作用域中调用的，this指代window，在严格模式下this指代undefined

## location ##
window.location === document.location
host/hostname/href/pathname/port/protocol/search