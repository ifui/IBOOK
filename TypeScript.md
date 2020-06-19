# TypeScript

## 数据类型

### 布尔值

```js
let isActive: boolean = false;
```

### 数值

```js
let count: number = 100;
```

### 字符串

```js
let name: string = 'ifui';
// 模板字符串
let hello: string = `Hello ${name}.`;
```

### 空值、`Null`、`Undefined`

```js
// void 表示没有任何返回值的函数
function who(): void {
  alert('Hello ifui!');
}
// void 只能赋值 undefined 和 null
let unKnow: void = undefined;
// void 类型的变量不能赋值给 number 类型的变量
let unNum: number = unKnow; // Type 'void' is not assignable to type 'number'.
// null 和 undefined 定义这两个原始数据类型
let u: undefined = undefined;
let n: null = null;
```

### 数组

```js
// 表示由此类型元素组成的数组
let list: number[] = [1, 2, 3];
// 数组泛型, Array<元素类型>
let list: Array<number> = [1, 2, 3];
```

### 元组 Tuple

```js
let x: [string, number];
```

### 枚举 Enum

```js
enum Color {Red, Green, Blue}
let c: Color = Color.Green
```

### 任意值

```js
let notSure: any = 4;
```

### 不存在的值 Never

```js
// 返回never的函数必须存在无法达到的终点
function error(message: string): never {
    throw new Error(message);
}

// 推断的返回值类型为never
function fail() {
    return error("Something failed");
}

// 返回never的函数必须存在无法达到的终点
function infiniteLoop(): never {
    while (true) {
    }
}
```

### 对象 Object

```js
declare function create(o: object | null): void;

create({ prop: 0 }); // OK
create(null); // OK

create(42); // Error
create("string"); // Error
create(false); // Error
create(undefined); // Error
```

## 类型断言

```js
// 尖括号
let someValue: any = "this is a string";
let strLength: number = (<string>someValue).length;
// as (推荐)
let someValue: any = "this is a string";
let strLength: number = (someValue as string).length;
```

## 联合类型 `Union Types`

> 表示取值可以为多种类型中的一种

```js
let myFavoriteNumber: string | number;
let myFavoriteNumber = 'seven';
let myFavoriteNumber = '7';

function getAge(age: string | number): number {
  return something.toString()
}
```

## 接口

### 类型接口

```js
interface LabeledValue {
  label: string;
}

function printLabel(labeledObj: LabeledValue) {
  console.log(labeledObj.label);
}
```

### 可选属性

```js
interface SquareConfig {
  color?: string;
  width?: number;
}
```

### 只读属性

```js
interface Point {
    readonly x: number;
    readonly y: number;
}

let ro: ReadonlyArray<number> = [1, 2, 3, 4];
```

### 额外的属性检查

```js
interface SquareConfig {
    color?: string;
    width?: number;
    [propName: string]: any;
}
```

### 函数类型

```js
interface SearchFunc {
  (source: string, subString: string): boolean;
}
let mySearch: SearchFunc;
mySearch = function(source: string, subString: string) {
  let result = source.search(subString);
  return result > -1;
}
```

### 可索引类型

使用 `number` 作索引

```js
interface StringArray {
  [index: number]: string;
}

let myArray: StringArray;
myArray = ["Bob", "Fred"];

let myStr: string = myArray[0];
```

使用 `number` and `sting` 作索引

```js
class Animal {
    name: string;
}
class Dog extends Animal {
    breed: string;
}

// 错误：使用数值型的字符串索引，有时会得到完全不同的Animal!
interface NotOkay {
    [x: number]: Animal;
    [x: string]: Dog;
}
```

将索引签名设置为只读

```js
interface ReadonlyStringArray {
    readonly [index: number]: string;
}
let myArray: ReadonlyStringArray = ["Alice", "Bob"];
myArray[2] = "Mallory"; // error!
```

### 实现类接口

```js
interface ClockInterface {
    currentTime: Date;
}

class Clock implements ClockInterface {
    currentTime: Date = new Date();
    constructor(h: number, m: number) { }
}
```

在接口中描述一个方法

```js
interface ClockInterface {
    currentTime: Date;
}

class Clock implements ClockInterface {
    currentTime: Date = new Date();
    constructor(h: number, m: number) { }
}
```

### 继承接口

```js
interface Shape {
    color: string;
}

interface Square extends Shape {
    sideLength: number;
}

let square = <Square>{};
square.color = "blue";
square.sideLength = 10;
```

### 混合类型

```js
interface Counter {
    (start: number): string;
    interval: number;
    reset(): void;
}

function getCounter(): Counter {
    let counter = <Counter>function (start: number): string { return '' };
    counter.interval = 123;
    counter.reset = function () { };
    return counter;
}

let c = getCounter();
c(10);
c.reset();
c.interval = 5.0;
```

## 类

基础用法

```js
class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    greet() {
        return "Hello, " + this.greeting;
    }
}

let greeter = new Greeter("world");
```

### 继承和重写

```js
class Animal {
    name: string;
    constructor(theName: string) { this.name = theName; }
    move(distanceInMeters: number = 0) {
        console.log(`${this.name} moved ${distanceInMeters}m.`);
    }
}

class Snake extends Animal {
    constructor(name: string) { super(name); }
    move(distanceInMeters = 5) {
        console.log("Slithering...");
        super.move(distanceInMeters);
    }
}

class Horse extends Animal {
    constructor(name: string) { super(name); }
    move(distanceInMeters = 45) {
        console.log("Galloping...");
        super.move(distanceInMeters);
    }
}

let sam = new Snake("Sammy the Python");
let tom: Animal = new Horse("Tommy the Palomino");

sam.move();
tom.move(34);
```

