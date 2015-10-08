## JavaScript DOM1 Level ##

### 什么是DOM? ###
DOM(文档对象模型)是针对HTML和XML文档的一个API(应用程序编程接口)。DOM描绘了一个层次化的节点树，允许开发人员添加，移除和修改页面的某一部分。

### Node 类型 ###
DOM1级定义了一个Node接口，该接口将由DOM中的所有节点类型实现。这个Node接口在javascript中作为Node类型实现的，除了IE外，在其他所有的浏览器中都可以访问到这个类型。javascript中的所有节点类型都继承自Node类型，因此所有的节点类型都共享着相同的基本属性和方法。
每个节点都有一个nodeType属性，用于表明节点类型。节点类型由在Node类型中定义的下列12个数值常量来表示，任何节点类型必居其一。
 * Node.ELEMENT_NODE(1)
 * Node.ATTRIBUTE_NODE(2)
 * Node.TEXT_NODE(3)
 * Node.CDATA_SECTION_NODE(4)
 * Node.ENTITY_REFERENCE_NODE(5)
 * Node.ENTITY_NODE(6)
 * Node.PROCESSING_INSTRUCTION_NODE(7)
 * Node.COMMENT_NODE(8)
 * Node.DOCUMENT_NODE(9)
 * Node.DOCUMENT_TYPE_NODE(10)
 * Node.DOCUMENT_FRAGMENT_NODE(11)
 * Node.NOTATION_NODE(12)

### Example ###
`if(someNode.nodeType == Node.ELEMENT_NODE){ // 在IE中无效
	alert('ELEMENT NODE!');  
}`

`if(someNode.nodeType == 1) { // better 适用于所有浏览器
	alert('ELEMENT NODE');
}`

### 节点关系 ###
文档中的节点之间都存在这样或那样的关系。
 * 每个节点都有一个childNodes属性，其中保存着一个childNodes对象。注意这个NodeList是一个类数组对象，保存着一组有序的节点，可以通过位置来访问这些节点。所有它并不是Array的一个实例!我们来看一下如何访问某个节点下的Nodelist节点：
  * var firstChild = someNode.childNodes[0];
  * var secondChild = someNode.childNodes.item(1);
  * var count = someNode.childNodes.length;
 * 每个节点都有一个parentNode属性，该属性指向文档树的父节点。包含在childNodes中的所有节点都具有相同的父节点。
 * 在childNodes中的每个节点都有`nextSibling`和`previousSibling`两个属性，指向childNodes中的下一个／上一个子节点。对于`firstChild`的`previousSibling`和`lastChild`的`nextSibling`，他们的值都为null。
 * 父节有两个指向子节点的特殊属性`firstChild`和`lastChild`，分别指向父节点的第一个和最后一个子节点
 * 所有节点都有的最后一个属性是`ownerDocument`，该属性指向表示整个文档的文档节点，表明任何的节点都属于它所在的文档，任何节点都不能同时存在2个或更多个的文档中。

### 操作节点 ###
上面讲的都是文档节点之间的关系，那么如何改变文档？
 * `appendChild()`在某个节点下增加子节点，这个方法将会返回刚刚添加进的节点并且使得父节点的`lastChild`指向刚添加进的节点。
 * `insertBefore(newNode,referenceNode)` 在参考节点之前插入节点
 * `replaceChild(newNode,oleNode)`将新的节点替换现有的节点，返回新的节点。
 * `removeChild()` 移除节点，返回被移除的节点。移除的节点依旧为文档所有，只不过在文档中已经没有了自己的位置。

### 其他方法 ###
有两个方法是所有类型的节点都有的。
 * cloneNode()，用于创建调用这个方法的节点的一个完全相同的副本。cloneNode()方法接受一个布而值，表示是否执行深复制。cloneNode(true):深复制 cloneNode(false):浅复制 注意 这个方法不会复制添加到DOM节点中的javascript属性，例如事件处理器文本节点的情况。
 * normalize()，这个方法的唯一作用就是处理文档树中的文本节点。由于解析器的实现货DOM操作等原因，可能出现文本节点不包含文本，或者接连出现两个文本的情况。当在某个节点上调用这个方法时，就会在改节点的后代节点中查找上述的两种情况。

 ### 待续 ###













