# HTML script标签 #
标签： script标签
---

## scrip标签有几个属性？##
 * src 指向一个外部JavaScript文件（可以不同域） 当含有src属性后将不会去执行 script标签内部代码
 * defer 表明当前的JavaScript代码不会对DOM结构进行修改，浏览器遇到加了derfer属性的标签后将会立即下载但延迟加载，按照HTML5规范，所有的加了defer属性的script标签都会按照它们在HTML文档的顺序去执行。 IE&firefox &chrome  onload事件触发前！？？
 * async 与defer类似 但是不能保证按照在HTML中出现的顺序，如果需要加载需要互不依赖的JavaScript代码 可以使用这个属性
 * type属性 但是这在HTML5中式可选的。
 * charset 指定脚本语言编码类型  一般不写 我们在head标签的头部使用<meta charset="UTF-8"> 的形式指定文档的编码方式
 *  language 已废除

## 为何谈到script标签加载如此的重要？ ##
 * 与我们的web页面呈现的快慢有着直接的联系。(直接关系到用户体验度)
 * 可以阻塞页面的渲染过程（非异步加载脚本）
 * 关系到页面的心脏的跳动 结构(HTML)表现(CSS)行为(JavaScript)
 * web性能优化重要的一点。

## 使用DOM 动态加载script标签 对于动态加载的script标签：##

    var script = document.createElement('script');
    script.src = 'load.js';
    if(script.readyState) {
    script.onreadystatechange = function () {
    if (script.readyState == 'loaded' || script.readyState == 'complete') { // 老版本IE 
    script.onreadystatechange = null;
    alert('javascript loaded!');
    }
    }
    } else {
    script.onload = function () {  // IE9+ and 标准浏览器兼容
    alert("javascript loaded! expect IE!")
    }
    }
    document.getElementsByTagName('body')[0].appendChild(script);


我发现了什么?
* IE 会在window.onload事件触发后去执行DOM动态加载的代码
* 而其他标准浏览器则是在window.onload事件触发之前执行DOM动态加载的代码 但是IE9+似乎在使用onload的时候符合2

## 使用XHR 动态加载 (ajax加载) ##
创建XMLHTTPRequest()对象 动态获取JavaScript代码文本 加入进创建的script标签中。
