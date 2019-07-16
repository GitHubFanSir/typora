ES标准中不包含 DOM 和 BOM的定义，只涵盖基本数据类型、关键字、语句、运算符、内建对象、内建函数等通用语法。

ECMAScrip(变量、语句、基本类型）

W3C(dom、document.getElementById、window.alert())

Node.js (Ecma+服务器端扩展）

flash (ECMA + ActionScript）

浏览器（ECMA +DOM)jscript/javascript



flash  加密  跨域(h5也可以)



ECMAScript 6.0（以下简称 ES6）是 JavaScript 语言的下一代标准，已经在 2015 年 6 月正式发布了。它的目标，是使得 JavaScript 语言可以用来编写复杂的大型应用程序，成为企业级开发语言。

3版本语法很宽松，4版本用面向对象的思想做了改版，但是因为变化太大，并没有流行起来。5版本对3版本做了一些漏洞的修复和语法的改进。但是因为前端开发越来越复杂，所以面向对象的思想还是要继续使用。因而，对4版本做了改进，发布了6版本。然而很多浏览器或者其他的js环境并不支持6，所以我们可以用6版本的语法编写代码，然后用一个工具进行转码，转码到低版本。



# 用let声明变量

// var 声明的变量没有**代码块级别**的局部作用域
// let 声明的变量  有**代码块级别**的局部作用域

```js
{
    var a = 0
    let b = 1
}
console.log(a)  // 0
console.log(b)  // ReferenceError: b is not defined
```



// var 可以声明多次
// let 只能声明一次（类似java）

```js
var m = 1
var m = 2
let n = 3
let n = 4
console.log(m)  // 2
console.log(n)  // Identifier 'n' has already been declared
```

// var 会变量提升
// let 不存在变量提升

```js
console.log(x)  //undefined
var x = 'apple' //var会将变量的定义提升至作用域内的第一行

console.log(y)  //ReferenceError: y is not defined
let y = 'banana'
```

//js中的五钟基本数据类型

//number（整形+浮点型）、string（包含字符和字符串，不分双引号和单引号）、 Doolean,undefined（声明但是没有给值）、null（dom获取不到元素，或者直接声明null）

//Number、String、Boolein

# const声明常量（只读变量）

// 1、声明之后不允许改变 

```
const PI = '3.1415926'
PI = 3  // TypeError: Assignment to constant variable.
```

// 2、一但声明必须初始化，否则会报错

```
const MY_AGE  // SyntaxError: Missing initializer in const declaratio
```



# 解构赋值

解构赋值是对赋值运算符的扩展。

他是一种针对数组或者对象进行模式匹配，然后对其中的变量进行赋值。

在代码书写上简洁且易读，语义更加清晰明了；也方便了复杂对象中数据字段获取。

### //1、数组解构

// 传统

```
let arr = [1, 2, 3]
let a = arr[0]
let b = arr[1]
let c = arr[2]
console.log(a, b, c)
```

// ES6

```
let [x, y, z] = [1, 2, 3]
console.log(x, y, z)
```

### //2、对象解构

let user = {name: 'Helen', age: 18}
// 传统

```
let name1 = user.name
let age1 = user.age
console.log(name1, age1)
```

// ES6

```
let { name, age } =  user//注意：解构的变量必须和user中的属性同名
console.log(name, age)
```

# 模板字符串

模板字符串相当于加强版的字符串，用反引号  ` ,除了作为普通字符串，还可以用来定义多行字符串，还可以在字符串中加入变量和表达式。
// 字符串插入变量和表达式。变量名写在 ${} 中，${} 中可以放入 JavaScript 表达式。
//模板字符串
//1、跨行拼接字符串
let centence = `无法访问此网站 192.168.255.1 的响应时间过长。
请试试以下办法：

  检查网络连接
检查代理服务器和防火墙
运行 Windows 网络诊断
ERR_CONNECTION_TIMED_OUT`

console.log(centence)

//2、插值表达式

```js
let name = 'Helen'
let age = 18
// let info = "My name is " + name + ", I'm " + age + " years old"
let info = `My name is ${name}, I'm ${age} years old`
console.log(info)
```

# 声明对象简写

声明对象简写

```js
const age = 12
const name = 'Amy'

// 传统
const person1 = {age: age, name: name}
console.log(person1)
```

// ES6

```js
const person2 = {age, name}
console.log(person2) //{age: 12, name: 'Amy'}
```



# 定义方法简写

// 传统

```js
const person1 = {
    sayHi:function(){
        console.log('Hi')
    }
}
person1.sayHi();//'Hi'
```

// ES6

```js
const person2 = {
    sayHi(){   //es6认为，不带括号的就是属性，带括号的就是方法
        console.log('Hi')
    }
}
person2.sayHi()  //'Hi'
```



# 对象拓展运算符

拓展运算符（...）用于取出参数对象所有可遍历属性然后拷贝到当前对象。

```js
let person = {name: 'Amy', age: 15}
// let someone = person //引用赋值
let someone = { ...person } //对象拷贝
someone.name = 'Helen' 
console.log(person)  //{name: 'Amy', age: 15}
console.log(someone)  //{name: 'Helen', age: 15}
```



# 函数的默认参数

```js
function showInfo(name, age = 17) {
    console.log(name + "," + age)
}

// 只有在未传递参数，或者参数为 undefined 时，才会使用默认参数
// null 值被认为是有效的值传递。
showInfo("Amy", 18)  // Amy,18
showInfo("Amy")     // Amy,17
showInfo("Amy", undefined) // Amy,17
showInfo("Amy", null)  // Amy, null
```



# 箭头函数

箭头函数提供了一种更加简洁的函数书写方式。基本语法是：

参数 => 函数体

箭头函数多用于**匿名函数**的定义

```js
let arr = ["10", "5", "40", "25", "1000"]
arr1 = arr.sort()
console.log(arr1)

//上面的代码没有按照数值的大小对数字进行排序，
//要实现这一点，就必须使用一个排序函数
arr2 = arr.sort(function(a,b){
    return a - b
})
console.log(arr2)
```


