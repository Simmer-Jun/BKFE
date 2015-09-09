## CSS 选择器知多少 ##

从选择器的类型划分：
* ID选择器 
* 类选择器
* 标签选择器
* 属性选择器，可以划分为：
    * 简单属性选择器 类似 a[href] 将会选中有href属性的a元素
    * 具体属性选择器  类似 h1[class="tittle"] 选中所有包含完整class="title"的元素 （实行严格匹配机制）
    * 部分属性选择器  类似 span[data~="simmer"] 根据属性中分割的某个词来进行匹配 （注意比较和类选择器的区别）
     * [foo^="en"]   选择foo属性以en开头的所有元素
     * [foo$="en"]   选择foo属性以en结尾的所有元素
     * [foo*="en"]    选择foo属性中包含子串en的所有元素
    * 特定属性选择器 如 p[lang|="en"] 将会选择lang属性等于en或者以en- 开头的所有p元素
* 使用文档结构
    1 后代选择器 p  a  选择p元素里面的所有a元素，不管嵌套的多深
    2 直接子元素选择器  p > a 选择a的直接父元素为p的所有a元素
    3 相邻兄弟选择器  h1 + p 选择紧接着h1出现的所有的p元素，h1要与p元素有共同的父元素。
* 伪类选择器   顺序 link>visited>focus>hover>active
    1 静态链接伪类 a:link  a:visited  
    2 动态伪类 :focus 指示当前拥有输入焦点的元素 可以接受键盘激活或某种方式激活的元素
                      :hover 指示鼠标指针停留在哪个元素
                      :active 指示被用户输入激活的元素 鼠标点击在超链接上的那一时刻被激活
    3 静态伪类 :first-child   例如 p:first-child 将会选择作为某个元素第一个子元素的所有p
    4 根据语言  :lang()伪类  *:lang(fr) 选中所有的法语元素
    5 结合伪类 a:link:hover 
* 伪元素选择器
    1 设置首字母样式  p:first-letter 只能用于标记与段落等块级元素
    2 设置首行样式  p:first-line   只能用于标记与段落等块级元素
    3 :before   and  :after  伪元素