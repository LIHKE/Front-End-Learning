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
