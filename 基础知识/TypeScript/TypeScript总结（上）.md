
## 基础类型

|数据类型|元素类型|备注|
|---|---|---|
|布尔值|boolean||
|数字|number||
|字符串|string||
|数组|元素类型[]||
|Array<元素类型>||
|元组 Tuple|[元素类型1, 元素类型2, 元素类型3]|一个已知元素数量和类型的数组|
|枚举|enum Color {Red, Green, Blue}<br><br>let c: Color = Color.Green;||
|未知|Any|移除类型检查|
|void|void|只能为它赋予undefined和null|
|null|null|默认情况下null和undefined是所有类型的子类型。 就是说你可以把 null和undefined赋值给number类型的变量。|
|Undefined|Undefined|
|Never|Never|永不存在的值的类型，never类型是任何类型的子类型，也可以赋值给任何类型。|
|对象|Object|非原始类型|

## 类型断言

“尖括号”语法

```
let value: any = "this is a string"; 
let length: number = (<string>value).length;
```

as 语法

```
let value: any = "this is a string";
let length: number = (value as string).length;
```

## 接口

- 接口描述对象
    ```
    interface SquareConfig {
      color?: string;
      width: number;
      readonly y: number;
    }
    ```

？可选属性
readonly 只读属性，赋值后无法改变

- 接口描述函数类型
    
    ```
    interface SearchFunc {
      (source: string, subString: string): boolean;
    }
    ```
    
- 接口描述索引类型
    
    ```
    interface StringArray {
      [index: number]: string;
    }
    ```
    
    TypeScript支持两种索引签名：字符串和数字。
    
- 接口描述类类型
    
    与C#或Java里接口的基本作用一样，TypeScript也能够用它来明确的强制一个类去符合某种契约。
    
    ```
    interface ClockInterface {
        currentTime: Date;
    }
    
    class Clock implements ClockInterface {
        currentTime: Date;
        constructor(h: number, m: number) { }
    }
    ```
    
    接口也能继承
    
    ```
    interface Shape {
        color: string;
    }
    
    interface PenStroke {
        penWidth: number;
    }
    
    interface Square extends Shape, PenStroke {
        sideLength: number;
    }
    ```

## 类

- 存取器，存取器要求你将编译器设置为输出ECMAScript 5或更高。 不支持降级到ECMAScript 3。
    
    ```
    class Employee {
        private _fullName: string;
    
        get fullName(): string {
            return this._fullName;
        }
    
        set fullName(newName: string) {
            if (passcode && passcode == "secret passcode") {
                this._fullName = newName;
            }
            else {
                console.log("Error: Unauthorized update of employee!");
            }
        }
    }
    ```
    

- 抽象；类，抽象类中的抽象方法不包含具体实现并且必须在派生类中实现。
    
    ```
    abstract class Department {
        constructor(public name: string) {
        }
        printName(): void {
            console.log('Department name: ' + this.name);
        }
        abstract printMeeting(): void; // 必须在派生类中实现
    }
    class AccountingDepartment extends Department {
        constructor() {
            super('Accounting and Auditing'); // 在派生类的构造函数中必须调用 super()
        }
        printMeeting(): void {
            console.log('The Accounting Department meets each Monday at 10am.');
        }
        generateReports(): void {
            console.log('Generating accounting reports...');
        }
    }
    let department: Department; // 允许创建一个对抽象类型的引用
    department = new Department(); // 错误: 不能创建一个抽象类的实例
    department = new AccountingDepartment(); // 允许对一个抽象子类进行实例化和赋值
    department.printName();
    department.printMeeting();
    department.generateReports(); // 错误: 方法在声明的抽象类中不存在
    ```