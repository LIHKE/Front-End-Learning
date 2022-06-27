# 高阶 JS 知识点

## 1. 面向对象

### a. 面向过程编程 POP（Process Oriented Programming）

分析步骤，按步骤解决问题，如单片机

### b. 面向对象 OOP（Object Oriented Programming）

先找出对象，并写出这些对象的功能，以功能划分问题

面向对象的特性：

- 封装性（Encapsulation）
- 继承性（Inheritance）
- 多态性（Polymorphism）

## 2。ES6 中的类和对象

JS 中，对象是一组无序的相关属性和方法的集合，所有事物都是对象

### a. 对象

对象由属性和方法组成的：

- 属性：事物的特征，在对象中用属性表示（名词）
- 方法：事物的行为，在对象中用方法来表示（动词）

### b. 类 class

用 class 来声明一个类

### c. 创建一个类

类里有个构造函数 constructor，当 new 一个对象的时候会自动执行，constructor 里不用写 return

_Note：在 ES5 里没有类的概念，但是有构造函数，可以当作是类，ES6 后引入类，类里也有构造函数，与 C#一致_

```
Class Star {
    constructor(uname){
        this.name = uname;
    }
    sing(song){
        console.log('唱歌: ' + song);
    }
}

var ldh = new Star('刘德华');
console.log(ldh.name);
ldh.sing('冰雨');
```

（1）类里面的函数不需要写 function

（2）多个方法之间不需要添加逗号

### d. 类的继承

（1）extends：用来继承父类：

```
class Father{
    constructor(){

    }
    money(){
        console.log(100);
    }
}

class Son extends Father{

}

var son = new Son();
son.money();
```

（2）super：用来访问和调用对象父类上的函数。可以调用父类的构造函数，也可以调用普通函数

- super()**写在子类构造函数里**就能够调用父类的构造函数

```
class Father{
    constructor(x,y){
        this.x = x;
        this.y = y;
    }
    sum(){
        console.log(this.x + this.y);
    }
}

class Son extends Father{
    constructor(x,y){
        super(x,y); //调用了父类中的构造函数，将x和y传入父类的构造函数
    }
}

//将1，2传入子类的构造函数，里面调用了父类的构造函数，将1，2传入父类的x，y中（传入父类构造函数中的this.x和this.y）
var son = new Son(1,2);

//子类调用了父类的函数，此时由于已经将参数传入父类的属性x和y中，因此调用父类方法成立
son.sum();
```

- super()**写在子类普通函数里**就能够调用父类的普通函数

```
class Father{
    say(){
        return '我是爸爸';
    }
}

class Son extends Father{
    say(){
        //调用父类的普通方法super.say()
        console.log(super.say() + ‘的儿子’);
    }
}

var son = new Son();
son.say();
```

继承中的属性或者方法查找原则：就近原则

- 继承中，如果实例化子类输出一个方法，先看子类有没有这个方法，如果有就先执行子类的

- 继承中，如果子类里面没有，就去查找父类有没有这个方法，如果有就执行父类的这个方法

（3）子类扩展方法

子类继承父类方法同时扩展出另一个方法。
子类在构造函数中使用 super，必须放到 this 前面（必须先调用父类的构造方法，再使用子类构造方法）

```
class Father{
    constructor(x,y){
        this.x = x;
        this.y = y;
    }
    sum(){
        console.log(this.x + this.y);
    }
}

class Son extends Father{
    constructor(x,y){
        //super必须在子类this之前调用
        super(x,y);
        //才能将传参给到子类的属性this.x和this.y中
        this.x = x;
        this.y = y;

    }
    subtract(){
        console.log(this.x - this.y);
    }
}
var son = new Son(5,3);
son.subtract();
son.sum();
```

### e. ES6 中类和对象注意点

（1）ES6 中类没有变量提升，必须先定义类才能实例化

（2）类里面的共有属性和方法一定要加 this 使用

（3）类里面的 this 指向问题：

constructor 里的 this 指向实例对象，方法里的 this 指向这个方法的调用者

example：在构造函数中想调用 sing()方法，加 this。在 sing()方法里调用这个类的属性 name，需要加 this

```
 <button>ClickMe</button>
 <script>
class Star{
    //constructor里面的this指向的是创建的实例对象
    constructor(uname){
        this.name = uname;
        this.btn = document.querySelector('button');
        this.btn.click(this.sing);
    }
    sing(){
        //这个方法里this指向btn这个按钮，因为这个按钮调用了这个函数
        console.log(this.name);
    }
    dance(){
        //这个方法里this指向的是创建的实例对象
        console.log(this);
    }
}
</script>
```
