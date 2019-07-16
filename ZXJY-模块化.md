# 模块化简介

### 模块化产生的背景

随着网站逐渐变成"互联网应用程序"，嵌入网页的Javascript代码越来越庞大，越来越复杂。

Javascript模块化编程，已经成为一个迫切的需求。理想情况下，开发者只需要实现核心的业务逻辑，其他都可以加载别人已经写好的模块。

但是，Javascript不是一种模块化编程语言，它不支持"类"（class），包（package）等概念，也不支持"模块"（module）。

### 模块化规范

- CommonJS模块化规范
- ES6模块化规范

# CommonJS模块规范

每个文件就是一个模块，有自己的作用域。在一个文件里面定义的变量、函数、类，都是私有的，对其他文件不可见。

### 1、创建“module”文件夹

### 2、导出模块

创建 modularization-common-js/四则运算.js

```js
// 定义成员：
var sum = function(a,b){
    return a + b
}
var subtract = function(a,b){
    return a - b
}
var multiply = function(a,b){
    return a * b
}
var divide = function(a,b){
    return a / b
}
```

导出模块中的成员

```js
// 导出成员，module可以省略
module.exports = {
    sum: sum,
    subtract: subtract,
    multiply: multiply,
    divide: divide
}
```

简写

```js
//简写
module.exports = {
    sum,
    subtract,
    multiply,
    divide
}
//如果只导出一个方法，还可以这样写
exports.info = function(a,b){
    return a + b
}
```

### 3、导入模块

创建 modularization-common-js/引入模块.js

```js
//引入模块，注意：当前路径必须写 ./
const m = require('./四则运算.js')
console.log(m)

const result1 = m.sum(1, 2)
const result2 = m.subtract(1, 2)
console.log(result1, result2)
```

### 4、运行程序

```
node 引入模块.js
```


总结：CommonJS使用 exports 和require 来导出、导入模块。

模块化后的js代码，就不能直接在html页面中进行使用了。具体怎么用老师还没说（可能就是webpack吧）



# ES6模块化规范

ES6使用 export 和 import 来导出、导入模块。

创建 modularization-es6 文件夹

注意：模块化后的程序时无法直接运行的，因为ES6的模块化无法在Node.js中执行，需要用Babel编辑成ES5后再执行。

### 第一种写法

##### 1、导出模块

创建 src/userApi.js 文件

```js
export function getList() {
    console.log('获取数据列表')
}

export function save() {
    console.log('保存数据')
}
```

##### 2、导入模块

创建 src/userComponent.js文件

```js
//只取需要的方法即可，多个方法用逗号分隔
import { getList, save } from './userApi.js'
getList()
save()
```



### 第二种写法

##### 1、导出模块

创建 src/userApi2.js

```js
export default {
    getList() {
        console.log('获取数据列表2')
    },

    save() {
        console.log('保存数据2')
    }
}
```
##### 2、导入模块

创建 src/userComponent2.js
```js
import user from "./userApi2.js"
user.getList()
user.save()
```

##### 3、转码

创建目标文件夹，然后在package.json中写上如下命令

```json
{
    // ...
    "scripts": {
       "build": "babel src -d dist"
       "build":"babel modularization-es6/src -d dist"    
        //注意：最好都写正斜杠，因为反斜杠只在windows中可以用。
    }
}
```

##### 4、运行build脚本实现转码

```
npm run build
```

##### 5、运行程序测试代码

```
node dist/userComponent.js
```

