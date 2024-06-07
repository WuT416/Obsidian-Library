### 第一章
略

### 第二章
1  &lt;script&gt;定义了下列 6 个属性。
- async:可选。表示应该立即下载脚本，但不应妨碍页面中的其他操作，比如下载其他资源或等待加载其他脚本。只对外部脚本文件有效。
- charset:可选。表示通过 src 属性指定的代码的字符集。由于大多数浏览器会忽略它的值，因此这个属性很少有人用。
- defer:可选。表示脚本可以延迟到文档完全被解析和显示之后再执行。只对外部脚本文件有效。IE7 及更早版本对嵌入脚本也支持这个属性。
- language:已废弃。原来用于表示编写代码使用的脚本语言(如 JavaScript、JavaScript1.2或 VBScript)。大多数浏览器会忽略这个属性，因此也没有必要再用了。
- src:可选。表示包含要执行代码的外部文件。
- type:可选。可以看成是 language 的替代属性;表示编写代码使用的脚本语言的内容类型(也称为 MIME 类型)。

2  &lt;script type="text/javascript" src="example.js"&gt;&lt;/script&gt;

带有 src 属性的&lt;script&gt;元素不应该在其&lt;script&gt;和&lt;/script&gt;标签之间再包含额外的 JavaScript 代码。如果包含了嵌入的代码，则只会下载并执行外部脚本文件，嵌入的代码  
会被忽略。

3  延迟脚本并不一定会按照顺序执行，也不一定会在 DOMContentLoaded 事件触发前执行，因此最好只包含一个延迟脚本

### 第三章

1.Safari 5 及之前版本、Chrome 7 及之前版本在对正则表达式调用 typeof 操作符时会返回"function"，而其他浏览器在这种情况下会返回"object"。

2.对未初始化的变量执行 typeof 操作符会返回 undefined 值，而对未声明的变量执行 typeof 操作符同样也会返回 undefined 值。

3.从逻辑角度来看，null 值表示一个空对象指针，而这也正是使用 typeof 操作符检测 null 值时会返回"object"的原因

4.Number() 如果是 null 值，返回 0。如果是 undefined，返回 NaN。

5.Object 的每个实例都具有下列属性和方法。
constructor:保存着用于创建当前对象的函数。对于前面的例子而言，构造函数(constructor) 8就是 Object()。
hasOwnProperty(propertyName):用于检查给定的属性在当前对象实例中(而不是在实例的原型中)是否存在。其中，作为参数的属性名(propertyName)必须以字符串形式指定(例
isPrototypeOf(object):用于检查传入的对象是否是当前对象的原型
propertyIsEnumerable(propertyName):用于检查给定的属性是否能够使用for-in语句来枚举。与 hasOwnProperty()方法一样，作为参数的属性名必须以字符串形式指定。
toLocaleString():返回对象的字符串表示，该字符串与执行环境的地区对应。toString():返回对象的字符串表示。valueOf():返回对象的字符串、数值或布尔值表示。通常与 toString()方法的返回值相同。  

6.按位非操作符由一个波浪线(~)表示
按位与操作符由一个和号字符(&)表示
按位或操作符由一个竖线符号(|)表示
按位异或操作符由一个插入符号(^)表
左移操作符由两个小于号(<<)表示，这个操作符会将数值的所有位向左移动指定的位数（先转成二进制）
有符号的右移操作符由两个大于号(>>)表示，这个操作符会将数值向右移动，但保留符号位(即正负号标记)。

7.var result = "23" < "3"; //true

确实，当比较字符串"23"是否小于"3"时，结果居然是 true。这是因为两个操作数都是字符串，而字符串比较的是字符编码("2"的字符编码是 50，而"3"的字符编码是 51)。不过，将一个操作数改为数值，比较的结果就正常了

8.使用 label 语句可以在代码中添加标签，以便将来使用。以下是 label 语句的语法:label: statement下面是一个示例:

```
start: for (var i=0; i < count; i++) {  
	alert(i);
}  
```

这个例子中定义的 start 标签可以在将来由 break 或 continue 语句引用。加标签的语句一般都要与 for 语句等循环语句配合使用。  

9.with 语句的作用是将代码的作用域设置到一个特定的对象中。with 语句的语法如下:with (expression) statement;定义 with 语句的目的主要是为了简化多次编写同一个对象的工作，如下面的例子所示:

```
var qs = location.search.substring(1);  
var hostName = location.hostname;  
var url = location.href;
```

上面几行代码都包含 location 对象。如果使用 with 语句，可以把上面的代码改写成如下所示:

```
with(location){  
	var qs = search.substring(1);  
	var hostName = hostname;  
	var url = href;
}
```


### 第四章

1.ECMAScript 中所有函数的参数都是按值传递的。也就是说，把函数外部的值复制给函数内部的参数，就和把值从一个变量复制到另一个变量一样。基本类型值的传递如同基本类型变量的复制一样，而引用类型值的传递，则如同引用类型变量的复制一样。

2
```
function setName(obj) {
obj.name = "Nicholas";
}
var person = new Object();
setName(person);
alert(person.name); //"Nicholas"
```
以上代码中创建一个对象，并将其保存在了变量 person 中。然后，这个变量被传递到 setName()函数中之后就被复制给了 obj。在这个函数内部，obj 和 person 引用的是同一个对象。换句话说，即使这个变量是按值传递的，obj 也会按引用来访问同一个对象。于是，在函数内部为 obj 添加 name属性后，函数外部的 person 也将有所反映;因为 person 指向的对象在堆内存中只有一个，而且是全局对象。有很多开发人员错误地认为:在局部作用域中修改的对象会在全局作用域中反映出来，就说明参数是按引用传递的。为了证明对象是按值传递的，我们再看一看下面这个经过修改的例子:

```
function setName(obj) {
obj.name = "Nicholas";
obj = new Object();
obj.name = "Greg";
}
var person = new Object();
setName(person);
alert(person.name); //"Nicholas"
```
这个例子与前一个例子的唯一区别，就是在 setName()函数中添加了两行代码:一行代码为 obj重新定义了一个对象，另一行代码为该对象定义了一个带有不同值的 name 属性。在把 person 传递给setName()后，其 name 属性被设置为"Nicholas"。然后，又将一个新对象赋给变量 obj，同时将其 name属性设置为"Greg"。如果 person 是按引用传递的，那么 person 就会自动被修改为指向其 name 属性值为"Greg"的新对象。但是，当接下来再访问 person.name 时，显示的值仍然是"Nicholas"。这说明即使在函数内部修改了参数的值，但原始的引用仍然保持未变。实际上，当在函数内部重写 obj 时，这个变量引用的就是一个局部对象了。而这个局部对象会在函数执行完毕后立即被销毁。

3.虽然执行环境的类型总共只有两种——全局和局部(函数)，但还是有其他办法来延长作用域链。这么说是因为有些语句可以在作用域链的前端临时增加一个变量对象，该变量对象会在代码执行后被移除。在两种情况下会发生这种现象。具体来说，就是当执行流进入下任何一个语句时，作用域链就会得到加长:

try-catch 语句的 catch 块;

with 语句。

### 第五章

1.数组的 length 属性很有特点——它不是只读的。因此，通过设置这个属性，可以从数组的末尾移除项或向数组中添加新项。请看下面的例子:

```
var colors = ["red", "blue", "green"]; // 创建一个包含 3 个字符串的数组
colors.length = 2;  
alert(colors[2]);//undefined
```

2.由于 RegExp 构造函数的模式参数是字符串，所以在某些情况下要对字符进行双重转义。所有元字符都必须双重转义，那些已经转义过的字符也是如此，例如\n(字符\在字符串中通常被转义为\\，

3.callee 的属性，该属性是一个指针，指向拥有这个 arguments 对象的函数。

```
function factorial(num){  
	if (num <=1) {
		return 1;  
	} else {
		return num * factorial(num-1);  
	}
}
```

定义阶乘函数一般都要用到递归算法;如上面的代码所示，在函数有名字，而且名字以后也不会变的情况下，这样定义没有问题。但问题是这个函数的执行与函数名 factorial 紧紧耦合在了一起。为了消除这种紧密耦合的现象，可以像下面这样使用 arguments.callee。

```
function factorial(num){  
	if (num <=1) {
		return 1;  
	} else {
		**return num * arguments.callee(num-1);**
	}  
}
```

4.前面曾经提到过，ECMAScript 中的函数是对象，因此函数也有属性和方法。每个函数都包含两个属性:length 和 prototype。其中，length 属性表示函数希望接收的命名参数的个数

### 第六章

1.一个例子创建了一个名为 name 的属性，它的值是只读的。这个属性的值是不可修改的，如果尝试为它指定新值，则在非严格模式下，赋值操作将被忽略;在严格模式下，赋值操作将会导致抛出错误。

2

```
//抛出错误
Object.defineProperty(person, "name", {
    configurable: true,
    value: "Nicholas"
});
```
可以多次调用 Object.defineProperty()方法修改同一个属性，但在把 configurable特性设置为 false 之后就会有限制了。

3.定义多个属性

```
var book = {};
Object.defineProperties(book, { 
_year: {
           writable: true,
            value: 2004
},
edition: {
            writable: true,
value: 1 }
}
```
4.用函数封装类

```
function createPerson(name, age, job){ var o = new Object();
o.name = name;
o.age = age;
o.job = job;
o.sayName = function(){
alert(this.name); };
return o; }
var person1 = createPerson("Nicholas", 29, "Software Engineer"); var person2 = createPerson("Greg", 27, "Doctor");

```
5

```
alert(Person.prototype.isPrototypeOf(person2)); //true
```
这里，我们用原型对象的 isPrototypeOf()方法测试了 person2。因为它们内部有一个指向 Person.prototype 的指针，因此返回了 true。

```
alert(Object.getPrototypeOf(person1) == Person.prototype); //true 
alert(Object.getPrototypeOf(person1).name); //"Nicholas"
```
ECMAScript 5增加了一个新方法，叫Object.getPrototypeOf()，在所有支持的实现中，这个方法返回[[Prototype]]的值。

6

```
function Person(){
    }
Person.prototype.name = "Nicholas";
Person.prototype.age = 29;
Person.prototype.job = "Software Engineer"; 
Person.prototype.sayName = function(){
alert(this.name);
};
var person1 = new Person();
var person2 = new Person();
alert(person1.hasOwnProperty("name")); //false
alert("name" in person1);  //true--------7
alert(hasPrototypeProperty(person, "name"));  //true--------8

person1.name = "Greg";
alert(person1.name); //"Greg"——来自实例 
alert("name" in person1);  //true--------7
alert(hasPrototypeProperty(person, "name"));  //false--------8

alert(person1.hasOwnProperty("name")); //true
alert(person2.name); //"Nicholas"——来自原型 
alert(person2.hasOwnProperty("name")); //false
alert("name" in person1);  //true--------7

delete person1.name;
alert(person1.name); //"Nicholas"——来自原型 
alert(person1.hasOwnProperty("name")); //false
alert("name" in person1);  //true--------7
```
使用 hasOwnProperty()方法可以检测一个属性是存在于实例中，还是存在于原型中。这个方法(它是从 Object 继承来的)只在给定属性存在于对象实例中时，才会返回 true。

7.如代码所示在以上代码执行的整个过程中，name 属性要么是直接在对象上访问到的，要么是通过原型访问到的。因此，调用"name" in person1 始终都返回 true，无论该属性存在于实例中还是存在于原型中。同时使用 hasOwnProperty()方法和 in 操作符，就可以确该属性到底是存在于对象中，还是存在于原型中，如下所示。

8

```
function hasPrototypeProperty(object, name){
return !object.hasOwnProperty(name) && (name in object);
}
```
由于 in 操作符只要通过对象能够访问到属性就返回 true，hasOwnProperty()只在属性存在于实例中时才返回 true，因此只要 in 操作符返回 true 而 hasOwnProperty()返回 false，就可以确定属性是原型中的属性。下面来看一看上面定义的函数 hasPrototypeProperty()的用法。

9

如果你想要得到所有实例属性，无论它是否可枚举，都可以使用 Object.getOwnPropertyNames()方法。

```
var keys = Object.getOwnPropertyNames(Person.prototype);
alert(keys); //"constructor,name,age,job,sayName"
```
### 第七章

1.我们把有权访问私有变量和私有函数的公有方法称为特权方法(privileged method)。有两种在对象  
上创建特权方法的方式。第一种是在构造函数中定义特权方法，基本模式如下。

```
function MyObject(){
   //私有变量和私有函数 
     var privateVariable = 10;
    function privateFunction(){
        return false;
}
//特权方法
this.publicMethod = function (){
        privateVariable++;
        return privateFunction();
    };
}
```
能够在构造函数中定义特权方法，是因为特权方法作为闭包有权访问在构造函数中定义的所有变量和函数。