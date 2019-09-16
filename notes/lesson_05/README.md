# TS中的类(下)

## TS中定义类

[代码示例](../../demo/lesson_05/demo1/index.ts)
```ts
class Person {
    /* 属性，前面省略了public关键字 */
    name: string;

    /* 构造函数，实例化类的时候调用的函数 */
    constructor(name: string) {
        this.name = name;
    }
}
```

## TS中实现继承(extends、super)

[代码示例](../../demo/lesson_05/demo2/index.ts)

父类和子类有同名方法时，子类方法覆盖父类方法。

## 类里面的修饰符

typescript里面定义属性的时候给我们提供了三种修饰符

|修饰符|说明|
|-|-|
|public|公有类型，在当前类里面、子类、类外面都可以访问|
|protected|保护类型，在当前类里面、子类可以访问，在类外部不能访问|
|private|私有类型，在当前类里面可以访问，子类、类外部不能访问|

属性如果不加修饰符，则默认为public。