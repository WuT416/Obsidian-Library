1.interface Person { name: string; age?: number;}

let tom: Person = { name: 'Tom' };

name是属性，age为可选属性（加？）

[propName: string]: any;允许添加任意属性

2.需要注意的是，**一旦定义了任意属性，那么确定属性和可选属性的类型都必须是它的类型的子集**。上例中，任意属性的值允许是 string，但是可选属性 age 的值却是 number，number 不是 string 的子属性，所以报错了。

interface Person {

readonly id: number;

name: string;

age?: number;

[propName: string]: string | number; }

let tom: Person = { name: 'Tom', age: 25, gender: 'male' };

上例中，任意属性的值允许是 string，但是可选属性 age 的值却是 number，number 不是 string 的子属性，所以报错了。

3.定义数组

let fibonacci: number[] = [1, 1, 2, 3, 5];

也可以使用数组泛型（Array Generic） Array<elemtype> 来表示数组：

let fibonacci: Array<number> = [1, 1, 2, 3, 5];

接口也可以用来描述数组

interface NumberArray { [index: number]: number; } let fibonacci: NumberArray = [1, 1, 2, 3, 5];

描述类数组：

function sum() { let args: { [index: number]: number; length: number; callee: Function; } = arguments; }

4.函数

function sum(x: number, y: number): number { return x + y; }

注意，**输入多余的（或者少于要求的）参数，是不被允许的**：

5.与接口中的可选属性类似，我们用 ? 表示可选的参数：

function buildName(firstName: string, lastName?: string) {

if (lastName) { return firstName + ' ' + lastName; }

else { return firstName; } }

let tomcat = buildName('Tom', 'Cat');

let tom = buildName('Tom');

需要注意的是，可选参数必须接在必需参数后面。换句话说，**可选参数后面不允许再出现必需参数了**

6.在 ES6 中，我们允许给函数的参数添加默认值，**TypeScript 会将添加了默认值的参数识别为可选参数**：

function buildName(firstName: string, lastName: string = 'Cat') { return firstName + ' ' + lastName; } let tomcat = buildName('Tom', 'Cat'); let tom = buildName('Tom');

此时就不受「可选参数必须接在必需参数后面」的限制了：

function buildName(firstName: string = 'Tom', lastName: string) { return firstName + ' ' + lastName; } let tomcat = buildName('Tom', 'Cat'); let cat = buildName(undefined, 'Cat');

7.我们可以使用重载定义多个 reverse 的函数类型：


```
function reverse(x: number): number;

 function reverse(x: string): string; 

function reverse(x: number | string): number | string {

 if (typeof x === 'number') {

 return Number(x.toString().split('').reverse().join('')); } else if (typeof x === 'string') { return x.split('').reverse().join(''); } }
```
上例中，我们重复定义了多次函数 reverse，前几次都是函数定义，最后一次是函数实现。在编辑器的代码提示中，可以正确的看到前两个提示。

注意，TypeScript 会优先从最前面的函数定义开始匹配，所以多个函数定义如果有包含关系，需要优先把精确的定义写在前面。