# 进阶 JS 知识点

## 1. Web APIs 和 JS 基础关联性

### 1.1 JS 的组成

a. JS 语法：ECMAScript

基础语法

b. WebAPI：DOM, BOM

WebAPI 是 JS 的应用，大量使用 JS 语法做交互效果

## 2. API 和 Web API

### 2.1 API

API 是预先定义的函数，给程序员提供的一种工具，能更轻松实现想要完成的功能

### 2.2 Web API

是**浏览器**提供的一套操作浏览器功能（BOM）和页面元素的 API（DOM）

现阶段主要针对浏览器做交互效果。

如：浏览器弹出警示框，直接使用 alert('弹出')

## 3. DOM

### 3.1 简介

文档对象模型（Document Object Model），是 W3C 组织推荐的处理可扩展标记语言（HTML 或 XML）的标准**编程接口**。通过 DOM 接口可以改变网页的内容，结构和样式。

文档：一个页面解释一个文档（document）

元素：页面所有标签都是元素（element）

节点：网页中所有的内容都是节点（标签，属性，文本，注释等）（node）

### 3.2 获取元素

- 根据 ID 获取

document.getElementById('id')

- 根据标签名获取

document.getElementsByTagName('Tag 名')

- 通过 HTML5 新增的方法获取（IE9 以上）

a. document.getElementsByClassName('类名')

b. document.querySelector('选择器') //根据选择器返回第一个元素对象，如：

    document.querySelector('.类名')

    document.querySelector('#id')

    document.querySelector('标签名')

c. document.querySelectorAll('选择器')//根据选择器返回所有元素对象

- 特殊元素获取，一般只有一个 body 和 html 标签

a. body 元素：document.body;

b. html 元素：document.documentElement;
