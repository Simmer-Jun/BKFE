## 包装对象 ##
类似
` var str = ‘hello!’;
 hello.name = ’simmer’; 创建了一个包装对象 在这行代码执行结束后立即删除这个对象
var name = hello.name; // Error name undefined`

## 区别 ##
引用类型和基本包装类型的主要区别就是对象的生存周期。
在执行流离开当前作用域之前都一直保存在内存中－－引用类型
只存在于一行代码执行的瞬间，随后立即被销毁。－－基本包装类型。

对于Boolean 和 Number 最好不要去创建对象，而是以基本类型来参与运算

## 特殊的String对象 ##
但是对于String来说，他的基本包装对象上的一些方法将会变的很有用。
 * charAt()   charCodeAt()  concat()字符串拼接
 * slice( ) substring( ) substr( )的区别？
          * slice(a[,b] ) a指代字符串的起始位子 b为可选参数，表示结束位置 但是通常只返回结束为止前一位
          * substring(a[,b]) 和slice方法比较相似，只是在处理传入的值为负数的情况下有一些不同。在slice中 a/b为负数将会和字符串相加 但是substring( )会将所有的负数都转为0  对于substr(a[,b])  如果a为负数将a和字符串长度相加，如果b为负数则会将b转为0.
           * substr(a[,b] ) a指代字符串开始 b指代截取字符串的长度（不是结束位置）
 * indexOf(a[,b])  当然a不仅仅是单个字符串，也可以是类似`console.log('simmer'.indexOf('mer'));  // 3`返回3 表示查找字符串首字符的索引。 b表示从字符串的哪一个开始。
 * trim( )方法 创建当前字符串的副本删除前置和后后缀的所有空格
 * toLowerCase( )/toLocalLowerCase( )/ toUpperCase( )/toLocalUpperCase( )
 * 模式匹配方法 reg.exec(’string’)和 string.match(reg)相同 当然还有search( )方法 接受一个由字符串或正则对象指定的一个正则表达式，返回索引。  repleace( )方法  注意第一个参数可以是字符串或一个正则表达式区别在于是取代多次还是取代一次
 * split(‘ ,’);基于指定的分隔符将字符串分割成许多的子字符串，结果放在一个数组中。
 * localCompare( ) 更具所在字母表的先后顺序返回不同的取值。
 * fromeCharCode( )