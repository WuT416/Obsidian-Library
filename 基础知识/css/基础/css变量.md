**1.自定义属性**（有时候也被称作**CSS变量**或者**级联变量**）是由CSS作者定义的，它包含的值可以在整个文档中重复使用。由自定义属性标记设定值（比如： **--main-color: black;**），由[var()](https://developer.mozilla.org/zh-CN/docs/Web/CSS/var)函数来获取值（比如： color: **var(--main-color)**;）

复杂的网站都会有大量的CSS代码，通常也会有许多重复的值。举个例子，同样一个颜色值可能在成千上百个地方被使用到，如果这个值发生了变化，需要全局搜索并且一个一个替换。自定义属性在某个地方存储一个值，然后在其他许多地方引用它。另一个好处是语义化的标识。比如，--main-text-color 会比 #00ff00 更易理解，尤其是这个颜色值在其他上下文中也被使用到。

自定义属性受级联的约束，并从其父级继承其值。

2.基本用法

声明一个自定义属性，属性名需要以两个减号（--）开始，属性值则可以是任何有效的CSS值。和其他属性一样，自定义属性也是写在规则集之内的

eg：

规则集所指定的选择器定义了自定义属性的可见作用域。通常的最佳实践是定义在根伪类 [:root](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:root) 下，这样就可以在HTML文档的任何地方访问到它了：


```
:root {

  --main-bg-color: brown;

}
```


```
element {

  background-color: var(--main-bg-color);

}
```


3.js获取

代码块


```
// 获取一个 Dom 节点上的 CSS 变量

element.style.getPropertyValue("--my-var");

​

// 获取任意 Dom 节点上的 CSS 变量

getComputedStyle(element).getPropertyValue("--my-var");

​

// 修改一个 Dom 节点上的 CSS 变量

element.style.setProperty("--my-var", jsVar + 4);
```
