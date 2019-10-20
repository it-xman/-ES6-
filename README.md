# ES6-UnderStanding

# 第一章  块级作用域绑定

## var声明及变量提升机制

## 块级声明

- ### let声明

- ### 禁止重声明

- ### const声明

- ### 临时死区

## 循环中的块级作用域绑定

- ### 循环中的函数

- ### 循环中的let声明

- ### 循环中的const声明

## 全局块作用域绑定

## 块级绑定最佳实践的进化

## 小结

# 第二章  字符串和正则表达式

## 更好的Unicode支持

## 其他字符串变更

## 其他正则表达式语法变更

## 模板字面量

## 小结

# 第三章  函数

## 函数形参的默认值

## 处理无命名参数

## 增强的Function构造函数

## 展开运算符

## name属性

## 明确函数的多用途

## 块级函数

## 箭头函数

## 尾调用优化

## 小结

# 第四章  扩展对象的功能性

## 对象类别

## 对象字面量语法扩展

## 新增方法

## 重复的对象字面量属性

## 自有属性枚举顺序

## 增强对象原型

## 正式的方法定义

## 小结

# 第五章  解构：使数据访问更便捷

## 为何使用解构功能

解构是一种打破数据结构，将其拆分成更小部分的过程。

## 对象解构

语法：在一个赋值操作符左边放置一个对象字面量

```javascript
let node = {
  type : 'Identifier',
  name : 'foo'
};

let {type, name} = node;

console.log(type);//'Identifier'
console.log(name);//'foo'
```

node.type的值被赋值给type，node.name的值被赋值给name。

type和name都是局部声明的变量，用来从options对象读取相应属性名称的值。

##### 注意：

##### 如果使用var、let或const解构声明变量，必须要提供初始化程序，即等号右侧的值。

```javascript
//全部报错  语法错误
var {type, name};
let {type, name};
const {type, name};
```

##### 如果不使用解构功能，则var和let声明不强制要求提供初始化程序，但是对于const声明，无论怎样，必须提供初始化程序。

- ### 解构赋值

  - 可以在给变量赋值时使用解构语法

    ```javascript
    let node = {
      type : 'Identifier',
      name : 'foo'
    };
    type = 'Literal';
    name = 5;
    
    //要用小括号括住解构赋值语句，JavaScript引擎将大花括号视为一个代码块，语法规定，代码块不能出现在赋值语句左侧，添加小括号可以将块语句转化成一个表达式，从而实现解构赋值的过程。
    ({type, name} = node);
    
    console.log(type); //'Identifier'
    console.log(name); //'foo'
    ```

  - 解构赋值表达式的值与表达式右侧的值相等，在任何可以使用值的地方都可以使用解构表达式。

    ```javascript
    let node = {
      type : 'Identifier',
      name : 'foo'
    };
    
    type = 'Literal';
    name = 5;
    
    function outputInfo(value) {
      console.log(value === node); //true
    }
    outputInfo({type, name} = node);
    
    console.log(type); //'Identifier'
    console.log(name); //'foo'
    ```

    - 调用outputInfo()函数时传入了一个解构表达式，由于JavaScript表达式的值为=右侧的值，因此传入的参数等同于node，且变量type和name被重新赋值，最终将node传入outputInfo()函数。

  - ##### 注意：解构赋值表达式(=右侧的表达式)如果为null或者undefined会导致程序抛出错误。任何尝试读取null或undefined的属性的行为都会触发运行时错误。

- ### 默认值

  - 使用解构赋值表达式时，如果指定的局部变量名称在对象中不存在，那么这个局部变量会被赋值为undefined。

    ```javascript
    let node = {
      type : 'Identifier',
      name : 'foo'
    };
    
    let {type, name, value} = node;
    
    console.log(type); //'Identifier'
    console.log(name); //'foo'
    console.log(value); //undefined
    ```

  - 当指定的属性不存在时，可以随意定义一个默认值，在属性名称后面添加一个等号和响应的默认值即可

    ```javascript
    let node = {
      type : 'Identifier',
      name : 'foo'
    };
    
    let {type, name, value = true} = node;
    
    console.log(type); //'Identifier'
    console.log(name); //'foo'
    console.log(value); //true
    ```

    - 为变量value设置了默认值true，只有当node上没有该属性或者该属性的值为undefined时，该值才生效，此处没有node.value属性，因为value使用了预设的默认值。

- ### 为非同名局部变量赋值

  - 

- ### 嵌套对象解构

## 数组解构

- ### 解构赋值

- ### 默认值

- ### 嵌套数组解构

- ### 不定元素

## 混合解构

## 解构参数

- ### 必须传值的解构参数

- ### 解构参数的默认值

## 小结

# 第六章  Symbol和Symbol属性

# 第七章  Set集合与Map集合

# 第八章  迭代器和生成器

# 第九章  JavaScript中的类

# 第十章  改进的数组功能

# 第十一章  Promise与异步编程

# 第十二章  代理（Proxy）和反射（Reflection）API

# 第十三章  用模块封装代码