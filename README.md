# Java 前端

HTML/CSS为基础

JavaScript为重点

Vue2,Vue3 React 为前端框架，选择一个学习即可



## 一 HTML 超文本标记语言

HTML：定义网页的内容和结构

### 1.1 HTML元素

HTML由一系列的元素组成

	<p>hello world!</p>

* 整体称之为元素
* `<p>` 和 `</p>` 分别称为起始和结束标签
* 标签包围起来的 Hello, world 称之为内容

* p 是预先定义好的 html 标签，作用是将内容作为一个单独的段落

元素还可以有属性，如

```html
<p id="p1">Hello, world!</p>
```

* 属性一般是预先定义好的，这里的 id 属性是给元素一个唯一的标识



元素之间可以嵌套，如

```html
<p>HTML 是一门非常<b>强大</b>的语言</p>
```

错误嵌套写法：

```html
<p>HTML 是一门非常<b>强大的语言</p></b>
```



不包含内容的元素称之为空元素，如

```html
<img src="1.png">
<img src="1.png"/>
```

* img 作用是用来展示图片
* src 属性用来指明图片路径



### 1.2 HTML页面

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>测试页面</title>
  </head>
  <body>
    <p id="p1">Hello, world!</p>
    <img src="1.png">
  </body>
</html>
```

* `html` 元素囊括了页面中所有其它元素，整个页面只需一个，称为根元素
* `head` 元素包含的是那些不用于展现内容的元素，如 `title`，`link`，`meta` 等
* `body` 元素包含了对用户展现内容的元素，例如后面会学到的用于展示文本、图片、视频、音频的各种元素

### 1.3 常见元素

#### 1.3.1文本

##### Heading

```html
<h1>1号标题</h1>
<h2>2号标题</h2>
<h3>3号标题</h3>
<h4>4号标题</h4>
<h5>5号标题</h5>
<h6>6号标题</h6>
```



##### Paragraph

```html
<p>段落</p>
```



##### List

无序列表 unordered list

```html
<ul>
    <li>列表项1</li>
    <li>列表项2</li>
    <li>列表项3</li>
</ul>
```

有序列表

```html
<ol>
    <li>列表项1</li>
    <li>列表项2</li>
    <li>列表项3</li>
</ol>
```

多级列表

```html
<ul>
    <li>
    	北京市
        <ul>
            <li>海淀区</li>
            <li>朝阳区</li>
            <li>昌平区</li>
        </ul>
    </li>
    <li>
    	河北省
        <ul>
            <li>石家庄</li>
            <li>保定</li>
        </ul>
    </li>
</ul>
```



##### Anchor

锚，超链接

```html
<a href="网页地址">超链接文本</a>
```

* 本地网页地址
* 互联网网页地址
* 页面内锚点 #id （id 为元素的属性）

#### 1.3.2 多媒体

##### Image

```html
<img src="文件路径">
```

src 格式有 3 种

* 文件地址

* data URL，格式如下

  ```
  data:媒体类型;base64,数据
  ```

* object URL，需要配合  javascript  使用

##### Video

```html
<video src="文件路径"></video>
```

##### Audio

```html
<audio src="文件路径"></audio>
```



#### 1.3.3 表单

##### 作用与语法

表单的作用：**收集**用户填入的**数据**，并将这些数据**提交给服务器**

表单的语法

```html
<form action="服务器地址" method="请求方式" enctype="数据格式">
    <!-- 表单项 -->
    
    <input type="submit" value="提交按钮">
</form>
```

* method 请求方式有 
  * get （默认）提交时，数据跟在 URL 地址之后
  * post 提交时，数据在请求体内
* enctype 在 post 请求时，指定请求体的数据格式
  * application/x-www-form-urlencoded（默认）
  * multipart/form-data
* 其中表单项提供多种收集数据的方式
  * 有 name 属性的表单项数据，才会被发送给服务器



##### 常见的表单项

文本框

```html
<input type="text" name="uesrname">
```

密码框

```html
<input type="password" name="password">
```

隐藏框

```html
<input type="hidden" name="id">
```

日期框

```html
<input type="date" name="birthday">
```

单选

```html
<input type="radio" name="sex" value="男" checked>
<input type="radio" name="sex" value="女">
```

多选

```html
<input type="checkbox" name="fav" value="唱歌">
<input type="checkbox" name="fav" value="逛街">
<input type="checkbox" name="fav" value="游戏">
```

文件上传

```html
<input type="file" name="avatar">
```



### 1.4 HTTP请求

#### 1.4.1 请求组成

请求由三部分组成

1. 请求行
2. 请求头
3. 请求体

可以用 telnet 程序测试

#### 1.4.2 请求方式与数据格式

##### get 请求示例

```
GET /test2?name=%E5%BC%A0&age=20 HTTP/1.1
Host: localhost
```

* %E5%BC%A0 是【张】经过 URL 编码后的结果

##### post 请求示例

```
POST /test2 HTTP/1.1
Host: localhost
Content-Type: application/x-www-form-urlencoded
Content-Length: 21

name=%E5%BC%A0&age=18
```

application/x-www-form-urlencoed 格式细节：

* 参数分成名字和值，中间用 = 分隔
* 多个参数使用 & 进行分隔
* 【张】等特殊字符需要用 encodeURIComponent() 编码为 【%E5%BC%A0】后才能发送



##### json 请求示例

```
POST /test3 HTTP/1.1
Host: localhost
Content-Type: application/json
Content-Length: 25

{"name":"zhang","age":18}
```



json 对象格式

```
{"属性名":属性值}
```

其中属性值可以是

* 字符串 ""
* 数字
* true, false
* null
* 对象
* 数组

json 数组格式

```
[元素1, 元素2, ...]
```



##### multipart 请求示例

```
POST /test2 HTTP/1.1
Host: localhost
Content-Type: multipart/form-data; boundary=123
Content-Length: 125

--123
Content-Disposition: form-data; name="name"

lisi
--123
Content-Disposition: form-data; name="age"

30
--123--
```

* boundary=123 用来定义分隔符
* 起始分隔符是 `--分隔符`
* 结束分隔符是 `--分隔符--`



##### 数据格式小结

客户端发送

* 编码 
  * application/x-www-form-urlencoded ：url 编码
  * application/json：utf-8 编码
  * multipart/form-data：每部分编码可以不同
* 表单只支持以 application/x-www-form-urlencoded 和 multipart/form-data 格式发送数据
* 文件上传需要用 multipart/form-data 格式
* js 代码可以支持任意格式发送数据 

服务端接收

* 对 application/x-www-form-urlencoded 和 multipart/form-data 格式的数据，Spring 接收方式是统一的，只需要用 java bean 的属性名对应请求参数名即可
* 对于 applicaiton/json 格式的数据，Spring 接收需要使用 @RequestBody 注解 + java bean 的方式



#### 1.4.3 session 原理

Http 无状态，有会话

* 无状态是指，请求之间相互独立，第一次请求的数据，第二次请求不能重用
* 有会话是指，客户端和服务端都有相应的技术，可以暂存数据，让数据在请求间共享

服务端使用了 session 技术来暂存数据

存

```
GET /s1?name=zhang HTTP/1.1
Host: localhost
```

取

```
GET /s2 HTTP/1.1
Host: localhost
Cookie: JSESSIONID=560FA845D02AE09B176E1BC5D9816A5D
```



session 技术实现身份验证

```mermaid
sequenceDiagram
participant Client
participant L as LoginController
participant i as LoginInterceptor
participant Session
rect rgb(200, 223, 255)
Client ->> +L : 登录请求
L ->> L : 检查用户名，密码，验证通过
L ->> +Session : 存入用户名
Session -->> -L: 
L -->> -Client: 登录成功
end
rect rgb(200, 190, 255)
Client ->> +i : 其它请求
i ->> +Session : 获取用户名
Session -->> -i : 
i ->> i: 用户名存在，放行
i -->> -Client : 
end
```







#### 1.4.4  jwt 原理

jwt 技术实现身份验证

```mermaid
sequenceDiagram
participant Client
participant L as LoginController
participant i as LoginInterceptor

rect rgb(200, 223, 255)
Client ->> +L : 登录请求
L ->> L : 检查用户名，密码，验证通过
L -->> -Client : 登录成功，返回token
end

rect rgb(150, 190, 155)
Client ->> +i : 其它请求，携带token
i ->> i : 校验token，校验无误，放行
i -->> -Client : 
end
```

生成 token

```
GET /j1?name=zhang&pass=123 HTTP/1.1
Host: localhost
```

校验 token

```
GET /j2 HTTP/1.1
Host: localhost
Authorization: eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJhZG1pbiJ9._1-P_TLlzQPb1_lCyGwplMZaKQ8Mcw_plBbYPZ3OX28
```



## 二 CSS

CSS： Cascading Style Sheets 级联（层叠）样式表，描述了网页的表现与展示效果

### 2.1 选择器

* type 选择器 - 根据标签名进行匹配（元素选择器）
* class 选择器 - 根据元素的 class 属性进行匹配

* id 选择器  - 根据元素的 id 属性进行匹配

### 2.2 属性和值

* background-color : red;
* ...
* display

### 2.3 布局

与布局相关的 html 元素

* div
* template



## 三 JavaScript（重点）

它是一种脚本语言，可以用来更改页面内容，控制多媒体，制作图像、动画等等

js 代码位置

```html
<script>
	// js 代码
</script>
```

引入 js 脚本

```html
<script src="js脚本路径"></script>
```

* 注意，到了框架之后，引入方式会有不同



### 3.1 变量与数据类型

#### 3.1.1 声明变量

##### 1) let :star:

```js
let 变量名 = 值;
```

* let 声明的变量可以被多次赋值，例如

```js
let a = 100;  // 初始值是 100
a = 200;	  // ok, 被重新赋值为 200
```

##### 2) const :star:

* const 修饰的叫常量，只能赋值一次

```js
const b = 300; // 初始值是 300
b = 400;	   // error, 不能再次赋值
```

* const 并不意味着它引用的内容不可修改，例如

```js
const c = [1,2,3];
c[2] = 4; 	        // ok, 数组内容被修改成 [1,2,4]
c = [5,6];			// error, 不能再次赋值
```

##### 3) var

var 声明的变量可以被多次赋值，例如

```js
var f = 100;
f = 200;
```



#### 3.1.2 基本类型

##### 1,2) undefined 和 null

* 执行表达式或函数，没有返回结果，出现 undefined
* 访问数组不存在的元素，访问对象不存在的属性，出现 undefined
* 定义变量，没有初始化，出现 undefined

例

```js
console.log(1);  	// 函数没有返回值, 结果是  undefined
let a = 10;		 	// 表达式没有返回值, 结果是 undefined
let b = [1,2,3];
console.log(b[10]); // 数组未定义元素是 undefined
let c = {"name":"张三"};
console.log(c.age); // 对象未定义属性是 undefined
let d;
console.log(d);		// 变量未初始化是 undefined
```

二者共同点

* 都没有属性、方法
* 二者合称 Nullish

二者区别

* undefined 由 js 产生
* null 由程序员提供



##### 3) string :star:

js 字符串三种写法

```js
let a = "hello";  // 双引号
let b = "world";  // 单引号
let c = `hello`;  // 反引号
```



html 代码如下，用 java 和 js 中的字符串如何表示？

```html
<a href="1.html">超链接</a>
```

java 显得比较繁琐

```java
String s1 = "<a href=\"1.html\">超链接</a>";

String s2 = """
    <a href="1.html">超链接</a>""";
```

js 就比较灵活

```js
let s1 = '<a href="1.html">超链接</a>';

let s2 = `<a href="1.html">超链接</a>`;
```



模板字符串（Template strings）

需求：拼接 URI 的请求参数，如

```
/test?name=zhang&age=18
/test?name=li&age=20
```

传统方法拼接

```js
let name = ; // zhang li ...
let age = ; // 18 20 ...

let uri = "/test?name=" + name + "&age=" + age;
```

模板字符串方式

```js
let name = ; // zhang li ...
let age = ; // 18 20 ...

let uri = `/test?name=${name}&age=${age}`;
```



##### 4,5) number 和 bigint:star:

number 类型标识的是双精度浮动小数，例如

```js
10 / 3;   // 结果 3.3333333333333335
```

既然是浮点小数，那么可以除零

```js
10 / 0;	  // 结果 Infinity 正无穷大
-10 / 0;  // 结果 -Infinity 负无穷大
```

浮点小数都有运算精度问题，例如

```js
2.0 - 1.1; // 结果 0.8999999999999999
```

字符串转数字

```js
parseInt("10"); 	// 结果是数字 10 
parseInt("10.5");	// 结果是数字 10, 去除了小数部分
parseInt("10") / 3; // 结果仍视为 number 浮点数, 因此结果为 3.3333333333333335

parseInt("abc");	// 转换失败，结果是特殊值 NaN (Not a Number)
```

要表示真正的整数，需要用 bigint，数字的结尾用 n 表示它是一个 bigint 类型

```js
10n / 3n;			// 结果 3n, 按整数除法处理
```



##### 6) boolean :star:

* Truthy
* Falsy

在 js 中，并不是 boolean 才能用于条件判断，你可以在 if 语句中使用【数字】、【字符串】... 作为判断条件

```js
let b = 1;

if(b) { // true
    console.log("进入了");
}
```



这时就有一个规则，当需要条件判断时，这个值被当作 true 还是 false，当作 true 的值归类为 truthy，当作 false 的值归类为 falsy

下面值都是 falsy

* `false`
* `Nullish (null, undefined)`
* `0, 0n, NaN`
* ``` "" '' `` ```  即长度为零的字符串

剩余的值绝大部分都是 truthy

有几个容易被当作 falsy 实际是 truthy 的

* `"false", "0"` 即字符串的 false 和 字符串的零
* `[]` 空数组
* `{}` 空对象



##### 7) symbol

* 很少使用



#### 3.1.3 对象类型

##### 1) Function :star::star:

###### 定义函数

```js
function 函数名(参数) {
    // 函数体
    return 结果;
}
```

例

```js
function add(a, b) {
    return a + b;
}
```

###### 调用函数

```js
函数名(实参);
```

例

```js
add(1, 2);     // 返回 3
```

js 中的函数调用特点：对参数的**类型**和**个数**都没有限制，例如

```js
add('a', 'b');  // 返回 ab
add(4, 5, 6);   // 返回 9, 第三个参数没有被用到, 不会报错
add(1);			// 返回 NaN, 这时 b 没有定义是 undefined, undefined 做数学运算结果就是 NaN
```



###### 默认参数

java 中（spring）要实现默认参数的效果得这么做：

```java
@RestController 
public class MyController {
    
    @RequestMapping("/page")
    @ResponseBody
    public void page(
        @RequestParam(defaultValue="1") int page, 
        @RequestParam(defaultValue="10") int size
    ){
        // ...
    }
}
```

js

```js
function pagination(page = 1, size = 10) {
    console.log(page, size);
}
```



###### 匿名函数

语法

```js
(function (参数) {
    // 函数体
    return 结果;
})
```

例

```js
(function(a,b){
    return a + b;
})
```

第一种场景：定义完毕后立刻调用

```js
(function(a,b){
    return a + b;
})(1,2)
```

第二种场景：作为其它对象的方法，例如

页面有元素

```html
<p id="p1">点我啊</p>
```

此元素有一个 onclick 方法，会在鼠标单击这个元素后被执行，onclick 方法刚开始是 null，需要赋值后才能使用

```js
document.getElementById("p1").onclick = (function(){
    console.log("鼠标单击了...");
});
```



###### 箭头函数

```js
(参数) => {
    // 函数体
    return 结果;
}
```

* 如果没有参数，() 还是要保留
* 如果只有一个参数，() 可以省略
* 如果函数体内只有一行代码，{} 可以省略
* 如果这一行代码就是结果，return 可以省略

例

```js
document.getElementById("p1").onclick = () =>  console.log("aa");
```



###### 函数是对象

以下形式在 js 中非常常见！

1. 可以参与赋值，例，具名函数也能参与赋值

```js
function abc() {
    console.log("bb");
}

document.getElementById("p1").onclick = abc;
```



2. 有属性、有方法，执行 `console.dir(abc)`，输出结果如下

```
ƒ abc()
    arguments: null
    caller: null
    length: 0
    name: "abc"
    ➡prototype: {constructor: ƒ}
    [[FunctionLocation]]: VM1962:1
    ➡[[Prototype]]: ƒ ()
    ➡[[Scopes]]: Scopes[1]
```

* 其中带有 f 标记的是方法，不带的是属性
* 带有 ➡ 符号的可以继续展开，限于篇幅省略了

* 带有 `[[ ]]` 的是内置属性，不能访问，只能查看
* 相对重要的是 `[[Prototype]]` 和 `[[Scopes]]` 会在后面继承和作用域时讲到



3. 可以作为方法参数

```js
function a() {
    console.log('a')
}

function b(fn) {          // fn 将来可以是一个函数对象
    console.log('b')
    fn();                 // 调用函数对象
}

b(a)
```



4. 可以作为方法返回值

```js
function c() {
    console.log("c");
    function d() {
        console.log("d");
    }
    return d;
}

c()()
```



###### 函数作用域

函数可以嵌套（js 代码中很常见，只是嵌套的形式更多是匿名函数，箭头函数）

```js
function a() {
    function b() {        
    }
}
```

看下面的例子

```js
function c() {
    var z = 30;
}

var x = 10;
function a() {
    var y = 20;
    function b() {
        // 看这里
        console.log(x, y);
    }
    b();
}
a();
```

* 以函数为分界线划定作用域，所有函数之外是全局作用域
* 查找变量时，由内向外查找
  * 在内层作用域找到变量，就会停止查找，不会再找外层
  * 所有作用域都找不到变量，报错
* 作用域本质上是函数对象的属性，可以通过 console.dir 来查看调试



###### 闭包

```js
var x = 10;
function a() {
    var y = 20;
    function b() {
        console.log(x,y);
    }
    return b;
}
a()();  // 在外面执行了 b
```

* 函数定义时，它的作用域已经确定好了，因此无论函数将来去了哪，都能从它的作用域中找到当时那些变量
* 别被概念忽悠了，闭包就是指**函数能够访问自己的作用域中变量**



###### let、var 与作用域

如果函数外层引用的是 let 变量，那么外层普通的 {} 也会作为作用域边界，最外层的 let 也占一个 script 作用域

```js
let x = 10; 
if(true) {
    let y = 20;
    function b() {
        console.log(x,y);
    }
    console.dir(b);
}
```

如果函数外层引用的是 var 变量，外层普通的 {} 不会视为边界

```js
var x = 10; 
if(true) {
    var y = 20;
    function b() {
        console.log(x,y);
    }
    console.dir(b);
}
```

如果 var 变量出现了重名，则他俩会被视为同一作用域中的同一个变量

```js
var e = 10; 
if(true) {
    var e = 20;
    console.log(e);	// 打印 20
}
console.log(e);		// 因为是同一个变量，还是打印 20
```

如果是 let，则视为两个作用域中的两个变量

```js
let e = 10; 
if(true) {
    let e = 20;	
    console.log(e);	// 打印 20
}
console.log(e);		// 打印 10
```

要想里面的 e 和外面的 e 能区分开来，最简单的办法是改成 let，或者用函数来界定作用域范围

```js
var e = 10; 
if(true) {
    function b() {
        var e = 20;
    	console.log(e);
    }
    b();
}
console.log(e);	
```



##### 2) Array :star:

语法

```js
// 创建数组
let arr = [1,2,3]; 

// 获取数组元素
console.log(arr[0]); // 输出 1

// 修改数组元素
array[0] = 5;		 // 数组元素变成了 [5,2,3]

// 遍历数组元素，其中 length 是数组属性，代表数组长度
for(let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
```

API

* push、shift、splice

```js
let arr = [1,2,3]; 

arr.push(4);    	// 向数组尾部(右侧)添加元素, 结果 [1,2,3,4]
arr.shift();		// 从数组头部(左侧)移除元素, 结果 [2,3,4]
arr.splice(1,1);	// 删除【参数1】索引位置的【参数2】个元素，结果 [2,4]
```

* join

```js
let arr = ['a','b','c'];

arr.join(); 		// 默认使用【,】作为连接符，结果 'a,b,c'
arr.join('');		// 结果 'abc'
arr.join('-');		// 结果 'a-b-c'
```

* map、filter、forEach

```js
let arr = [1,2,3,6];

function a(i) {   // 代表的新旧元素之间的变换规则
    return i * 10
}

// arr.map(a) // 具名函数，结果 [10,20,30,60]

// arr.map( (i) => {return i * 10} ); // 箭头函数
arr.map( i => i * 10 ); // 箭头函数
```

* 传给 map 的函数，参数代表旧元素，返回值代表新元素

map 的内部实现（伪代码）

```js
function map(a) { // 参数是一个函数
    let narr = [];
    for(let i = 0; i < arr.length; i++) {
        let o = arr[i]; // 旧元素
        let n = a(o);   // 新元素
        narr.push(n);
    }
    return narr;
} 
```

filter 例子

```js
let arr = [1,2,3,6];
arr.filter( (i)=> i % 2 == 1 ); // 结果 [1,3]
```

* 传给 filter 的函数，参数代表旧元素，返回 true 表示要留下的元素

forEach 例子

```js
let arr = [1,2,3,6];

/*for(let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}*/

arr.forEach( (i) => console.log(i) );
```

两个称呼

* 高阶函数，map，filter，forEach
* 回调函数，例如作为参数传入的函数



##### 3) Object :star::star:

###### 语法

```js
let obj = {
    属性名: 值,
    方法名: 函数,
    get 属性名() {},
    set 属性名(新值) {}
}
```

例1

```js
let stu1 = {
    name: "小明",
    age: 18,
    study: function(){
        console.log(this.name + "爱学习");
    }    
}
```

例2

```js
let name = "小黑";
let age = 20;
let study = function(){
    console.log(this.name + "爱学习");
}

let stu2 = { name, age, study }
```

例3（重点）

```js
let stu3 = {
    name: "小白",
    age: 18,
    study(){
        console.log(this.name + "爱学习");
    }    
}
```

* **注意**：对象方法这么写，仅限于对象内部

例4

```js
let stu4 = {
    _name: null, /*类似于java中私有成员变量*/
    get name() {
        console.log("进入了get");
        return this._name;
    },
    set name(name) {
        console.log("进入了set");
        this._name = name;
    }
}
```

调用 get，set

```js
stu4.name = "小白"

console.log(stu4.name)
```



###### 特色：属性增删

对比一下 Java 中的 Object

* Java 的 Object 是以类作为模板来创建，对象不能脱离类模板的范围，一个对象的属性、能用的方法都是确定好的
* js 的对象，不需要什么模板，它的属性和方法可以随时加减

```js
let stu = {name:'张三'};
stu.age = 18;					// 添加属性
delete stu.age;					// 删除属性

stu.study = function() {		// 添加方法
    console.log(this.name + "在学习");
}
```

添加 get，set，需要借助 Object.definePropery

```js
let stu = {_name:null};

Object.defineProperty(stu, "name", {
    get(){
        return this._name;
    },
    set(name){
        this._name = name;
    }
});
```

* 参数1：目标对象
* 参数2：属性名
* 参数3：get，set 的定义



###### 特色：this

先来对 Java 中的 this 有个理解

```java
public class TestMethod {

    static class Student {
        private String name;

        public Student(String name) {
            this.name = name;
        }

        public void study(Student this, String subject) {
            System.out.println(this.name + "在学习 " + subject);
        }
    }

    public static void main(String[] args) {
        Student stu = new Student("小明");
        
        // 下面的代码，本质上是执行 study(stu, "java")，因此 this 就是 stu
        stu.study("java"); 
    }
}
```

* Java 中的 this 是个隐式参数
* Java 中，我们说 this 代表的就是调用方法的那个对象



js 中的 this 也是隐式参数，但它与函数运行时上下文相关

例如，一个“落单”的函数

```js
function study(subject) {
    console.log(this.name + "在学习 " + subject)
}
```

测试一下

```js
study("js");  // 输出 在学习 js
```

这是因为此时函数执行，全局对象 window 被当作了 this，window 对象的 name 属性是空串



同样的函数，如果作为对象的方法

```js
let stu = {
    name:"小白",
    study
}
```

这种情况下，会将当前对象作为 this

```js
stu.study('js'); 	// 输出 小白在学习 js
```



还可以动态改变 this

```js
let stu = {name:"小黑"};
study.call(stu, "js");	// 输出 小黑在学习 js
```

这回 study 执行时，就把 call 的第一个参数 stu 作为 this



一个例外是，在**箭头函数**内出现的 this，以外层 this 理解 

用匿名函数

```js
let stu = {
    name: "小花",
    friends: ["小白","小黑","小明"],
    play() {
        this.friends.forEach(function(e){
            console.log(this.name + "与" + e + "在玩耍");
        });
    }
}
stu.play()
```

* this.name 所在的函数是【落单】的函数，因此 this 代表 window

输出结果为

```
与小白在玩耍
与小黑在玩耍
与小明在玩耍
```

用箭头函数

```js
let stu = {
    name: "小花",
    friends: ["小白","小黑","小明"],
    play() {
        this.friends.forEach(e => {
            console.log(this.name + "与" + e + "在玩耍");
        })
    }    
}
```

* this.name 所在的函数是箭头函数，因此 this 要看它外层的 play 函数，play 又是属于 stu 的方法，因此 this 代表 stu 对象

输出结果为

```
小花与小白在玩耍
小花与小黑在玩耍
小花与小明在玩耍
```

不用箭头函数的做法

```js
let stu = {
    name: "小花",
    friends: ["小白","小黑","小明"],
    play() {
        let me = this;
        this.friends.forEach(function(e){
            console.log(me.name + "与" + e + "在玩耍");
        });
    }
}
```



###### 特色：原型继承

```js
let father = {
    f1: '父属性',
    m1: function() {
        console.log("父方法");
    }
}

let son = Object.create(father);

console.log(son.f1);  // 打印 父属性
son.m1();			  // 打印 父方法
```

* father 是父对象，son 去调用 .m1 或 .f1 时，自身对象没有，就到父对象找
* son 自己可以添加自己的属性和方法
* son 里有特殊属性 `__proto__` 代表它的父对象，js 术语： son 的原型对象
* 不同浏览器对打印 son 的 `__proto__` 属性时显示不同
  * Edge 打印 console.dir(son) 显示 `[[Prototype]]`
  * Firefox 打印 console.dir(son) 显示 `<prototype>`



###### 特色：基于函数的原型继承

出于方便的原因，js 又提供了一种基于函数的原型继承

> **函数职责**
>
> 1. 负责创建子对象，给子对象提供属性、方法，功能上相当于构造方法
>
> 2. 函数有个特殊的属性 prototype，它就是函数创建的子对象的父对象
>
>    **注意！**名字有差异，这个属性的作用就是为新对象提供原型

```js
function cons(f2) {
    // 创建子对象(this), 给子对象提供属性和方法
    this.f2 = f2;
    this.m2 = function () {
        console.log("子方法");
    }
}
// cons.prototype 就是父对象
cons.prototype.f1 = "父属性";
cons.prototype.m1 = function() {
    console.log("父方法");
}
```

配合 new 关键字，创建子对象

```js
let son = new cons("子属性")
```

子对象的 `__proto__` 就是函数的 `prototype` 属性



JSON

之前我们讲 http 请求格式时，讲过 json 这种数据格式，它的语法看起来与 js 对象非常相似，例如：

一个 json 对象可以长这样：

```json
{
    "name":"张三",
    "age":18
}
```

一个 js 对象长这样：

```js
{
    name:"张三",
    age:18
}
```

那么他们的区别在哪儿呢？我总结了这么几点

1. 本质不同
   * json 对象本质上是个字符串，它的职责是作为客户端和服务器之间传递数据的一种格式，它的属性只是样子货
   * js 对象是切切实实的对象，可以有属性方法
2. 语法细节不同
   * json 中只能有 null、true|false、数字、字符串（只有双引号）、对象、数组
   * json 中不能有除以上的其它 js 对象的特性，如方法等
   * json 中的属性必须用双引号引起来



json 字符串与 js 对象的转换

```js
JSON.parse(json字符串);  // 返回js对象
JSON.stringify(js对象);  // 返回json字符串
```



#### 3.1.4 动态类型

静态类型语言，如 Java，值有类型，变量也有类型、赋值给变量时，类型要相符

```java
int a = 10;
String b = "abc";

int c = "abc";  // 错误
```

而 js 属于动态类型语言，值有类型，但变量没有类型，赋值给变量时，没要求

例如

```js
let a = 200;

let b = 100;
b = 'abc';
b = true;
```

动态类型看起来比较灵活，但变量没有类型，会给后期维护带来困难，例如

```js
function test(obj) {
    // obj 的类型未知，必须根据不同类型做出相应的容错处理
}
```



## 3.2 运算符与表达式

* `+ - * / % ** `
* `+= -= *= /= %= **=`
* `++ --`
* 位运算、移位运算
* `== != > >= < <=`
* `=== !==` :star:
* `&& || !` :star:
* `?? ?.` :star:
* `...` :star:
* 解构赋值 :star:



#### 1) ===

严格相等运算符，用作逻辑判等

```js
1 == 1    	// 返回 true 
1 == '1'	// 返回 true，会先将右侧的字符串转为数字，再做比较
1 === '1'	// 返回 false，类型不等，直接返回 false
```

typeof 查看某个值的类型

```js
typeof 1	// 返回 'number'
typeof '1'	// 返回 'string'
```



#### 2) ||

它的语法是

```js
值1 || 值2
```

如果值1 是 Truthy，返回值1，如果值1 是 Falsy 返回值 2



#### 3) ?? 与 ?.

??语法

```
值1 ?? 值2
```

* 值1 是 nullish，返回值2
* 值1 不是 nullish，返回值1



?.：希望当某个属性是 nullish 时，短路并返回 undefined，可以用 ?.

需求，函数参数是一个对象，可能包含有子属性

例如，参数可能是

```js
let stu1 = {
    name:"张三",
    address: {
        city: '北京'
    }
};

let stu2 = {
    name:"李四"
}

let stu3 = {
    name:"李四",
    address: null
}
```

现在要访问子属性（有问题）

```js
function test(stu) {
    console.log(stu.address.city)
}
```

现在希望当某个属性是 nullish 时，短路并返回 undefined，可以用 ?.

```js
function test(stu) {
    console.log(stu.address?.city)
}
```

用传统办法 

```js
function test(stu) {
    if(stu.address === undefined || stu.address === null) {
        console.log(undefined);
        return;
    }
    console.log(stu.address.city)
}
```



#### 4) ...

展开运算符

作用1：打散数组，把元素传递给多个参数

```js
let arr = [1,2,3];

function test(a,b,c) {
    console.log(a,b,c);
}
```

需求，把数组元素依次传递给函数参数

传统写法

```js
test(arr[0],arr[1],arr[2]);		// 输出 1,2,3
```

展开运算符写法

```js
test(...arr);					// 输出 1,2,3
```

* 打散可以理解为【去掉了】数组外侧的中括号，只剩下数组元素



作用2：复制数组或对象

数组

```js
let arr1 = [1,2,3];
let arr2 = [...arr1];		// 复制数组
```

对象

```js
let obj1 = {name:'张三', age: 18};

let obj2 = {...obj1};		// 复制对象
```

**注意**：展开运算符复制属于浅拷贝，例如

```js
let o1 = {name:'张三', address: {city: '北京'} }

let o2 = {...o1};
```



作用3：合并数组或对象

合并数组

```js
let a1 = [1,2];
let a2 = [3,4];

let b1 = [...a1,...a2];		// 结果 [1,2,3,4]
let b2 = [...a2,5,...a1]	// 结果 [3,4,5,1,2]
```

合并对象

```js
let o1 = {name:'张三'};
let o2 = {age:18};
let o3 = {name:'李四'};

let n1 = {...o1, ...o2};	// 结果 {name:'张三',age:18}

let n2 = {...o3, ...o2, ...o1}; // 结果{name:'李四',age:18}
```

* 复制对象时出现同名属性，后面的会覆盖前面的



#### 5) [] {}

解构赋值

[]：用在声明变量时

```js
let arr = [1,2,3];

let [a, b, c] = arr;	// 结果 a=1, b=2, c=3
```

用在声明参数时

```js
let arr = [1,2,3];

function test([a,b,c]) {
    console.log(a,b,c) 	// 结果 a=1, b=2, c=3
}

test(arr);				
```



{}：用在声明变量时

```js
let obj = {name:"张三", age:18};

let {name,age} = obj;	// 结果 name=张三, age=18
```

用在声明参数时

```js
let obj = {name:"张三", age:18};

function test({name, age}) {
    console.log(name, age); // 结果 name=张三, age=18
}

test(obj)
```



## 3.3  控制语句

* `if ... else`
* `switch`
* `while`
* `do ... while`
* `for` 
* `for ... in` :star:
* `for ... of` :star:
* `try ... catch` :star:



#### 1) for in

主要用来遍历对象

```js
let father = {name:'张三', age:18, study:function(){}};

for(const n in father) {
    console.log(n);
}
```

* 其中 const n 代表遍历出来的属性名
* 注意1：方法名也能被遍历出来（它其实也算一种特殊属性）
* 注意2：遍历子对象时，父对象的属性会跟着遍历出来

```js
let son = Object.create(father);
son.sex = "男";

for(const n in son) {
    console.log(n);
}
```

* 注意3：在 for in 内获取属性值，要使用 [] 语法，而不能用 . 语法

```js
for(const n in son) {
    console.log(n, son[n]);
}
```



#### 2) for of

主要用来遍历数组，也可以是其它可迭代对象，如 Map，Set 等

```js
let a1 = [1,2,3];

for(const i of a1) {
    console.log(i);
}

let a2 = [
    {name:'张三', age:18},
    {name:'李四', age:20},
    {name:'王五', age:22}
];

for(const obj of a2) {
    console.log(obj.name, obj.age);
}

for(const {name,age} of a2) {
    console.log(name, age);
}
```



#### 3) try catch

```js
let stu1 = {name:'张三', age:18, address: {city:'北京'}};
let stu2 = {name:'张三', age:18};

function test(stu) {
    try {
        console.log(stu.address.city)   
    } catch(e) {
        console.log('出现了异常', e.message)
    } finally {
        console.log('finally');
    }
}
```



### 3.4 API

#### 3.4.1 环境准备

安装：nvm install  node.js 版本号

进入环境：nvm use node.js 版本号

![](C:/ubuntu/net_file/front/imgs/nvm指令.png)

##### 1) 安装 nvm

nvm 即 (node version manager)，好处是方便切换 node.js 版本

安装注意事项

1. 要卸载掉现有的 nodejs
2. 提示选择 nvm 和 nodejs 目录时，一定要避免目录中出现空格
3. 选用【以管理员身份运行】cmd 程序来执行 nvm 命令
4. 首次运行前设置好国内镜像地址

```
nvm node_mirror http://npm.taobao.org/mirrors/node/
nvm npm_mirror https://npm.taobao.org/mirrors/npm/
```

首先查看有哪些可用版本

```
nvm list available
```

输出

```
|   CURRENT    |     LTS      |  OLD STABLE  | OLD UNSTABLE |
|--------------|--------------|--------------|--------------|
|    18.7.0    |   16.16.0    |   0.12.18    |   0.11.16    |
|    18.6.0    |   16.15.1    |   0.12.17    |   0.11.15    |
|    18.5.0    |   16.15.0    |   0.12.16    |   0.11.14    |
|    18.4.0    |   16.14.2    |   0.12.15    |   0.11.13    |
|    18.3.0    |   16.14.1    |   0.12.14    |   0.11.12    |
|    18.2.0    |   16.14.0    |   0.12.13    |   0.11.11    |
|    18.1.0    |   16.13.2    |   0.12.12    |   0.11.10    |
|    18.0.0    |   16.13.1    |   0.12.11    |    0.11.9    |
|    17.9.1    |   16.13.0    |   0.12.10    |    0.11.8    |
|    17.9.0    |   14.20.0    |    0.12.9    |    0.11.7    |
|    17.8.0    |   14.19.3    |    0.12.8    |    0.11.6    |
|    17.7.2    |   14.19.2    |    0.12.7    |    0.11.5    |
|    17.7.1    |   14.19.1    |    0.12.6    |    0.11.4    |
|    17.7.0    |   14.19.0    |    0.12.5    |    0.11.3    |
|    17.6.0    |   14.18.3    |    0.12.4    |    0.11.2    |
|    17.5.0    |   14.18.2    |    0.12.3    |    0.11.1    |
|    17.4.0    |   14.18.1    |    0.12.2    |    0.11.0    |
|    17.3.1    |   14.18.0    |    0.12.1    |    0.9.12    |
|    17.3.0    |   14.17.6    |    0.12.0    |    0.9.11    |
|    17.2.0    |   14.17.5    |   0.10.48    |    0.9.10    |
```

建议安装 LTS（长期支持版）

```
nvm install 16.16.0
nvm install 14.20.0
```

执行 `nvm list` 会列出已安装版本

切换到 16.16.0

```
nvm use 16.16.0
```

切换到 14.20.0

```
nvm use 14.20.0
```

安装后 nvm 自己的环境变量会自动添加，但可能需要手工添加 nodejs 的 PATH 环境变量



##### 2) 检查 npm

npm 是 js 的包管理器，就类似于 java 界的 maven，要确保它使用的是国内镜像

检查镜像

```
npm get registry
```

如果返回的不是 `https://registry.npm.taobao.org/`，需要做如下设置

```
npm config set registry https://registry.npm.taobao.org/
```



##### 3) 搭建前端服务器

新建一个保存项目的 client 文件夹，进入文件夹执行

```
npm install express --save-dev
```

修改 package.json 文件

```json
{
  "type": "module",
  "devDependencies": {
    "express": "^4.18.1"
  }
}
```

* 其中 devDependencies 是 npm install --save-dev 添加的

编写 main.js 代码

```js
import express from 'express'
const app = express()

app.use(express.static('./'))
app.listen(7070)
```

执行 js 代码（运行前端服务器）

```
node main.js
```

使用CTRL+C 退出前端服务器



#### 3.4.2 前端案例

初步效果

![image-20220812103323220](C:/ubuntu/net_file/front/imgs/image-20220812103323220.png)

架构

![image-20220812103219916](C:/ubuntu/net_file/front/imgs/image-20220812103219916.png)

* 前端只有静态页面，使用 Express 服务器
* 后端使用 Tomcat 服务器，通过 SpringBoot、MyBatis 等框架获取数据库数据



##### 1) 查找元素

* document.getElementById - 根据 id 值查找一个元素
* [document|元素].querySelector - 根据选择器查找第一个匹配元素
* [document|元素].querySelectorAll - 根据选择器查找所有匹配元素

例如，有下面的 html 代码

```html
<div>
    <div class="title">学生列表</div>
    <div class="thead">
        <div class="row bold">
            <div class="col">编号</div>
            <div class="col">姓名</div>
            <div class="col">性别</div>
            <div class="col">年龄</div>
        </div>
    </div>
    <div class="tbody">
        <div class="row">
            <div class="col">1</div>
            <div class="col">张三</div>
            <div class="col">男</div>
            <div class="col">18</div>
        </div>
    </div>
</div>
```

执行

```js
document.querySelector('.title'); // 找到 <div class="title">学生列表</div>
```

执行

```js
document.querySelector('.col'); // 找到 <div class="col">编号</div>
```

执行

```js
document.querySelectorAll('.col');

/*
  找到的是一个集合
  <div class="col">编号</div>
  <div class="col">姓名</div>
  <div class="col">性别</div>
  <div class="col">年龄</div>
  <div class="col">1</div>
  <div class="col">张三</div>
  <div class="col">男</div>
  <div class="col">18</div>
*/
```

执行

```js
const thead = document.querySelector('.thead');

// 只在 thead 元素范围内找
thead.querySelectorAll('.col');

/*
  找到的是一个集合
  <div class="col">编号</div>
  <div class="col">姓名</div>
  <div class="col">性别</div>
  <div class="col">年龄</div>
*/
```

根据 id 属性查找既可以用

```js
document.getElementById("id值")
```

也可以用 

```js
document.querySelector("#id值")
```



##### 2) 修改元素内容

* 元素.innerHTML
* 元素.textContent

例如

```js
document.querySelector('.title').innerHTML = '侠客列表'
```

效果

![image-20220812161003958](C:/ubuntu/net_file/front/imgs/image-20220812161003958.png)

innerHTML  会解析内容中的标签，例如

![image-20220812161137912](C:/ubuntu/net_file/front/imgs/image-20220812161137912.png)

textContext 不会解析内容中的标签

![image-20220812161341825](C:/ubuntu/net_file/front/imgs/image-20220812161341825.png)

给 innerHTML 或 textContent 赋值空串，可以实现清空标签内容的效果



##### 3) 利用模板

```html
<div>
    <div class="title">学生列表</div>
    <div class="thead">
        <div class="row bold">
            <div class="col">编号</div>
            <div class="col">姓名</div>
            <div class="col">性别</div>
            <div class="col">年龄</div>
        </div>
    </div>
    <div class="tbody">
    </div>
</div>

<template id="tp">
    <div class="row">
        <div class="col">xx</div>
        <div class="col">xx</div>
        <div class="col">xx</div>
        <div class="col">xx</div>
    </div>
</template>

<script>
    // 将来这些数据从 java 端返回
    let array = [
        { id: 1, name: '张三', sex: '男', age: 18 },
        { id: 2, name: '李四', sex: '女', age: 17 }
    ];

    const tp = document.getElementById("tp");
    const row = tp.content;
    const [c1,c2,c3,c4] = row.querySelectorAll(".col");
    const tbody = document.querySelector('.tbody');
    for(const {id,name,sex,age} of array) {
        c1.textContent = id;
        c2.textContent = name;
        c3.textContent = sex;
        c4.textContent = age;
        // 复制元素
        const newRow = document.importNode(row, true);
        // 建立父子关系，左边父，右边子
        tbody.appendChild(newRow);
    }
</script>
```



##### 4) Fetch API

Fetch API 可以用来获取远程数据，它有两种方式接收结果，同步方式与异步方式

格式

```js
fetch(url, options) // 返回 Promise
```

同步方式

```js
const 结果 = await Promise
// 后续代码
```

* await 关键字必须在一个标记了 **async 的 function 内**来使用
* 后续代码**不会在结果返回前执行**

异步方式

```js
Promise
	.then(结果 => { ... })//箭头函数
// 后续代码                 
```

* 后续代码不必等待结果返回就可以执行



例：

在 express 服务器上有 students.json 文件

```json
[
    { "id": 1, "name": "张三", "sex": "男", "age": 18 },
    { "id": 2, "name": "李四", "sex": "女", "age": 17 }
]
```

现在用 fetch api 获取这些数据，并展示

同步方式

```html
<script>
    async function findStudents() {
        try {
            // 获取响应对象
            const resp = await fetch('students.json')

            // 获取响应体, 按json格式转换为js数组
            const array = await resp.json();

            // 显示数据
            const tp = document.getElementById("tp");
            const row = tp.content;
            const [c1,c2,c3,c4] = row.querySelectorAll(".col");
            const tbody = document.querySelector('.tbody');
            for(const {id,name,sex,age} of array) {
                c1.textContent = id;
                c2.textContent = name;
                c3.textContent = sex;
                c4.textContent = age;
                // 复制元素
                const newRow = document.importNode(row, true);
                // 建立父子关系
                tbody.appendChild(newRow);
            }
        } catch (e) {
            console.log(e);
        }

    }
    findStudents()
</script>
```

* fetch('students.json') 内部会发送请求，但响应结果不能立刻返回，因此 await 就是等待响应结果返回
* 其中 resp.json() 也不是立刻能返回结果，它返回的也是 Promise 对象，也要配合 await 取结果

异步方式

```html
<script>
    fetch('students.json')
        .then( resp => resp.json() )
        .then( array => {
        	// 显示数据
            const tp = document.getElementById("tp");
            const row = tp.content;
            const [c1,c2,c3,c4] = row.querySelectorAll(".col");
            const tbody = document.querySelector('.tbody');
            for(const {id,name,sex,age} of array) {
                c1.textContent = id;
                c2.textContent = name;
                c3.textContent = sex;
                c4.textContent = age;
                // 复制元素
                const newRow = document.importNode(row, true);
                // 建立父子关系
                tbody.appendChild(newRow);
            }
        })
        .catch( e => console.log(e) )


</script>
```

* 第一个 then 是在响应返回后，才会调用它里面的箭头函数，箭头函数参数即 resp  响应对象
* 第二个 then 是在 json 解析完成后，才会调用它里面的箭头函数，箭头函数参数即解析结果（本例是 array 数组）
* 上一个 then 返回的是 Promise 对象时，才能链式调用下一个 then



###### 跨域问题

![image-20220814105448882](C:/ubuntu/net_file/front/imgs/image-20220814105448882.png)

* 只要协议、主机、端口之一不同，就不同源，例如
  * http://localhost:7070/a 和 https://localhost:7070/b 就不同源
* 同源检查是浏览器的行为，而且只针对 fetch、xhr 请求
  * 如果是其它客户端，例如 java http client，postman，它们是不做同源检查的
  * 通过表单提交、浏览器直接输入 url 地址这些方式发送的请求，也不会做同源检查
* 更多相关知识请参考
  * [跨源资源共享（CORS） - HTTP | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/CORS)



请求响应头解决

![image-20220814144040703](C:/ubuntu/net_file/front/imgs/image-20220814144040703.png)

* fetch 请求跨域，会携带一个 Origin 头，代表【发请求的资源源自何处】，目标通过它就能辨别是否发生跨域
  * 我们的例子中：student.html 发送 fetch 请求，告诉 tomcat，我源自 localhost:7070
* 目标资源通过返回 Access-Control-Allow-Origin 头，告诉浏览器【允许哪些源使用此响应】
  * 我们的例子中：tomcat 返回 fetch 响应，告诉浏览器，这个响应允许源自 localhost:7070 的资源使用



代理解决

![image-20220814161532141](C:/ubuntu/net_file/front/imgs/image-20220814161532141.png)

```cmd
npm install http-proxy-middleware --save-dev
```

在 express 服务器启动代码中加入

```js
import {createProxyMiddleware} from 'http-proxy-middleware'

// ...

app.use('/api', createProxyMiddleware({ target: 'http://localhost:8080', changeOrigin: true }));
```

fetch 代码改为

```js
const resp = await fetch('http://localhost:7070/api/students')
```

或

```js
const resp = await fetch('/api/students')
```



##### 5) 模块化

单个导出 const、let、function

```js
export const a = 10;
export let b = 20;
export function c() {
    console.log('c');
}
```

一齐导出

```js
const a = 10;
let b = 20;
function c() {
    console.log('c')
}

export {a,b,c}
```

导出 default，只能有一个

```js
export const a = 10;
export let b = 20;
export function c() {
    console.log('c')
}

export default b;
```



import 语法

```html
<script type="module">
	import 语句
</script>
```

* import 需要遵循同源策略

整个导入

```js
import * as module from '/1.js'
console.log(module.a)		// 输出10
console.log(module.b)		// 输出20
module.c()					// 输出c
```

单个导入

```js
import {a,c} from '/1.js'
console.log(a)				// 输出10
c()							// 输出c
```

导入默认

```js
import x from '/1.js'
console.log(x)				// 输出20
```



## 四 Vue2

不学

## 五 Vue 3

### 1. TypeScript

#### 1) 动态类型的问题

前面我们讲过 js 属于动态类型语言，例如

```js
function test(obj) {    
}
```

obj 可能只是个字符串

```js
test('hello, world')
```

obj 也有可能是个函数

```js
test(()=>console.log('hello, world'))
```

obj 类型不确定，就给后期使用者带来了麻烦，一旦参数传不对，代码就崩溃了



动态类型意味着

* 运行代码时才知道发生什么 (running the code to see what happens)

静态类型意味着

* 在代码运行前，就对它的行为做出预测 (make predications about what code is expected before it runs)



下面的 typescript 代码，就在代码运行前对参数加入了约束限制

```typescript
function test(msg : string) {
}
```

* 限制了参数只能做 string 那些事

```typescript
function test(msg : Function) {
  msg()
}
```

* 限制了参数只能做函数那些事



#### 2) 入门

安装 typescript 编译器

```cmd
npm install -g typescript
```

编写 ts 代码

```typescript
function hello(msg: string) {
  console.log(msg)
}

hello('hello,world')
```

执行 tsc 编译命令

```cmd
tsc xxx.ts
```

编译生成 js 代码，编译后进行了类型擦除

```js
function hello(msg) {
    console.log(msg);
}
hello('hello,world');
```



再来一个例子，用 interface 定义用户类型

```ts
interface User {
  name: string,
  age: number
}

function test(u: User): void {
  console.log(u.name)
  console.log(u.age)
}

test({ name: 'zhangs', age: 18 })
```

编译后

```js
function test(u) {
    console.log(u.name);
    console.log(u.age);
}
test({ name: 'zhangs', age: 18 });
```



可见，typescript 属于编译时实施类型检查（静态类型）的技术



#### 3) 类型

| 类型        | 例                                    | 备注                         |
| ----------- | ------------------------------------- | ---------------------------- |
| 字符串类型  | string                                |                              |
| 数字类型    | number                                |                              |
| 布尔类型    | boolean                               |                              |
| 数组类型    | number[],string[], boolean[] 依此类推 |                              |
| 任意类型    | any                                   | 相当于又回到了没有类型的时代 |
| 复杂类型    | type 与 interface                     |                              |
| 函数类型    | () => void                            | 对函数的参数和返回值进行说明 |
| 字面量类型  | "a"\|"b"\|"c"                         | 限制变量或参数的取值         |
| nullish类型 | null 与 undefined                     |                              |
| 泛型        | `<T>`，`<T extends 父类型>`           |                              |



##### 标注位置

###### 标注变量

```typescript
let message: string = 'hello,world'
```

* 一般可以省略，因为可以根据后面的字面量推断出前面变量类型

```typescript
let message = 'hello,world'
```



###### 标注参数

```typescript
function greet(name: string) {
    
}
```

很多时候，都能够推断出参数类型

```typescript
const names = ['Alice', 'Bob', 'Eve']
const lowercaseNames = names.map((e: string) => e.toLowerCase())
```

* 可以用类型推断，推断出 e 是 string 类型



###### 标注返回值

```typescript
function add(a: number, b: number) : number {
    return a + b
}
```

* 一般也可以省略，因为可以根据返回值做类型推断



##### 复杂类型

###### type

```typescript
type Cat = {
  name: string,
  age: number
}

const c1: Cat = { name: '小白', age: 1 }
const c2: Cat = { name: '小花' }					  // 错误: 缺少 age 属性
const c3: Cat = { name: '小黑', age: 1, sex: '公' } // 错误: 多出 sex 属性
```



###### interface

```typescript
interface Cat {
  name: string,
  age: number
}

const c1: Cat = { name: '小白', age: 1 }
const c2: Cat = { name: '小花' }					  // 错误: 缺少 age 属性
const c3: Cat = { name: '小黑', age: 1, sex: '公' } // 错误: 多出 sex 属性
```



###### 可选属性

如果需要某个属性可选，可以用下面的语法

```typescript
interface Cat {
  name: string,
  age?: number
}

const c1: Cat = { name: '小白', age: 1 }
const c2: Cat = { name: '小花' }					  // 正确: age 属性可选
```

* 可选属性要注意处理 undefined 值



###### 鸭子类型

```typescript
interface Cat {
  name: string
}

function test(cat: Cat) {
  console.log(cat.name)
}

const c1 = { name: '小白', age: 1 } 
test(c1)
```

* const c1 并没有声明类型为 Cat，但它与 Cat 类型有一样的属性，也可以被当作是 Cat 类型



##### 方法类型

```typescript
interface Api {
  foo(): void,
  bar(str: string): string
}

function test(api: Api) {
  api.foo()
  console.log(api.bar('hello'))
}

test({
  foo() { console.log('ok') },
  bar(str: string) { return str.toUpperCase() }
})
```



##### 字面量类型

```typescript
function printText(s: string, alignment: "left" | "right" | "center") {
  console.log(s, alignment)
}

printText('hello', 'left')
printText('hello', 'aaa') // 错误: 取值只能是 left | right | center
```



##### nullish 类型

```typescript
function test(x?: string | null) {
  console.log(x?.toUpperCase())
}

test('aaa')
test(null)
test()
```

* x?: string | null 表示可能是 undefined 或者是 string 或者是 null



##### 泛型

下面的几个类型声明显然有一定的相似性

```typescript
interface RefString {
  value: string
}

interface RefNumber {
  value: number
}

interface RefBoolean {
  value: boolean
}

const r1: RefString = { value: 'hello' }
const r2: RefNumber = { value: 123 }
const r3: RefBoolean = { value: true }
```

可以改进为

```typescript
interface Ref<T> {
  value: T
}

const r1: Ref<string> = { value: 'hello' }
const r2: Ref<number> = { value: 123 }
const r3: Ref<boolean> = { value: true }
```

* 泛型的要点就是 `<类型参数>`，把【类型】也当作一个变化的要素，像参数一样传递过来，这样就可以派生出结构相似的新类型



函数定义也支持泛型

```typescript
function ref<T>(n: T): Ref<T> {
  return { value: n }
}

const v1 = ref("hello"); 	// Ref<string>
const v2 = ref(123.3333);	// Ref<number>

v1.value.toLocaleLowerCase()
v2.value.toFixed(2)
```



#### 4) 意义

##### 更好理解框架

现在越来越多的前端框架采用 typescript，如果懂 typescript 语法，可以更好地阅读框架代码

以 Map 为例

```typescript
const map = new Map<string, string>()
map
  .set("a", "b")
  .set("c", "d")

map.forEach((value,key,m)=>{
  console.log(value, key)
})
```

* 注意编译需要 `tsc --target es6 .\xxx.ts`



##### 更好的提示

例如，从服务器返回的一段 json，如果不用 typescript，则编辑器也不能给出准确的提示

```typescript
interface User {
  name: string,
  age: number
}

const user: User = JSON.parse(`{ "name":"张三", "age":18 }`)
```



#### 5) 类

> 关于 TypeScript 与 JavaScript 中的类语法不是重点，class 相关语法只是起到辅助作用，更重要的是前面讲的 interface

##### 基本语法

```typescript
class User {
    name: string;
    
    constructor(name: string) {
        this.name = name
    }
}

const u = new User('张三')
```

其实会被编译成这个样子（默认 --target=es3）

```js
var User = /** @class */ (function () {
    function User(name) {
        this.name = name;
    }
    return User;
}());
var u = new User('张三');
```

所以 js 中的 class，并不等价于 java 中的 class，它还是基于原型实现的，原理参考第二章（036、037）



##### 只读属性

```typescript
class User {
  readonly name: string;
  
  constructor(name: string) {
      this.name = name
  }
}

const u = new User('张三')
u.name = '李四'				// 编译错误
```

* readonly 是 typescript 特有的，表示该属性只读



##### 方法

```typescript
class User {
  readonly name: string;
  
  constructor(name: string) {
      this.name = name
  }

  study() {
    console.log(`[${this.name}]正在学习`)
  }
}

const u = new User('张三')
u.study()
```



##### get，set

```typescript
class User {
  _name: string;

  constructor(name: string) {
    this._name = name
  }

  get name() {
    return this._name
  }

  set name(name: string) {
    this._name = name
  }
}

const u = new User('张三')
console.log(u.name)
u.name = '李四'
console.log(u.name)
```

* 注意，需要在编译时加上 `tsc --target es6 .\xxx.ts` 选项
* es6 等价于 es2015，再此之上还有 es2016 ... es2022



##### 类与接口

```typescript
interface User {
  name: string
  study(course: string): void
}

class UserImpl implements User {
  name: string;
  constructor(name: string) {
    this.name = name
  }
  study(course: string) {
    console.log(`[${this.name}]正在学习[${course}]`)
  }
  foo() { }
}

const user: User = new UserImpl('张三')
user.study('Typescript')
user.foo() // 错误，必须是接口中定义的方法
```



##### 继承与接口

```typescript
interface Flyable {
  fly(): void
}

class Animal {
  name: string;
  constructor(name: string) {
    this.name = name
  }
}

class Bird extends Animal implements Flyable {
  fly() {
    console.log(`${this.name}在飞翔`)
  }
}

const b: Flyable & Animal = new Bird("小花")
b.fly()
```

* Flyable & Animal 表示变量是 flyable 类型，同时也是 Animal 类型



##### 方法重写

```typescript
class Father {
  study(): void {
    console.log(`father study`)
  }
}

class Son extends Father {  
  study(): void {
    super.study()
    console.log(`son study`)
  }
}

const f: Father = new Son()
f.study()
```



### 2. Vue3 基础

技术选型

* Vue 
  * **选项式 API** 还是 **组合式 API**✔️
  * **HTML** 还是 **单文件组件**✔️
* 语法
  * **javascript** 还是 **typescript**✔️
* 构建工具
  * **@vue/cli** 还是 **vite**✔️
* 路由
  * **vue-router**✔️
* 共享存储
  * **vuex** 还是 **pinia**✔️
* 视图组件
  * **ElementUI** 还是 **Antdv**✔️



#### 1) 环境准备

##### 创建项目

采用 vite 作为前端项目的打包，构建工具

```cmd
npm init vite@latest
```

按提示操作

```cmd
cd 项目目录
npm install
npm run dev
```



##### 编码 IDE

推荐采用微软的 VSCode 作为开发工具，到它的官网 [Visual Studio Code - Code Editing. Redefined](https://code.visualstudio.com/) 下载安装即可

![image-20220911090418621](D:\2022.js\imgs\image-20220911090418621.png)

要对 *.vue 做语法支持，还要安装一个 Volar 插件

![image-20220911090756694](D:\2022.js\imgs\image-20220911090756694.png)



##### 安装 devtools

* devtools 插件网址：https://devtools.vuejs.org/guide/installation.html

![image-20220815141648040](D:\2022.js\imgs\image-20220815141648040.png)



##### 修改端口

打开项目根目录下 vite.config.ts

```typescript
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue()],
  server: {
    port: 7070
  }
})
```

* 文档地址：[配置 Vite {#configuring-vite} | Vite中文网 (vitejs.cn)](https://vitejs.cn/config/#server-port)



##### 配置代理

为了避免前后端服务器联调时， fetch、xhr 请求产生跨域问题，需要配置代理，同样是修改项目根目录下 vite.config.ts

```typescript
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue()],
  server: {
    port: 7070,
    proxy: {
      '/api': {
        target: 'http://localhost:8080',
        changeOrigin: true
      }
    }
  }
})
```

* 文档地址：[配置 Vite {#configuring-vite} | Vite中文网 (vitejs.cn)](https://vitejs.cn/config/#server-proxy)



##### 项目结构

```
index.html
package.json
tsconfig.json
vite.config.ts
├─public
└─src
    ├─assets
    ├─components
    ├─model
    ├─router
    ├─store
    └─views
```

* index.html 为主页面
* package.json npm 配置文件
* tsconfig.json typescript 配置文件
* vite.config.ts vite 配置文件
* public 静态资源
* src/components 可重用组件
* src/model 模型定义
* src/router 路由
* src/store 共享存储
* src/views 视图组件



#### 2) Vue 组件

Vue 的组件文件以 .vue 结尾，每个组件由三部分组成

```vue
<script setup lang="ts"></script>

<template></template>

<style scoped></style>
```

* script 代码部分，控制模板的数据来源和行为
* template 模板部分，由它生成 html 代码
* style 样式部分，一般不咋关心



根组件是 src/App.vue，先来个 Hello,world 例子

```vue
<script setup lang="ts">
import { ref } from "vue";
let msg = ref("hello"); // 把数据变成响应式的

function change() {
  msg.value = "world";
  console.log(msg);
}
</script>
<template>
  <h1>{{ msg }}</h1>
  <input type="button" value="修改msg" @click="change" />
</template>
```

* {{msg}} 用来把一个变量绑定到页面上某个位置
* 绑定的变量必须用 ref 函数来封装
  * ref 返回的是【响应式】数据，即数据一旦变化，页面展示也跟着变化



#### main.ts

```typescript
import { createApp } from 'vue'
import './style.css'
import App from './App.vue'

createApp(App)
  .mount('#app')
```

* createApp 是创建一个 Vue 应用程序，它接收的参数 App 即之前我们看到的根组件
* mount 就是把根组件生成的 html 代码片段【挂载】到 index.html 中 id 为 app 的 html 元素上



可以修改自己的组件文件，挂载到主页面

新建 src/views/E0.vue，内容如下

```vue
<script setup lang="ts">
import { ref } from 'vue'
const msg = ref('Hello, World!!')
</script>
<template>
  <h1>{{ msg }}</h1>
</template>
```

修改 main.ts 将自己的组件文件挂载

```typescript
import { createApp } from 'vue'
import './style.css'
// import App from './App.vue'
import E0 from './views/E0.vue'

createApp(E0).mount('#app')
```

* 以后我们用这样的方式演示课堂案例



打开浏览器控制台，进入 Vue 的开发工具，尝试做如下修改

![image-20220906141650435](D:\2022.js\imgs\image-20220906141650435.png)

当把 msg 的值由 "Hello, World" 改为 "你好" 时，会发现页面展示同步发生了变化



#### ref 与 reactive

vue 提供了两个函数，都可以将数据变为【响应式】的

```vue
<script setup lang="ts">
import { ref, reactive } from 'vue'
const msg = ref('Hello, World')
const user = reactive({ name: '张三' })
</script>

<template>
  <h2>{{msg}}</h2>
  <h2>{{user.name}}</h2>
</template>
```

* ref 能将任意类型的数据变为【响应式】的
* reactive 只能将对象类型变为【响应式】，对基本类型无效（例如 string，number，boolean）



还有一点不同

```vue
<script setup lang="ts">
import { ref, reactive } from 'vue'
const u1 = ref({ name: '张三' })
const u2 = reactive({ name: '张三' })

function test() {
  console.log(u1.value)
  console.log(u2)
}

test()
</script>
  
<template>
  <h2>{{u1.name}}</h2>
  <h2>{{u2.name}}</h2>
</template>
```

* 在 template 模板中使用 ref 包装的数据，直接写【变量名】就可以了
* 但在代码中要使用 ref 包装的数据，必须用【变量名.value】才能访问到
* reactive 包装的数据，在模板中和代码中都是一致的



#### 属性绑定

```vue
<script setup lang="ts">
import { ref } from 'vue'
const path = ref('/src/assets/vue.svg')

</script>

<template>
  <img :src="path" alt="">
</template>
```

* 【:属性名】用来将标签属性与【响应式】变量绑定



#### 事件绑定

```vue
<script setup lang="ts">
import { ref } from 'vue'
const count = ref(0)
function dec() {
  count.value--
}
function inc() {
  count.value++
}
</script>

<template>
  <input type="button" value="-" @click="dec">
  <h2>{{count}}</h2>
  <input type="button" value="+" @click="inc">
</template>
```

* 【@事件名】用来将标签属性与函数绑定，事件发生后执行函数内代码



#### 表单绑定

```vue
<script setup lang="ts">
import { ref } from "vue";
const user = ref({
  name:'张三',
  age:18,
  sex:'男',
  fav:['游泳','打球']
})

function saveUser() {
  console.log(user.value)
}
</script>

<template>
  <div class="outer">
    <div>
      <label for="">请输入姓名</label>
      <input type="text" v-model="user.name"/>
    </div>
    <div>
      <label for="">请输入年龄</label>
      <input type="text" v-model="user.age"/>
    </div>
    <div>
      <label for="">请选择性别</label>
      男 <input type="radio" value="男" v-model="user.sex"/> 
      女 <input type="radio" value="女" v-model="user.sex"/>
    </div>
    <div>
      <label for="">请选择爱好</label>
      游泳 <input type="checkbox" value="游泳" v-model="user.fav"/> 
      打球 <input type="checkbox" value="打球" v-model="user.fav"/> 
      健身 <input type="checkbox" value="健身" v-model="user.fav"/>
    </div>
    <div>
      <input type="button" value="保存" @click="saveUser">
    </div>
  </div>
</template>

<style scoped>
  div {
    margin-bottom: 8px;
  }
  .outer {
    width: 100%;
    position: relative;
    padding-left: 80px;
  }
  label {
    text-align: left;
    width: 100px;
    display: inline-block;
    position: absolute;
    left :0;
  }
</style>
```

* 用 v-model 实现双向绑定，即 
  * javascript 数据可以同步到表单标签
  * 反过来用户在表单标签输入的新值也会同步到 javascript 这边
* 双向绑定只适用于表单这种带【输入】功能的标签，其它标签的数据绑定，单向就足够了
* 复选框这种标签，双向绑定的 javascript 数据类型一般用数组



#### 计算属性

有时在数据展示时要做简单的计算

```vue
<script setup lang="ts">
import { ref } from 'vue'
const firstName = ref('三')
const lastName = ref('张')

</script>

<template>
  <h2>{{lastName + firstName}}</h2>
  <h3>{{lastName + firstName}}</h3>
  <h4>{{lastName + firstName}}</h4>
</template>
```

看起来较为繁琐，可以用计算属性改进

```vue
<script setup lang="ts">
import { ref, computed } from 'vue'
const firstName = ref('三')
const lastName = ref('张')
const fullName = computed(() => {
  console.log('enter')
  return lastName.value + firstName.value
})
</script>

<template>
  <h2>{{fullName}}</h2>
  <h3>{{fullName}}</h3>
  <h4>{{fullName}}</h4>
</template>
```

* fullName 即为计算属性，它具备缓存功能，即 firstName 和 lastName 的值发生了变化，才会重新计算
* 如果用函数实现相同功能，则没有缓存功能

```vue
<script setup lang="ts">
import { ref } from 'vue'
const firstName = ref('三')
const lastName = ref('张')
function fullName() {
  console.log('enter')
  return lastName.value + firstName.value
}
</script>
  
<template>
  <h2>{{fullName()}}</h2>
  <h3>{{fullName()}}</h3>
  <h4>{{fullName()}}</h4>
</template>
```



#### xhr

浏览器中有两套 API 可以和后端交互，发送请求、接收响应，fetch api 前面我们已经介绍过了，另一套 api 是 xhr，基本用法如下

```js
const xhr = new XMLHttpRequest()
xhr.onload = function() {
    console.log(xhr.response)
}
xhr.open('GET', 'http://localhost:8080/api/students')
xhr.responseType = "json"
xhr.send()
```

但这套 api 虽然功能强大，但比较老，不直接支持 Promise，因此有必要对其进行改造

```typescript
function get(url: string) {
  return new Promise((resolve, reject)=>{
    const xhr = new XMLHttpRequest()
    xhr.onload = function() {
      if(xhr.status === 200){
        resolve(xhr.response)
      } else if(xhr.status === 404) {
        reject(xhr.response)
      } // 其它情况也需考虑，这里简化处理
    }
    xhr.open('GET', url)
    xhr.responseType = 'json'
    xhr.send()
  })
}
```

* Promise 对象适合用来封装异步操作，并可以配合 await 一齐使用
* Promise 在构造时，需要一个箭头函数，箭头函数有两个参数 resolve 和 reject
  * resolve 是异步操作成功时被调用，把成功的结果传递给它，最后会作为 await 的结果返回
  * reject 在异步操作失败时被调用，把失败的结果传递给它，最后在 catch 块被捉住
* await 会一直等到 Promise 内调用了 resolve 或 reject 才会继续向下运行



调用示例1：同步接收结果，不走代理

```js
try {
  const resp = await get("http://localhost:8080/api/students")
  console.log(resp)
} catch (e) {
  console.error(e)
}
```

调用示例2：走代理

```js
try {
  const resp = await get('/api/students')
  console.log(resp)  
} catch(e) {
  console.log(e)
}
```

* 走代理明显慢不少



#### axios

##### 基本用法

axios 就是对 xhr api 的封装，手法与前面例子类似

安装

```cmd
npm install axios
```

一个简单的例子

```vue
<script setup lang="ts">
import { ref, onMounted } from "vue";
import axios from "axios";

let count = ref(0);

async function getStudents() {
  try {
    const resp = await axios.get("/api/students");
    count.value = resp.data.data.length;
  } catch (e) {
    console.log(e);
  }
}

onMounted(() => {
  getStudents()
})
</script>

<template>
  <h2>学生人数为：{{ count }}</h2>
</template>
```

* onMounted 指 vue 组件生成的 html 代码片段，挂载完毕后被执行



再来看一个 post 例子

```vue
<script setup lang="ts">
import { ref } from "vue";
import axios from "axios";

const student = ref({
  name: '',
  sex: '男',
  age: 18
})

async function addStudent() {
  console.log(student.value)
  const resp = await axios.post('/api/students', student.value)
  console.log(resp.data.data)
}
</script>

<template>
  <div>
    <div>
      <input type="text" placeholder="请输入姓名" v-model="student.name"/>
    </div>
    <div>
      <label for="">请选择性别</label>
      男 <input type="radio" value="男" v-model="student.sex"/> 
      女 <input type="radio" value="女" v-model="student.sex"/>
    </div>
    <div>
      <input type="number" placeholder="请输入年龄" v-model="student.age"/>
    </div>
    <div>
      <input type="button" value="添加" @click="addStudent"/>
    </div>
  </div>
</template>
<style scoped>
div {
  font-size: 14px;
}
</style>
```



##### 环境变量

* 开发环境下，联调的后端服务器地址是 `http://localhost:8080`，
* 上线改为生产环境后，后端服务器地址为 `http://itheima.com`

这就要求我们区分开发环境和生产环境，这件事交给构建工具 vite 来做



默认情况下，vite 支持上面两种环境，分别对应根目录下两个配置文件 

* .env.development - 开发环境
* .env.production - 生产环境

针对以上需求，分别在两个文件中加入

```properties
VITE_BACKEND_API_BASE_URL = 'http://localhost:8080'
```

和

```properties
VITE_BACKEND_API_BASE_URL = 'http://itheima.com'
```

然后在代码中使用 vite 给我们提供的特殊对象 `import.meta.env`，就可以获取到 `VITE_BACKEND_API_BASE_URL` 在不同环境下的值

```js
import.meta.env.VITE_BACKEND_API_BASE_URL
```



默认情况下，不能智能提示自定义的环境变量，做如下配置：新增文件 `src/env.d.ts` 并添加如下内容

```typescript
/// <reference types="vite/client" />

interface ImportMetaEnv {
  readonly VITE_BACKEND_API_BASE_URL: string
  // 更多环境变量...
}

interface ImportMeta {
  readonly env: ImportMetaEnv
}
```

* 参考文档地址 [环境变量和模式 | Vite 官方中文文档 (vitejs.dev)](https://cn.vitejs.dev/guide/env-and-mode.html)



##### baseURL

可以自己创建一个 axios 对象，方便添加默认设置，新建文件 /src/api/request.ts

```typescript
// 创建新的 axios 对象
import axios from 'axios'
const _axios = axios.create({
  baseURL: import.meta.env.VITE_BACKEND_API_BASE_URL
})

export default _axios
```

然后在其它组件中引用这个 ts 文件，例如 /src/views/E8.vue，就不用自己拼接路径前缀了

```vue
<script setup lang="ts">
import axios from '../api/request'
// ...
await axios.post('/api/students', ...)    
</script>
```



##### 拦截器

```typescript
// 创建新的 axios 对象
import axios from 'axios'
const _axios = axios.create({
  baseURL: import.meta.env.VITE_BACKEND_API_BASE_URL
})

// 请求拦截器
_axios.interceptors.request.use(
  (config)=>{ // 统一添加请求头
    config.headers = {
      Authorization: 'aaa.bbb.ccc'
    }
    return config
  },
  (error)=>{ // 请求出错时的处理
    return Promise.reject(error)
  }
)

// 响应拦截器
_axios.interceptors.response.use(
  (response)=>{ // 状态码  2xx
    // 这里的code是自定义的错误码
    if(response.data.code === 200) {
      return response
    }     
    else if(response.data.code === 401) {       
      // 情况1
      return Promise.resolve({})
    }
    // ... 
  },
  (error)=>{ // 状态码 > 2xx, 400,401,403,404,500
    console.error(error) // 处理了异常
    if(error.response.status === 400) {
      // 情况1
    } else if(error.response.status === 401) {
      // 情况2
    } 
    // ...
    return Promise.resolve({})
  }
)

export default _axios
```

处理响应时，又分成两种情况

1. 后端返回的是标准响应状态码，这时会走响应拦截器第二个箭头函数，用 error.response.status 做分支判断
2. 后端返回的响应状态码总是200，用自定义错误码表示出错，这时会走响应拦截器第一个箭头函数，用 response.data.code 做分支判断

另外

* Promise.reject(error) 类似于将异常继续向上抛出，异常由调用者（Vue组件）来配合 try ... catch 来处理
* Promise.resolve({}) 表示错误已解决，返回一个空对象，调用者中接到这个空对象时，需要配合 ?. 来避免访问不存在的属性



#### 条件与列表

首先，新增模型数据 src/model/Model8080.ts

```typescript
export interface Student {
  id: number;
  name: string;
  sex: string;
  age: number;
}

// 如果 spring 错误，返回的对象格式
export interface SpringError {
  timestamp: string,
  status: number,
  error: string,
  message: string,
  path: string
}

// 如果 spring 成功，返回 list 情况
export interface SpringList<T> {
  data: T[],
  message?: string,
  code: number
}

// 如果 spring 成功，返回 page 情况
export interface SpringPage<T> {
  data: { list: T[], total: number },
  message?: string,
  code: number
}

// 如果 spring 成功，返回 string 情况
export interface SpringString {
  data: string,
  message?: string,
  code: number
}

import { AxiosResponse } from 'axios'
export interface AxiosRespError extends AxiosResponse<SpringError> { }
export interface AxiosRespList<T> extends AxiosResponse<SpringList<T>> { }
export interface AxiosRespPage<T> extends AxiosResponse<SpringPage<T>> { }
export interface AxiosRespString extends AxiosResponse<SpringString> { }
```

其中 

* AxiosRespPage 代表分页时的响应类型
* AxiosRespList 代表返回集合时的响应类型
* AxiosRespString 代表返回字符串时的响应类型
* AxiosRespError 代表 Spring 出错时时的响应类型

```vue
<script lang="ts" setup>
import { ref, onMounted } from "vue";
import axios from "../api/request";
import { Student, SpringList } from "../model/Model8080";

// 说明 students 数组类型为 Student[]
const students = ref<Student[]>([]);

async function getStudents() {
  // 说明 resp.data 类型是 SpringList<Student>
  const resp = await axios.get<SpringList<Student>>("/api/students");  
  console.log(resp.data.data);
  students.value = resp.data.data;
}

onMounted(() => getStudents());
</script>
<template>
  <div class="outer">
    <div class="title">学生列表</div>
    <div class="thead">
      <div class="row bold">
        <div class="col">编号</div>
        <div class="col">姓名</div>
        <div class="col">性别</div>
        <div class="col">年龄</div>
      </div>
    </div>
    <div class="tbody">
      <div v-if="students.length === 0">暂无数据</div>
      <template v-else>
        <div class="row" v-for="s of students" :key="s.id">
          <div class="col">{{ s.id }}</div>
          <div class="col">{{ s.name }}</div>
          <div class="col">{{ s.sex }}</div>
          <div class="col">{{ s.age }}</div>
        </div>
      </template>
    </div>
  </div>
</template>
<style scoped>
.outer {
  font-family: 华文行楷;
  font-size: 20px;
  width: 500px;
}

.title {
  margin-bottom: 10px;
  font-size: 30px;
  color: #333;
  text-align: center;
}

.row {
  background-color: #fff;
  display: flex;
  justify-content: center;
}

.col {
  border: 1px solid #f0f0f0;
  width: 15%;
  height: 35px;
  text-align: center;
  line-height: 35px;
}

.bold .col {
  background-color: #f1f1f1;
}
</style>
```

* 加入泛型是为了更好的提示
* v-if 与 v-else 不能和 v-for 处于同一标签
* template 标签还有一个用途，就是用它少生成一层真正 html 代码
* 可以看到将结果封装为响应式数据还是比较繁琐的，后面会使用 useRequest 改进



#### 监听器

利用监听器，可以在【响应式】的基础上添加一些副作用，把更多的东西变成【响应式的】

* 原本只是数据变化 => 页面更新

* watch 可以在数据变化时 => 其它更新

```vue
<template>
  <input type="text" v-model="name" />
</template>

<script setup lang="ts">
import { ref, watch } from "vue";
    
function useStorage(name: string) {
  const data = ref(sessionStorage.getItem(name) ?? "");
  //参数1：要监听的数据；参数2：数据变化时要执行的箭头函数
  watch(data, (newValue) => {
    sessionStorage.setItem(name, newValue);//存储数据
  });
  return data;
}
const name = useStorage("name");
</script>
```

* 名称为 useXXXX 的函数，作用是返回带扩展功能的【响应式】数据
* localStorage   即使浏览器关闭，数据还在
* sessionStorage  数据工作在浏览器活动期间



#### vueuse

安装

```cmd
npm install @vueuse/core
```

一些函数的用法

```vue
<template>
  <h3>X: {{x}}</h3>
  <h3>Y: {{y}}</h3>

  <h3>{{count}}</h3>
  <input type="button" @click="inc()" value="+">
  <input type="button" @click="dec()" value="-">

  <input type="text" v-model="name">
</template>
<script setup lang="ts">
import { useMouse, useCounter, useStorage } from '@vueuse/core'
//返回鼠标的位置
const {x, y} = useMouse()
//count 计数的变量，inc是增加函数，dec是减少函数
const {count, inc, dec} = useCounter()

const name = useStorage("name", "")
</script>
```



#### useRequest

响应式的 axios 封装，官网地址 [一个 Vue 请求库 | VueRequest (attojs.org)](https://next.cn.attojs.org/)

首先安装 vue-request

```cmd
npm install vue-request@next
```

组件

```vue
<template>
  <h3 v-if="students.length === 0">暂无数据</h3>
  <ul v-else>
    <li v-for="s of students" :key="s.id">
      <span>{{s.name}}</span>
      <span>{{s.sex}}</span>
      <span>{{s.age}}</span>
    </li>
  </ul>
</template>
<script setup lang="ts">
import axios from "../api/request"
import { useRequest } from 'vue-request'
import { computed } from 'vue'
import { AxiosRespList, Student } from '../model/Model8080'

// data 代表就是 axios 的响应对象
const { data } = useRequest<AxiosRespList<Student>>(() => axios.get('/api/students'))

const students = computed(()=>{
  return data?.value?.data.data || []
})
</script>
<style scoped>
ul li {
  list-style: none;
  font-family: "华文行楷";
}

li span:nth-child(1) {
  font-size: 24px;
}
li span:nth-child(2) {
  font-size: 12px;
  color: crimson;
  vertical-align: bottom;
}
li span:nth-child(3) {
  font-size: 12px;
  color: darkblue;
  vertical-align: top;
}
</style>
```

* data.value 的取值一开始是 undefined，随着响应返回变成 axios 的响应对象
* 用 computed 进行适配



#### usePagination

在 src/model/Model8080.ts 中补充类型说明

```typescript
export interface StudentQueryDto {
  name?: string,
  sex?: string,
  age?: string, // 18,20
  page: number,
  size: number
}
```

* js 中类似于 18,20 这样以逗号分隔字符串，会在 get 传参时转换为 java 中的整数数组

编写组件

```vue
<template>
  <input type="text" placeholder="请输入姓名" v-model="dto.name">
  <select v-model="dto.sex">
    <option value="" selected>请选择性别</option>
    <option value="男">男</option>
    <option value="女">女</option>
  </select>
  <input type="text" placeholder="请输入年龄范围" v-model="dto.age">
  <br>
  <input type="text" placeholder="请输入页码" v-model="dto.page">
  <input type="text" placeholder="请输入页大小" v-model="dto.size">
  <input type="button" value="搜索" @click="search">
  <hr>
  <h3 v-if="students.length === 0">暂无数据</h3>
  <ul v-else>
    <li v-for="s of students" :key="s.id">
      <span>{{s.name}}</span>
      <span>{{s.sex}}</span>
      <span>{{s.age}}</span>
    </li>
  </ul>
  <hr>
  总记录数{{total}} 总页数{{totalPage}}
</template>
<script setup lang="ts">
import axios from "../api/request"
import { usePagination } from 'vue-request'
import { computed, ref } from 'vue'
import { AxiosRespPage, Student, StudentQueryDto } from '../model/Model8080'

const dto = ref<StudentQueryDto>({name:'', sex:'', age:'', page:1, size:5})

// data 代表就是 axios 的响应对象
// 泛型参数1: 响应类型
// 泛型参数2: 请求类型
const { data, total, totalPage, run } = usePagination<AxiosRespPage<Student>, StudentQueryDto[]>(
  (d) => axios.get('/api/students/q', {params: d}), // 箭头函数
  {
    defaultParams: [ dto.value ], // 默认参数, 会作为参数传递给上面的箭头函数
    pagination: {
      currentKey: 'page', // 指明当前页属性
      pageSizeKey: 'size', // 指明页大小属性
      totalKey: 'data.data.total' // 指明总记录数属性
    } 
  } // 选项
)

const students = computed(()=>{
  return data?.value?.data.data.list || []
})

function search() {
  run(dto.value) // 会作为参数传递给usePagination的箭头函数
}
</script>
<style scoped>
ul li {
  list-style: none;
  font-family: "华文行楷";
}

li span:nth-child(1) {
  font-size: 24px;
}
li span:nth-child(2) {
  font-size: 12px;
  color: crimson;
  vertical-align: bottom;
}
li span:nth-child(3) {
  font-size: 12px;
  color: darkblue;
  vertical-align: top;
}
input,select {
  width: 100px;
}
</style>
```

* usePagination 只需要定义一次，后续还想用它内部的 axios 发请求，只需调用 run 函数



#### 子组件

##### 例1

定义子组件 Child1

```vue
<template>
  <div class="container">
    <div class="card">
      <div>
        <p class="name">{{name}}</p>
        <p class="location">{{country}}</p>
      </div>
      <img :src="avatar || '/src/assets/vue.svg'"/>
    </div>
  </div>
</template>
<script setup lang="ts">
// 定义属性,  编译宏
defineProps<{name:string,country:string,avatar?:string}>()
</script>
<style scoped>
.container {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  flex-direction: row-reverse;
}
.name {
  font-weight: bold;
}
.location {
  font-size: 0.8em;
  color: #6d597a;
}
.card {
  display: flex;
  justify-content: space-evenly;
  padding: 1em;
  margin: 1rem;
  border-radius: 5px;
  background: #fff;
  width: 200px;
  box-shadow: 0 14px 28px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.22);
}

.card:hover {
  transform: rotate(-5deg);
}

.card img {
  margin-left: 1em;
  border-radius: 50%;
  max-width: 55px;
  max-height: 55px;
}
</style>
```

父组件引用

```vue
<template>
  <Child1 name="张三" country="中国" avatar="/src/assets/vue.svg"></Child1>
  <Child1 name="李四" country="印度" avatar="/vite.svg"></Child1>
  <Child1 name="王五" country="韩国" ></Child1>
</template>
<script lang="ts" setup>
import Child1 from '../components/Child1.vue';
</script>
```



##### 例2

首先添加类型说明 model/ModelRandomUser.ts

```typescript
import { AxiosResponse } from "axios";
export interface AxiosRespResults extends AxiosResponse<Results>{}

export interface Results {
  info: {
    page: number,
    results: number
  },
  results: Result[]
}

export interface Result {
  gender: 'male' | 'female',
  name: {
    first: string,
    last: string
  },
  location: {
    country: string
  },
  picture: {
    medium: string
  },
  login: {
    username: string
  }
}
```

子组件不变，父组件使用子组件

```vue
<!-- 父组件 -->
<template>
  <Child1 v-for="u of users" 
    :name="u.name.first" 
    :country="u.location.country" 
    :avatar="u.picture.medium"
    :key="u.login.username"></Child1>
</template>
<script setup lang="ts">
import axios from "axios";
import { useRequest } from "vue-request";
import { computed } from "vue";
import { AxiosRespResults } from '../model/ModelRandomUser'
import Child1 from "../components/Child1.vue";

const { data } = useRequest<AxiosRespResults>(
  ()=>axios.get('https://randomuser.me/api/?results=3')
)

const users = computed(()=>{
  return data.value?.data.results || []
})
</script>
```

如果觉得 Result 数据结构嵌套太复杂，还可以做一个类型映射

```vue
<!-- 父组件 -->
<template>
  <Child1 v-for="u of users" 
    :name="u.name" 
    :country="u.country" 
    :avatar="u.avatar"
    :key="u.username"></Child1>
</template>
<script setup lang="ts">
import axios from "axios";
import { useRequest } from "vue-request";
import { computed } from "vue";
import { AxiosRespResults, Result } from '../model/ModelRandomUser'
import Child1 from "../components/Child1.vue";

const { data } = useRequest<AxiosRespResults>(
  ()=>axios.get('https://randomuser.me/api/?results=3')
)

const users = computed(()=>{
  return data.value?.data.results.map(resultToUser) || []
})

interface User {
  name: string,
  country: string,
  avatar: string,
  username: string
}
function resultToUser(r:Result):User {
  return {
    name: r.name.first,
    country: r.location.country,
    avatar: r.picture.medium,
    username: r.login.username
  }
}
</script>
```

* resultToUser 将 Result 类型映射为 User 类型



### 3. Vue 进阶

### 1) Antdv

添加必要插件

```cmd
npm install ant-design-vue
```

* ant-design-vue 组件库插件

引入 antdv 功能，修改 main.ts

```typescript
import { createApp } from 'vue'
import './style.css'
import App from './App.vue'
import antd from 'ant-design-vue'
import 'ant-design-vue/dist/antd.css'

createApp(App).use(antd).mount('#app')
```



#### 表格

```vue
<template>
  <!-- <a-table :columns="columns" :dataSource="students" rowKey="id"></a-table> -->
  <a-table :columns="columns" :dataSource="students" :rowKey="rowKey"></a-table>
</template>
<script setup lang="ts">
import axios from "../api/request";
import { ref, computed } from "vue";
import { useRequest } from "vue-request";
import { AxiosRespList, Student } from "../model/Model8080";

const {data} = useRequest<AxiosRespList<Student>>(
  ()=>axios.get('/api/students')
)

const students = computed(()=>{
  return data.value?.data.data || []
})

function rowKey(r:Student) {
  return r.id
}

const columns = ref([
  {
    title:'编号',
    dataIndex:'id'
  },
  {
    title:'姓名',
    dataIndex:'name'
  },
  {
    title:'性别',
    dataIndex:'sex'
  },
  {
    title:'年龄',
    dataIndex:'age'
  }
])
</script>
```



#### 分页

```vue
<template>
  <a-table :columns="columns" :data-source="students" row-key="id"
   :pagination="pagination" @change="tableChange"></a-table>
</template>
<script setup lang="ts">
import axios from "../api/request";
import { ref, computed } from "vue";
import { usePagination } from "vue-request";
import { AxiosRespPage, Student, StudentQueryDto } from "../model/Model8080";
import { PaginationProps } from "ant-design-vue";
import DateBody from "ant-design-vue/lib/vc-picker/panels/DatePanel/DateBody";

const dto = ref({page: 1, size: 5})

const {data, total, run} = usePagination<AxiosRespPage<Student>, StudentQueryDto[]>(
  (d)=> axios.get('/api/students/q', {params:d}),
  {
    defaultParams: [dto.value],
    pagination: {
      currentKey: "page",
      pageSizeKey: 'size',
      totalKey: 'data.data.total'
    }
  }
)

// 在页号或页大小改变时调用
function tableChange(pagination: PaginationProps) { 
  console.log(pagination)
  dto.value.page = pagination.current ?? 1
  dto.value.size = pagination.pageSize ?? 5
  run(dto.value)
}

const pagination = computed<PaginationProps>(()=>{
  return {
    current: dto.value.page, // 当前页
    pageSize: dto.value.size, // 页大小
    total: total.value,       // 总记录数
    showSizeChanger: true,    // 显示页大小的下拉列表
    pageSizeOptions: ["1","2","3","4","5"] // 自定义下拉列表内容
  }
})

const students = computed(()=>{
  return data.value?.data.data.list || []
})

const columns = ref([
  {
    title: "编号",
    dataIndex: "id",
  },
  {
    title: "姓名",
    dataIndex: "name",
  },
  {
    title: "性别",
    dataIndex: "sex",
  },
  {
    title: "年龄",
    dataIndex: "age",
  },
]);
</script>
```



#### 搜索、删除

```vue
<template>
  <a-row>
    <a-col :span="2">
      <a-button type="primary" size="small">新增</a-button>
    </a-col>
    <a-col :span="4">
      <a-popconfirm title="确认要删除选中学生吗?"
        ok-text="确定" cancel-text="取消" @confirm="onDeleteIds"
        @visibleChange="onVisibleChange" :visible="visible">
        <a-button type="primary" size="small">删除选中</a-button>
      </a-popconfirm>
    </a-col>
    <a-col :span="4">
    </a-col>
    <a-col :span="4">
      <a-input v-model:value="dto.name" placeholder="输姓名" size="small"></a-input>
    </a-col>
    <a-col :span="4">
      <a-select v-model:value="dto.sex" placeholder="选性别" :allowClear="true" size="small">
        <a-select-option value="男">男</a-select-option>
        <a-select-option value="女">女</a-select-option>
      </a-select>
    </a-col>
    <a-col :span="4">
      <a-select v-model:value="dto.age" placeholder="选年龄" :allowClear="true" size="small">
        <a-select-option value="0,20">20以下</a-select-option>
        <a-select-option value="21,30">21~30</a-select-option>
        <a-select-option value="31,40">31~40</a-select-option>
        <a-select-option value="40,120">40以上</a-select-option>
      </a-select>
    </a-col>
    <a-col :span="2">
      <a-button @click="tableChange" type="primary" size="small">搜索</a-button>
    </a-col>
  </a-row>
  <hr>
  <a-table :columns="columns" :data-source="students" row-key="id"
    :pagination="pagination" @change="tableChange"
    :row-selection="{selectedRowKeys:ids,onChange:onSelectChange}">
    <template #bodyCell="{column, record}">
      <template v-if="column.dataIndex==='name'">
      {{record.name + (record.sex==='男'?'(大侠)':'(女侠)')}}
      </template>

      <template v-else-if="column.dataIndex==='operation'">
      <a>修改</a>
      <a-divider type="vertical"></a-divider>
      <a-popconfirm title="确认要删除该学生吗?"
        ok-text="确定" cancel-text="取消" @confirm="onDelete(record.id)">
        <a>删除</a>   
      </a-popconfirm>         
      </template>
    </template>
  </a-table>
  
</template>
<script setup lang="ts">
import axios from "../api/request";
import { ref, computed } from "vue";
import { usePagination, useRequest } from "vue-request";
import { AxiosRespPage, AxiosRespString, Student, StudentQueryDto } from "../model/Model8080";
import { PaginationProps } from "ant-design-vue";

// >>>>>>>>>>>>>> 搜索功能开始
const dto = ref({page: 1, size: 5, name: '', sex: null, age: null})

const {data, total, run: search} = usePagination<AxiosRespPage<Student>, StudentQueryDto[]>(
  (d) => axios.get('/api/students/q', {params:d}),
  {
    defaultParams: [dto.value],
    pagination: {
      currentKey: "page",
      pageSizeKey: 'size',
      totalKey: 'data.data.total'
    }
  }
)

function tableChange(pagination: PaginationProps) { 
  // console.log(pagination)
  dto.value.page = pagination.current ?? 1
  dto.value.size = pagination.pageSize ?? 5
  search(dto.value)
}

const pagination = computed<PaginationProps>(()=>{
  return {
    current: dto.value.page, // 当前页
    pageSize: dto.value.size, // 页大小
    total: total.value,       // 总记录数
    showSizeChanger: true,    // 显示页大小的下拉列表
    pageSizeOptions: ["1","2","3","4","5"] // 自定义下拉列表内容
  }
})

const students = computed(()=>{
  return data.value?.data.data.list || []
})
// <<<<<<<<<<<<<< 搜索功能结束


// >>>>>>>>>>>>>> 删除功能开始
async function onDelete(id:number) {
  // console.log("学生id是:"+id)
  await deleteById(id)      // 删除请求 删除响应
  search(dto.value)        //                   查询请求 查询响应
}

const { runAsync: deleteById } = useRequest<AxiosRespString, number[]>(
  (id) => axios.delete(`/api/students/${id}`),
  {
    manual: true
  }
)
// <<<<<<<<<<<<<< 删除功能结束

// >>>>>>>>>>>>>> 删除选中开始
const ids = ref<number[]>([])

function onSelectChange(keys:number[]) {
  // console.log(keys)
  ids.value = keys
}

async function onDeleteIds() {
  await deleteByIds(ids.value)
  ids.value = []
  search(dto.value)
}

const { runAsync: deleteByIds } = useRequest<AxiosRespString, number[][]>(
  (ids)=>axios.delete('/api/students', {data: ids}),
  {
    manual: true
  }
)

const visible = ref(false)

function onVisibleChange(v:boolean) {
  if(!v) { // 希望隐藏
    visible.value = false
  } else { // 希望显示
    visible.value = ids.value.length > 0
  }
}
// <<<<<<<<<<<<<< 删除选中结束

const columns = ref([
  {
    title: "编号",
    dataIndex: "id",
  },
  {
    title: "姓名",
    dataIndex: "name",
  },
  {
    title: "性别",
    dataIndex: "sex",
  },
  {
    title: "年龄",
    dataIndex: "age",
  },
  {
    title: '操作',
    dataIndex: 'operation'
  }
]);
</script>
<style scoped>
  .ant-input, .ant-select {
    width: 80px;
  }
</style>
```



#### 新增、修改

子组件

```vue
<template>
  <a-modal :visible="visible" :title="title" 
    @ok="onOk" @cancel="onCancel">
    <a-form>
      <a-form-item label="编号" v-if="id">
        <a-input readonly v-model:value="id"></a-input>
      </a-form-item>
      <a-form-item label="姓名">
        <a-input v-model:value="dto.name"></a-input>
      </a-form-item>
      <a-form-item label="性别">
        <a-radio-group v-model:value="dto.sex">
          <a-radio-button value="男">男</a-radio-button>
          <a-radio-button value="女">女</a-radio-button>
        </a-radio-group>
      </a-form-item>
      <a-form-item label="年龄">
        <a-input-number v-model:value="dto.age"></a-input-number>
      </a-form-item>
    </a-form>
  </a-modal>
</template>
<script setup lang="ts">
import axios from "../api/request";
import { ref, computed } from "vue";
import { useRequest } from "vue-request";
import { StudentSaveDto, AxiosRespString } from "../model/Model8080";
import { Form } from 'ant-design-vue'

// 定义属性
const props = defineProps<{id:number, dto:StudentSaveDto, visible:boolean}>()

const title = computed(()=> props.id===0?'新增学生':'修改学生')

// 定义事件
const emit = defineEmits(['update:visible', 'saved'])

async function onOk() {
  if(props.id === 0) {
    await insert(props.dto)
  } else {
    await update(props.dto)
  }
  emit('saved')
  // 发送事件给父组件, 希望把 visible 改为 false
  emit('update:visible', false) 
}

function onCancel() {
  // 发送事件给父组件, 希望把 visible 改为 false
  emit('update:visible', false)
}

const {runAsync:insert} = useRequest<AxiosRespString,StudentSaveDto[]>(
  (dto)=>axios.post('/api/students', dto),
  {
    manual: true
  }
)

const {runAsync:update} = useRequest<AxiosRespString,StudentSaveDto[]>(
  (dto)=>axios.put(`/api/students/${props.id}`, dto),
  {
    manual: true
  }
)
</script>
```

父组件使用子组件

```vue
<A4Save :id="id" :dto="saveDto" v-model:visible="saveVisible"></A4Save>

<script setup lang="ts">
// ...
// >>>>>>>>>>>>>> 新增、修改开始
const saveVisible = ref(false)
const id = ref(0)
const saveDto = reactive({name:'', sex:'男', age:18})

function onInsert() {
  saveVisible.value = true
  id.value = 0
  Object.assign(saveDto, {name:'', sex:'男', age:18})
}

function onUpdate(record: Student) {
  saveVisible.value = true
  id.value = record.id
  Object.assign(saveDto, record)
}

function onSaved() {
  search(dto.value)
}    
// <<<<<<<<<<<<<< 新增、修改结束
</script>
```

* saveDto 使用 reactive 包装，是为了解决后续表单校验失效问题

* Object.assign 是将源对象（参数2）的属性值赋值给目标对象（参数1）的同名属性，效果等价于

  ```js
  saveDto.name = record.name
  saveDto.sex = record.sex
  saveDto.age = record.age
  ```



#### 全局消息

在 request.ts 中对响应消息统一处理

```typescript
import { message } from 'ant-design-vue'

// ...
// 响应拦截器
_axios.interceptors.response.use(
  (response)=>{ // 状态码  2xx
    if(response.data.message) {
      message.success(response.data.message, 3)
    }    
    // ... 
  },
  (error)=>{ // 状态码 > 2xx, 400,401,403,404,500
    // ...
  }
)
```



#### 表单校验

```vue
<template>
  <a-modal :visible="visible" :title="title" 
    @ok="onOk" @cancel="onCancel">
    <a-form>
      <a-form-item label="编号" v-if="id">
        <a-input readonly v-model:value="id"></a-input>
      </a-form-item>
      <a-form-item label="姓名" v-bind="validateInfos.name">
        <a-input v-model:value="dto.name"></a-input>
      </a-form-item>
      <a-form-item label="性别" v-bind="validateInfos.sex">
        <a-radio-group v-model:value="dto.sex">
          <a-radio-button value="男">男</a-radio-button>
          <a-radio-button value="女">女</a-radio-button>
        </a-radio-group>
      </a-form-item>
      <a-form-item label="年龄" v-bind="validateInfos.age">
        <a-input-number v-model:value="dto.age"></a-input-number>
      </a-form-item>
    </a-form>
  </a-modal>
</template>
<script setup lang="ts">
import axios from "../api/request";
import { ref, computed } from "vue";
import { useRequest } from "vue-request";
import { StudentSaveDto, AxiosRespString } from "../model/Model8080";
import { Form } from 'ant-design-vue'

// 定义属性
const props = defineProps<{id:number, dto:StudentSaveDto, visible:boolean}>()

const title = computed(()=> props.id===0?'新增学生':'修改学生')

// 定义事件
const emit = defineEmits(['update:visible', 'saved'])

async function onOk() {
  try {
    // 提交前校验
    await validate()
    if(props.id === 0) {
      await insert(props.dto)
    } else {
      await update(props.dto)
    }
    emit('saved')
    // 发送事件给父组件, 希望把 visible 改为 false
    emit('update:visible', false) 
  } catch (e) {
    console.error(e)
  }
}

function onCancel() {
  // 发送事件给父组件, 希望把 visible 改为 false
  emit('update:visible', false)
}

const {runAsync:insert} = useRequest<AxiosRespString,StudentSaveDto[]>(
  (dto)=>axios.post('/api/students', dto),
  {
    manual: true
  }
)

const {runAsync:update} = useRequest<AxiosRespString,StudentSaveDto[]>(
  (dto)=>axios.put(`/api/students/${props.id}`, dto),
  {
    manual: true
  }
)

const rules = ref({
  name: [
    {required: true, message:'姓名必须'},
    {min:2, message:'字符数至少为2'}
  ],
  sex: [
    {required: true, message:'性别必须'}
  ],
  age: [
    {required: true, message:'年龄必须'},
    {min:10, message:'年龄最小为10岁', type:'number'},
    {max:120, message:'年龄最大为120岁', type:'number'}
  ]
})

// 参数1: 待校验的数据
// 参数2: 校验规则
const { validateInfos, validate } = Form.useForm(props.dto, rules)
</script>
```



### 2) vue-router

#### 安装

```cmd
npm install vue-router@4
```



#### 创建 router

首先创建一个 /src/router/a5router.ts 文件，在其中定义路由

```typescript
import {createRouter, createWebHashHistory} from 'vue-router'
import A51 from '../views/A51.vue'
import A52 from '../views/A52.vue'
// 路由 => 路径和组件之间的对应关系
const routes = [
  {
    path: '/a1',
    component: A51
  },
  {
    path: '/a2', 
    component: A52
  }
]

const router = createRouter({ 
  history: createWebHashHistory(), // 路径格式
  routes: routes // 路由数组
})

export default router
```

* createWebHashHistory 是用 # 符号作为【单页面】跳转技术，上面两个路由访问时路径格式为
  * http://localhost:7070/#/a1
  * http://localhost:7070/#/a2

* 每个路由都有两个必须属性

  * path：路径

  * component：组件

* createRouter 用来创建 router 对象，作为默认导出

需要在 main.ts 中导入 router 对象：

```typescript
// ...
import A5 from './views/A5.vue'  // vue-router
import router from './router/a5router'
createApp(A5).use(antdv).use(router).mount('#app')
```

A5 是根组件，不必在 router 中定义，但需要在其中定义 router-view，用来控制路由跳转后，A51、A52 这些组件的显示位置，内容如下

```vue
<template>
  <div class="a5">
    <router-view></router-view>
  </div>
</template>
```

效果如下

![image-20220926145812121](D:\2022.js\imgs\image-20220926145812121.png)

![image-20220926145959690](D:\2022.js\imgs\image-20220926145959690.png)



#### 动态导入

```typescript
import {createRouter, createWebHashHistory} from 'vue-router'
import A51 from '../views/A51.vue'
import A52 from '../views/A52.vue'
const routes = [
  // ...
  {
    path: '/a3',
    component: () => import('../views/A53.vue')
  }
]
```

* 用 import 关键字导入，效果是打包时会将组件的 js 代码都打包成一个大的 js 文件，如果组件非常多，会影响页面加载速度
* 而 import 函数导入（动态导入），则是按需加载，即
  * 当路由跳转到 /a3 路径时，才会去加载 A53 组件对应的 js 代码
  * vue-router 官方推荐采用动态导入



#### 嵌套路由

如果希望再嵌套更深层次的路由跳转，例如：希望在 A53 组件内再进行路由跳转

![image-20220926150819624](D:\2022.js\imgs\image-20220926150819624.png)

首先，修改 A53.vue

```vue
<template>
  <div class="a53">
    <router-view></router-view>
  </div>
</template>
```

其次，再修改 /src/router/a5router.ts 文件 内容

```typescript
import {createRouter, createWebHashHistory} from 'vue-router'
import A51 from '../views/A51.vue'
import A52 from '../views/A52.vue'
const routes = [
  // ...
  {
    path: '/a3',
    component: () => import('../views/A53.vue'),
    children: [
      {
        path: 'student',
        component: () => import('../views/A531.vue')
      },
      {
        path: 'teacher',
        component: () => import('../views/A532.vue')
      }
    ]
  }
]

// ...
```

将来访问 /a3/student 时，效果为

![image-20220926151216217](D:\2022.js\imgs\image-20220926151216217.png)

访问 /a3/teacher 时，效果为

![image-20220926151249403](D:\2022.js\imgs\image-20220926151249403.png)



#### 重定向

用法1

```typescript
import {createRouter, createWebHashHistory} from 'vue-router'
import A51 from '../views/A51.vue'
import A52 from '../views/A52.vue'
const routes = [
  // ...
  {
    path: '/a3',
    component: () => import('../views/A53.vue'),
    redirect: '/a3/student', // 重定向到另外路径
    children: [
      {
        path: 'student',
        component: () => import('../views/A531.vue')
      },
      {
        path: 'teacher',
        component: () => import('../views/A532.vue')
      }
    ]
  }
]
// ...
```

效果是，页面输入 /a3，紧接着会重定向跳转到 /a3/student



用法2

```typescript
import {createRouter, createWebHashHistory} from 'vue-router'
import A51 from '../views/A51.vue'
import A52 from '../views/A52.vue'
const routes = [
  {
    path: '/a1',
    component: A51
  },
  {
    path: '/a2', 
    component: A52
  },
  // ...
  {
    path: '/:pathMatcher(.*)*', // 可以匹配剩余的路径
    redirect: '/a2'
  }
]
// ...
```

效果是，当页面输入一个不存在路径 /aaa 时，会被 `path: '/:pathMatcher(.*)*'` 匹配到，然后重定向跳转到 A52 组件去



#### 主页布局

借助 antdv 的 layout 组件，可以实现主页【上】【左】【右】布局

```vue
<template>
  <div class="a53">
    <a-layout>
      <a-layout-header></a-layout-header>
      <a-layout>
        <a-layout-sider></a-layout-sider>
        <a-layout-content>
          <router-view></router-view>
        </a-layout-content>
      </a-layout>
    </a-layout>
  </div>
</template>
<style scoped>
.a53 {
  height: 100%;
  background-color: rgb(220, 225, 255);
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg'%3E%3Ctext x='35' y='10' font-size='14' font-family='system-ui, sans-serif' text-anchor='middle' dominant-baseline='middle'%3EA53(主页)%3C/text%3E%3C/svg%3E");
  padding: 20px;
  box-sizing: border-box;
}
.ant-layout-header {
  height: 50px;
  background-color:darkseagreen;
}

.ant-layout-sider {
  background-color:lightsalmon;
}

.ant-layout-content {
  background-color: aliceblue;
}

.ant-layout-footer {
  background-color:darkslateblue;
  height: 30px;
}

.ant-layout {
  height: 100%;
}

.ant-layout-has-sider {
  height: calc(100% - 50px);
}
</style>
```



#### 侧边栏菜单

```vue
<template>
  <div class="a53">
    <a-layout>
      <a-layout-header></a-layout-header>
      <a-layout>
        <a-layout-sider>
          <a-menu theme="dark" mode="inline">
            <a-menu-item :key="1">
              <router-link to="/a3/student">菜单1</router-link>
            </a-menu-item>
            <a-menu-item :key="2">
              <router-link to="/a3/teacher">菜单2</router-link>
            </a-menu-item>
            <a-menu-item :key="3">菜单3</a-menu-item>
            <a-sub-menu :key="4" title="菜单4">
              <a-menu-item :key="41">菜单41</a-menu-item>
              <a-menu-item :key="42">菜单42</a-menu-item>
            </a-sub-menu>
          </a-menu>
        </a-layout-sider>
        <a-layout-content>
          <router-view></router-view>
        </a-layout-content>
      </a-layout>
    </a-layout>
  </div>
</template>
```

* a-menu-item 与 a-sub-menu 都必须为 key 属性唯一赋值，否则会产生混乱
* router-link 标签用来切换路由，to 是目标路由的路径
* theme 属性定义菜单的主题（默认亮色主题，dark 为暗色主题）
* mode 属性定义子菜单的展示模式（默认弹出，inline 显示在下方）



#### 菜单图标

安装图标依赖

```cmd
npm install @ant-design/icons-vue
```

菜单中使用图标

```vue
<template>
  <div class="a53">
    <a-layout>
      <a-layout-header></a-layout-header>
      <a-layout>
        <a-layout-sider>
          <a-menu theme="dark" mode="inline">
            <a-menu-item :key="1">
              <template #icon>
                <highlight-outlined />
              </template>
              <router-link to="/a3/student">菜单1</router-link>
            </a-menu-item>
            <a-menu-item :key="2">
              <template #icon>
                <align-center-outlined />
              </template>
              <router-link to="/a3/teacher">菜单2</router-link>
            </a-menu-item>
            <a-menu-item :key="3">
              <template #icon>
                <strikethrough-outlined />
              </template>
              菜单3</a-menu-item>
            <a-sub-menu :key="4" title="菜单4">
              <template #icon>
                <sort-descending-outlined />
              </template>
              <a-menu-item :key="41">菜单41</a-menu-item>
              <a-menu-item :key="42">菜单42</a-menu-item>
            </a-sub-menu>
          </a-menu>
        </a-layout-sider>
        <a-layout-content>
          <router-view></router-view>
        </a-layout-content>
      </a-layout>
    </a-layout>
  </div>
</template>
<script setup lang="ts">
import {HighlightOutlined, AlignCenterOutlined, StrikethroughOutlined, SortDescendingOutlined} from '@ant-design/icons-vue'
</script>
```

* 图标组件没有全局绑定，需要 import 之后才能使用
* 用 `<template #icon></template>` 插槽，才能确定图标展示的位置（菜单文字之前）



#### 二次封装图标组件

最终希望用统一的图标组件去使用图标，图标名只是作为一个属性值传递进去，例如：

使用者

```vue
<template>
  <a-icon icon="highlight-outlined"></a-icon>
  <a-icon icon="align-center-outlined"></a-icon>
  <a-icon icon="strikethrough-outlined"></a-icon>
  <a-icon icon="sort-descending-outlined"></a-icon>
</template>
<script setup lang="ts">
import AIcon from '../components/AIcon1.vue'
</script>
```

##### 方法1，使用 vue 组件

```vue
<script lang="ts" setup>
import {HighlightOutlined, AlignCenterOutlined, StrikethroughOutlined, SortDescendingOutlined} from '@ant-design/icons-vue'
const props = defineProps<{icon:string}>()
</script>
<template>
  <highlight-outlined v-if="icon==='highlight-outlined'"></highlight-outlined>
  <align-center-outlined v-else-if="icon==='align-center-outlined'"></align-center-outlined>
  <strikethrough-outlined v-else-if="icon==='strikethrough-outlined'"></strikethrough-outlined>
  <sort-descending-outlined v-else-if="icon==='sort-descending-outlined'"></sort-descending-outlined>
</template>
```

* 缺点：实现太笨

##### 方法2，使用函数式组件

```typescript
import { h } from "vue"
import * as Icons from '@ant-design/icons-vue'

interface Module {
  [p:string]: any
}

// 参数1: 组件属性
const AIcon = (props:{icon:string}) => {
  // console.log(props.icon)
  // console.log(Icons)
  // 参数1: 组件对象
  const im: Module = Icons
  return h(im[toCamelCase(props.icon)])
}

export default AIcon

// 将-分隔的单词转换为大驼峰命名的单词
function toCamelCase(str: string) { // highlight-outlined
  return str.split('-') // ['highlight', 'outlined']
    .map((e)=> e.charAt(0).toUpperCase() + e.slice(1) ) // ['Highlight', 'Outlined']
    .join('')
}
/*
Icons 的结构如下
{
  HighlightOutlined: HighlightOutlined组件对象,
  MonitorOutlined: MonitorOutlined组件对象,
  ...
}
*/
```

* 需要动态生成标签的时候，可以考虑使用函数式组件

##### 方法3，使用 jsx 组件

首先，安装  

```cmd
npm install @vitejs/plugin-vue-jsx -D
```

配置 vite.config.ts

```typescript
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import vueJsx from '@vitejs/plugin-vue-jsx'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue(), vueJsx()]
})
```

编写一个 Hi.tsx 组件

```tsx
export default {
  props: {
    msg: String
  },
  setup(props: { msg: string }) {
    return () => <h5>{props.msg}</h5>
  }
}
```

然后被其它组件使用

```vue
<script setup lang="ts">
import Hi from '../components/Hi'
</script>

<template>
  <Hi msg="Hello,World"></Hi>
</template>
```

用 jsx 实现图标组件

```typescript
import * as Icons from '@ant-design/icons-vue'

interface Module {
  [p:string]: any
}

function toCamelCase(str: string) { // highlight-outlined
  return str
    .split("-") // ['highlight', 'outlined']
    .map((e) => e.charAt(0).toUpperCase() + e.slice(1)) // ['Highlight', 'Outlined']
    .join(""); // HighlightOutlined
}

export default {
  props: {
    icon: String
  },
  setup(props: {icon: string}) {
    const im: Module = Icons
    const tag = im[toCamelCase(props.icon)] // 图标组件
    // HighlightOutlined
    return ()=> <tag></tag> // 返回组件标签
  }
}
```



#### 动态路由与菜单

##### 路由文件

a6router.js

```typescript
import { createRouter, createWebHashHistory } from 'vue-router'
import { useStorage } from '@vueuse/core'
import { Route, Menu } from '../model/Model8080'
const clientRoutes = [
  {
    path: '/login',
    name: 'login',
    component: () => import('../views/A6Login.vue')
  },
  {
    path: '/404',
    name: '404',
    component: () => import('../views/A6NotFound.vue')
  },
  {
    path: '/',
    name: 'main',
    component: () => import('../views/A6Main.vue')
  },
  {
    path: '/:pathMatcher(.*)*',
    name: 'remaining',
    redirect: '/404'
  }
]

const router = createRouter({
  history: createWebHashHistory(),
  routes: clientRoutes
})

export const serverMenus = useStorage<Menu[]>('serverMenus', [])
const serverRoutes = useStorage<Route[]>('serverRoutes', [])
addServerRoutes(serverRoutes.value)

export function addServerRoutes(routeList: Route[]) {
  for (const r of routeList) {
    if (r.parentName) {
      router.addRoute(r.parentName, {
        path: r.path,
        component: () => import(r.component),
        name: r.name
      })
    }
  }
  serverRoutes.value = routeList
}

export function resetRoutes() {
  for (const r of clientRoutes) {
    router.addRoute(r)
  }
  serverRoutes.value = null
  serverMenus.value = null
}

export default router
```

本文件重要的函数及变量

* addServerRoutes 函数向路由表中添加由服务器提供的路由，路由分成两部分
  * clientRoutes 这是客户端固定的路由
  * serverRoutes 这是服务器变化的路由，存储于 localStorage
* resetRoutes 函数用来将路由重置为 clientRoutes 
  * vue-router@4 中的 addRoute 方法会【覆盖】同名路由，这是这种实现的关键
  * 因此，服务器返回的路由最好是 main 的子路由，这样重置时就会比较简单，用之前的 main 一覆盖就完事了
* serverMenus 变量记录服务器变化的菜单，存储于 localStorage



##### 登录组件

动态路由应当在登录时生成，A6Login.vue

```vue
<template>
  <div class="login">
    <a-form :label-col="{ span: 6 }" autocomplete="off">
      <a-form-item label="用户名" v-bind="validateInfos.username">
        <a-input v-model:value="dto.username" />
      </a-form-item>
      <a-form-item label="密码" v-bind="validateInfos.password">
        <a-input-password v-model:value="dto.password" />
      </a-form-item>
      <a-form-item :wrapper-col="{ offset: 6, span: 16 }">
        <a-button type="primary" @click="onClick">Submit</a-button>
      </a-form-item>      
    </a-form>
  </div>
</template>
<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { Form } from 'ant-design-vue'
import { useRouter } from 'vue-router'
import axios from '../api/request'
import { useRequest } from 'vue-request'
import { AxiosRespToken, LoginDto, AxiosRespMenuAndRoute } from '../model/Model8080'
import { resetRoutes, addServerRoutes, serverMenus } from '../router/a6router'
const dto = ref({username:'', password:''})
const rules = ref({
  username: [
    {required: true, message:'用户名必填'}
  ],
  password:[
    {required: true, message:'密码必填'}
  ]
})
const { validateInfos, validate } = Form.useForm(dto, rules)
const router = useRouter()
const { runAsync:login } = useRequest<AxiosRespToken, LoginDto[]>((dto)=> axios.post('/api/loginJwt', dto), {manual:true})
const { runAsync:menu } = useRequest<AxiosRespMenuAndRoute, string[]>((username)=> axios.get(`/api/menu/${username}`), {manual:true})
async function onClick() {
  try {
    await validate()
    const loginResp = await login(dto.value
    if(loginResp.data.code === 200) { // 登录成功
      const token = loginResp.data.data.token
      const menuResp = await menu(dto.value.username)
      const routeList = menuResp.data.data.routeList
      addServerRoutes(routeList)
      serverMenus.value = menuResp.data.data.menuTree
      router.push('/')
    })
  } catch (e) {
    console.error(e)
  }
}
onMounted(()=>{
  resetRoutes()
})
</script>
<style scoped>
.login{
  margin: 200px auto;
  width: 25%;
  padding: 20px;
  height: 180px;
  background-color: antiquewhite;
}
</style>
```

* 登录成功后去请求 `/api/menu/{username}`  获取该用户的菜单和路由
* router.push 方法用来以编程方式跳转至主页路由



##### 主页组件

A6Main.vue

```vue
<template>
  <div class="a6main">
    <a-layout>
      <a-layout-header>
      </a-layout-header>
      <a-layout>
        <a-layout-sider>
          <a-menu mode="inline" theme="dark">
            <template v-for="m1 of serverMenus">
              <a-sub-menu v-if="m1.children" :key="m1.id" :title="m1.title">
                <template #icon><a-icon :icon="m1.icon"></a-icon></template>
                <a-menu-item v-for="m2 of m1.children" :key="m2.id">
                  <template #icon><a-icon :icon="m2.icon"></a-icon></template>
                  <router-link v-if="m2.routePath" :to="m2.routePath">{{m2.title}}</router-link>
                  <span v-else>{{m2.title}}</span>
                </a-menu-item>
              </a-sub-menu>
              <a-menu-item v-else :key="m1.id">
                <template #icon><a-icon :icon="m1.icon"></a-icon></template>
                <router-link v-if="m1.routePath" :to="m1.routePath">{{m1.title}}</router-link>
                <span v-else>{{m1.title}}</span>
              </a-menu-item>
            </template>            
          </a-menu>
        </a-layout-sider>
        <a-layout-content>
          <router-view></router-view>
        </a-layout-content>
      </a-layout>
    </a-layout>
  </div>
</template>
<script setup lang="ts">
import AIcon from '../components/AIcon3' // jsx icon 组件
import { serverMenus } from '../router/a6router'
</script>
<style scoped>
.a6main {
  height: 100%;
  background-color: rgb(220, 225, 255);
  box-sizing: border-box;
}
.ant-layout-header {
  height: 50px;
  background-color:darkseagreen;
}

.ant-layout-sider {
  background-color:lightsalmon;
}

.ant-layout-content {
  background-color: aliceblue;
}

.ant-layout-footer {
  background-color:darkslateblue;
  height: 30px;
}

.ant-layout {
  height: 100%;
}

.ant-layout-has-sider {
  height: calc(100% - 50px);
}

</style>
```



#### token 使用

1. 获取用户信息，例如服务器端可以把用户名、该用户的路由、菜单信息都统一从 token 返回
2. 前端路由跳转依据，例如跳转前检查 token，如果不存在，表示未登录，就避免跳转至某些路由
3. 后端 api 访问依据，例如每次发请求携带 token，后端需要身份校验的 api 需要用到



### 3) pinia

需求：在组件 p1 里更新了数据，主页组件也同步更新显示

![image-20220930172635166](D:\2022.js\imgs\image-20220930172635166.png)

* storage 虽然可以实现多个组件的数据共享，但是需要【主动访问】才能获取更新后的数据
* 本例中由于没有涉及主页组件的 mounted 操作，因此并不会【主动】获取 storage 的数据 



#### 安装

```cmd
npm install pinia
```

在 main.ts 中引入

```typescript
import { createPinia } from 'pinia'

// ...
createApp(A6).use(antdv).use(router).use(createPinia()).mount('#app')
```



#### 定义Store

再新建 store 目录来管理共享数据，下面是 /src/store/UserInfo.ts

```typescript
import axios from '../api/request'
import { defineStore } from "pinia"
import { UserInfoDto } from '../model/Model8080'

export const useUserInfo = defineStore('userInfo', {
  state: () => {
    return { username: '', name: '', sex: '' }
  },
  actions: {
    async get(username: string) {
      const resp = await axios.get(`/api/info/${username}`)
      Object.assign(this, resp.data.data)
    },
    async update(dto: UserInfoDto) {
      await axios.post('/api/info', dto)
      Object.assign(this, dto)
    }
  }
})
```

* 定义了 useUserInfo 函数，用来获取共享数据，它可能用于多个组件

  * 命名习惯上，函数变量以 use 打头

* state 定义数据格式

* actions 定义操作数据的方法

  * get 方法用来获取用户信息

  * update 方法用来修改用户信息


* 由于 useRequest 必须放在 setup 函数内，这里简化起见，直接使用了 axios



获取用户信息

```vue
<template>
  <div class="a6main">
    <a-layout>
      <a-layout-header>
        <span>{{serverUsername}} 【{{userInfo.name}} - {{userInfo.sex}}】</span>
      </a-layout-header>
      <a-layout>
        <!-- ... -->
      </a-layout>
    </a-layout>
  </div>
</template>
<script setup lang="ts">
import { onMounted } from 'vue';
import AIcon from '../components/AIcon3' // jsx icon 组件
import { serverMenus, serverUsername } from '../router/a6router'
import { useUserInfo } from '../store/UserInfo'
const userInfo = useUserInfo()

onMounted(()=>{
  userInfo.get(serverUsername.value)
})
</script>
```



修改用户信息

```vue
<template>
  <div class="a6p1">
    <h3>修改用户信息</h3>
    <hr>
    <a-form>
      <a-form-item label="用户名">
        <a-input readonly v-model:value="dto.username"></a-input>
      </a-form-item>
      <a-form-item label="姓名" v-bind="validateInfos.name">
        <a-input v-model:value="dto.name"></a-input>
      </a-form-item>
      <a-form-item label="性别">
        <a-radio-group v-model:value="dto.sex">
          <a-radio-button value="男">男</a-radio-button>
          <a-radio-button value="女">女</a-radio-button>
        </a-radio-group>
      </a-form-item>
    </a-form>
    <a-button type="primary" @click="onClick">确定</a-button>
  </div>
</template>
<script setup lang="ts">
import { Form } from 'ant-design-vue'
import { onMounted, ref } from 'vue'
import { UserInfoDto } from '../model/Model8080'
import { useUserInfo } from '../store/UserInfo';
const dto = ref<UserInfoDto>({ username: '', name: '', sex: '' })
const userInfo = useUserInfo()
onMounted(()=>{
  Object.assign(dto.value, userInfo)
})
const rules = ref({
  name: [
    {required: true, message:'姓名必填'}
  ]
})
const { validateInfos, validate } = Form.useForm(dto, rules)
async function onClick() {
  try {
    await validate()
    await userInfo.update(dto.value)
  } catch (e) {
    console.error(e)
  }
}
</script>
```

* 不能直接把 userInfo 绑定到表单，需要 dto 中转一下
* userInfo.update 和 useInfo.get 返回的都是 Promise 对象，可以配合 await 一起用



### 后记

vite + vue3 + vue-router + ts 还没有太多成熟的项目范例，可以参考 [GitHub - sendya/preview-pro: Use pro-layout in vitejs. preview https://sendya.github.io/preview-pro/index.html](https://github.com/sendya/preview-pro)，它提供了基本的布局和样例代码

## 六 React

不学

## 七 jQuery









