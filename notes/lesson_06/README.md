# TS中的接口

**接口的作用**

在面向对象的编程中，接口是一种规范的定义，它定义了行为和动作的规范，在程序设计里面，接口起到一种限制和规范的作用。接口定义了某一批类所需要遵守的规范，接口不关心这些类的内部状态数据，也不关心这些类里面方法的实现细节，它只规定这批类里必须提供某些方法，提供这些方法的类就可以满足实际需要。TS中的接口类似于java，同时还增加了更灵活的接口类型，包括属性、函数、可索引和类等。

接口也是定义标准

**TS中的接口**

- 属性类接口
- 函数类接口
- 可索引接口
- 类类型接口
- 接口扩展

## 属性接口

对json的约束。

TS中定义方法：

```ts
function printLabel(): void{
    console.log('printLabel');
}
printLabel();
```

TS中定义方法传入参数

```ts
function printLabel(label: string): void {
    console.log(label);
}
printLabel('hello world');
```

TS中自定义方法传入参数，对json进行约束

```ts
function printLabel(labelInfo: {label: string}): void {
    console.log(labelInfo.label);
}
printLabel('hello world');          /* 错误写法 */
printLabel({name: 'hello world'});  /* 错误写法 */
printLabel({label: 'hello world'}); /* 正确写法 */
```

## 对批量方法传入参数进行约束

接口：行为和动作的规范，对批量方法进行规范。

[示例代码](../../demo/lesson_06/demo1/index.ts)
```ts
/* 就是传入对象的约束，属性接口 */
interface FullName {
    firstName: string;
    secondName: string;
}

/* 必须传入对象。包含firstName和secondName */
function printName(name: FullName):void {
    console.log(name.firstName + '---' + name.secondName);
}

printName('123');               /* 错误 */
printName({                     /* 报错 */
    age: 20,                    // 不能包含age属性，只能包含firstName和secondName
    firstName: 'hello',
    secondName: 'world'
})

const obj = {
    age: 20,
    firstName: 'hello',
    secondName: 'world'
}
printfName(obj);                /* 正确 */
```
接口中定义的属性不能多不能少。（上面在外部声明一个对象可以多设置几个属性，但是在函数内使用时依然无法使用接口中未定义的属性）

## 接口可选属性

```ts
interface FullName {
    firstName: string;
    secondName?: string; 
}

function printName(name: FullName):void {
    console.log(name.firstName);
}

const obj = {
    firstName: 'hello'
}
printName(obj);                                                 /* 正确 */
printName({firstName: 'hello', secondName: 'world'});           /* 正确 */
```

## 举个例子
用接口定义ajax参数。略。

## 函数类型接口
对方法传入的`参数`以及`返回值`进行约束。

加密的函数类型接口：

[代码示例](../../demo/lesson_06/demo2/index.ts)
```ts
interface Encrypt {
    (key: string, value: string): string;
}

const md5: Encrypt = function(key: string, value: string): string {
    // 模拟操作
    return key + value;
}

console.log(md5('hello', 'world'));
```

