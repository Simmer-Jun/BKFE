# JavaScript 类型判断知多少？ #

## 使用typeof ##
 * 使用typeof属性判断基本类型和对象，typeof是操作符
 * type可用于检测基本类型，对于字符串/函数/数字/布尔/null/undefined/obj检测分别返回 "string/function/number/boolean/object/underfined/obj"  注意 undefined派生自null 所以 undefined == null  返回"true"，关于基本类型一些特定如下：
     * Boolean() 可用于将任何值返回特点的boolean类型值（true or false）,运用的比较多的地方就在if语句中 if() 括号里面的值将会转换为boolean值
     * 浮点运算精度为17位 不要做类似if (0.1 + 0.2 == 0.3)的判断
     * Number.MIN_VALUE 与 Number.MAX_VALUE中 如果某次运算的结果超出则将自动转化为-Infinity or Infinity  使用isFinite()判断数值是否在有效区间内。NaN == NaN return false  任何涉及NaN的操作都将返回 NaN 所以就又有了所谓的isNaN() 来判断是否为NaN...
     * Number()可用于任何数据类型，稍微有些许的复杂。parseInt(string[,进制基数])  parseFloat(string)不在支持16进制
     * toString()方法几乎所有的类型都含有除了undefined /null 这个时候就要使用String()方法 如果某个方法含有toString()方法这调用它的返回结果。如果是undefined/null则直接返回"null"和"undefined"
     * Constructor hanOwnproperty() isPrototypeOf()  propertyIsEnumerable() valueOf() toLocalString() toString()
## 使用instanceof ##

 * obj instanceof [Function/Array/Obj/Boolean/String/RegExp/Error] 
 * 利用原型链查找，但是在跨iframe的时候由于来源不同 所以判断不同框架不能使用instanceof 
 * 当然instanceof的用处不仅仅如此，它能判断某个实例是否是是某个构造函数的的实例

## 使用toString() ##

判断复杂的引用类型怎么办？当然要数toString方法
使用Object.prototype.toString.call(obj) 能够精确的返回一个对obj的类型判断的字符串。结果如下：
 * Object.prototype.toString.call([1，2，3]) // "[object Array]"
 * Object.prototype.toString.call({name:"simmer"}) // "[object Object]"
 * Object.prototype.toString.call(/ simmer/g) // "[object RegExp]"
 * Object.prototype.toString.call(true) // "[object Boolean]"