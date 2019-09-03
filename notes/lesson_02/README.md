# TS中的变量类型

**注意：写TS代码必须指定类型。**

## 1.1 TS中的类型
|名称|写法|备注|
|-|-|-|
|布尔类型|```let a:boolean=true```|
|数字类型|```let a:number=123```|
|字符串类型|```let a:string='hello'```|
|数组类型|1)```number[]```<br>2)```Array<number>```|
|元组类型(tuple)|```[number, string]```|**元组类型也属于数组的一种。**<br>元组类型可以给数组中**每一个位置指定一个类型**|
|枚举类型(enum)|```enum 枚举名{ 标识符[=整型常量], 标识符[=整型常量], ..., 标识符[=整型常量]}```|

**元组类型**
```js
let arr:[number, string] = [123, 'hello'];
let arr1:[number, string] = ['hello', 'world'];      // 报错
let arr2:[number, string] = ['hello', 123];          // 报错
```
**枚举类型**
```js
enum flag {success=1, error=2};
let result:flag = flag.success;
console.log(result);        // 1
```
如果标识符没有赋值，那么它的值就是下标
```js
enum colors {red, blue, 'yellow'};
let c:colors = colors.blue;
console.log(c);             // 1
```
也可以单独对某一枚举标识符进行赋值
```js
enum colors {red, blue=3, 'yellow'};
let c:colors = colors.blue;
console.log(c);             // 3
```
如果对某一枚举标识符进行赋值之后，其后的枚举标识符的值也会改变
```js
enum colors {red, blue=3, 'yellow'};
let c:colors = colors.yellow;
console.log(c);             // 4
c = colors.red;
console.log(c);             // 0
```