1.布尔值是最基础的数据类型，在 TypeScript 中，使用 boolean 定义布尔值类型：

let isDone: boolean = false; // 编译通过

注意，使用构造函数 Boolean 创造的对象**不是**布尔值：事实上 new Boolean() 返回的是一个 Boolean 对象：

let createdByNewBoolean: Boolean = new Boolean(1);

直接调用 Boolean 也可以返回一个 boolean 类型：

let createdByBoolean: boolean = Boolean(1);

在 TypeScript 中，boolean 是 JavaScript 中的基本类型，而 Boolean 是 JavaScript 中的构造函数。其他基本类型（除了 null 和 undefined）一样，不再赘述。

2.0b1010 和 0o744 是 ES6 中的二进制和八进制表示法，它们会被编译为十进制数字。

3.JavaScript 没有空值（Void）的概念，在 TypeScript 中，可以用 void 表示没有任何返回值的函数：

function alertName(): void { alert('My name is Tom'); }

声明一个 void 类型的变量没有什么用，因为你只能将它赋值为 undefined 和 null：

let unusable: void = undefined;

4.与 void 的区别是，undefined 和 null 是所有类型的子类型。也就是说 undefined 类型的变量，可以赋值给 number 类型的变量：

// 这样不会报错 let num: number = undefined;

// 这样也不会报错 let u: undefined; let num: number = u;

而 void 类型的变量不能赋值给 number 类型的变量：

5.但如果是 any 类型，则允许被赋值为任意类型。let myFavoriteNumber: any = 'seven';

在任意值上访问任何属性都是允许的，也允许调用任何方法，**声明一个变量为任意值之后，对它的任何操作，返回的内容的类型都是任意值**。

**变量如果在声明的时候，未指定其类型，那么它会被识别为任意值类型**

**6.**如果没有明确的指定类型，那么 TypeScript 会依照类型推论（Type Inference）的规则推断出一个类型。

以下代码虽然没有指定类型，但是会在编译的时候报错：

let myFavoriteNumber = 'seven'; myFavoriteNumber = 7;

**如果定义的时候没有赋值，不管之后有没有赋值，都会被推断成 any 类型而完全不被类型检查**：

let myFavoriteNumber; myFavoriteNumber = 'seven'; myFavoriteNumber = 7;

7.联合类型（Union Types）表示取值可以为多种类型中的一种。

let myFavoriteNumber: string | number; myFavoriteNumber = 'seven'; myFavoriteNumber = 7;