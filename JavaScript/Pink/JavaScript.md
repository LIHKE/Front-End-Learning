# JavaScript

## 1. 初识 Javascript

### 1.1 浏览器执行 JS

浏览器两部分组成：

- 渲染引擎：用来解析 HTML 与 CSS，俗称内核，比如 chome 的 blink
- JS 引擎：也称为 JS 解释器，用来读取网页中的 JS 代码，处理后运行，如 chrome 的 V8

浏览器本身不执行 JS 代码，是通过 JS 引擎来执行，**逐行解释执行**

### 1.2 JS 的组成

- ECMASCript: Javascript 语法
- DOM （JS API）：文档对象模型，对页面上元素进行操作
- BOM（JS API）：浏览器对象模型，操作浏览器窗口

### 1.3 JS 三种书写位置

- 行内式 JS

  - 写在 HTML 标签的时间属性中
  - 在 HTML 中推荐使用**双引号**，JS 中推荐使用**单引号**
  - 可读性差

- 内嵌式

- 外部式

  - 利于 HTML 页面代码结构化，把打断 JS 独立到 HTML 页面之外，也方便复用
  - 引用外部 JS 文件的 script 标签中间不可以写代码：

    ```
    <script src="my.js">这里不能写代码</script>
    ```

---

## 2. Javascript 输入输出语句

|       方法       |              说明              |  归属  |
| :--------------: | :----------------------------: | :----: |
|    alert(msg)    |        浏览器弹出警示窗        | 浏览器 |
| console.log(msg) |    浏览器控制台打印输出信息    | 浏览器 |
|   prompt(info)   | 浏览器弹出输入框，用户可以输入 | 浏览器 |

---

## 3. 变量

本质：程序在内存中申请的一块用来存放数据的空间

### 3.1 声明多个变量：

- 使用逗号来区隔：

  ```
      var name = Eric,
      age = 18;
  ```

- JS 允许不声明直接赋值使用（全局变量）
  ```
      name = Eric;
  ```

---

## 4. 数据类型

### 4.1 undefined

- undefined 和数字相加，结果会是 NaN（Not A Number）;
  undefined 和 string 相加，结果会是 string

  ```
  var variable = undefined;
  console.log(variable + 'pink');
  console.log(variable + 1);
  ```

  结果是：

  ```
  undefinedpink
  NaN
  ```

### 4.2 null

- null 空值，里面存的值为空

  ```
  var space = null;
  console.log(space + 'pink');
  console.log(spcae + 1);
  ```

  结果是：

  ```
  nullpink
  1
  ```

---

## 5. 运算符

### 5.1 递增递减运算符

#### 5.1.1 前置递增

++num 先自加，后返回值

```
var age = 10;
console.log('++age + 10');
```

结果：

```
21
```

#### 5.1.2 后置递增

num++ 先返回原值，后自加

```
var age = 10;
console.log('age++ + 10');
```

结果：

```
20
```

但 age 的值变为 11

---

## 6. 函数

### 6.1 return

函数如果有 return，则返回 return 后的值，没有 return 则返回 undefined

### 6.2 arguments

当不确定有多少个参数传递的时候可以用 arguments 来获取。其是当前函数的一个内置对象。arguments 对象中存储了传递的所有**实参**。

### 6.3 函数两种声明方式：

1. 利用函数关键字自定义函数（命名函数）：

```
function fn(){

}
fun();
```

2. 函数表达式（匿名函数，变量名非函数名）
   跟声明变量差不多，只不过变量里面存的是函数

```
var fun = function(){

}
fun()  //这里的fun是变量名而非函数名，不过只是调用的时候使用变量名
```

---

## 7. 作用域

1. 全局变量：

2. 局部变量（函数作用域）：

   \*特殊情况：在函数内没有 var 的变量是全局变量

3. 从执行效率来看：

- 全局变量只有在浏览器关闭的时候才会销毁
- 局部变量当程序执行完毕便会销毁，节约内存

4. 块级作用域：在 es6 里新增

   在{}里的变量，外面不能调用

5. 作用域链

   内部函数能访问外部函数的变量

---

## 8. 预解析

JS 是由浏览器中的 Javascript 解析器来执行的。JavaScript 解析器在运行

1. JavaScript 代码的时候分为两步：预解析和代码执行

- 预解析：js 引擎会把 js 里面所有的 var 还有 function 提升到当前作用域的最前面
- 代码执行：按照代码书写的顺序从上往下执行

2. 预解析分为 变量预解析（变量提升）和函数预解析（函数提升）

- 变量提升：把所有变量声明提升到当前的作用域最前面，不提升赋值
- 函数提升：把所有函数声明提升到当前的作用域最前面，不调用函数
