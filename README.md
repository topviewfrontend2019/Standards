# TopView大前端代码规范

---
# 代码风格

## 文件
- `js`文件使用`utf-8`编码

## 代码结构
### 缩进
- 缩进使用`2`个空格作为一个缩进层级
- `switch`下的`case`和`default`语句需要增加一个缩进层级
``` javascript
// good example
switch (variable) {

    case '1':
        // do...
        break;

    case '2':
        // do...
        break;

    default:
        // do...

}

// bad example
switch (variable) {

case '1':
    // do...
    break;

case '2':
    // do...
    break;

default:
    // do...

}
```

### 空格问题
- 二元运算符两侧要有一个空格，一元运算符与操作对象之间不需要有空格
``` javascript
var a = !arr.length;// 有空格
a++;                // 无空格
a = b + c;
```
- 用作代码块起始的左花括号 `{ `前必须有一个空格。

``` javascript
// good
if (condition) {
}

while (condition) {
}

function funcName() {
}

// bad
if (condition){
}

while (condition){
}

function funcName(){
}
```

- `if / else / for / while / function / switch / do / try / catch / finally` 关键字后，必须有一个空格。
``` javascript
// good example
if (condition) {
}

while (condition) {
}

(function () {
})();

// bad example
if(condition) {
}

while(condition) {
}

(function() {
})();
```
- 在对象创建时，属性中的 `: `之后必须有空格，`:` 之前不允许有空格。
``` javascript
// good example
var obj = {
    a: 1,
    b: 2,
    c: 3
};

// bad example
var obj = {
    a : 1,
    b:2,
    c :3
};
```
- 函数声明、具名函数表达式、函数调用中，函数名和 `(` 之间不允许有空格。
``` javascript
// good example
function funcName() {
}

var funcName = function funcName() {
};

funcName();

// bad example
function funcName () {
}

var funcName = function funcName () {
};

funcName ();
```

- `,` 和` ;` 前不允许有空格。
``` javascript
// good example
callFunc(a, b);

// bad example
callFunc(a , b) ;
```

- 在函数调用、函数声明、括号表达式、属性访问、`if / for / while / switch / catch` 等语句中，`()`和 `[]` 内紧贴括号部分不允许有空格。
``` javascript
// good example

callFunc(param1, param2, param3);

save(this.list[this.indexes[i]]);

needIncream && (variable += increament);

if (num > list.length) {
}

while (len--) {
}


// bad example

callFunc( param1, param2, param3 );

save( this.list[ this.indexes[ i ] ] );

needIncreament && ( variable += increament );

if ( num > list.length ) {
}

while ( len-- ) {
}
```

- 单行声明的数组与对象，如果包含元素，`{}` 和 `[]` 内紧贴括号部分不允许包含空格。
``` javascript
// good example
var arr1 = [];
var arr2 = [1, 2, 3];
var obj1 = {};
var obj2 = {name: 'obj'};
var obj3 = {
    name: 'obj',
    age: 20,
    sex: 1
};

// bad example
var arr1 = [ ];
var arr2 = [ 1, 2, 3 ];
var obj1 = { };
var obj2 = { name: 'obj' };
var obj3 = {name: 'obj', age: 20, sex: 1};
```

- 行尾不得有多余的空格。

### 换行
- 每个独立语句结束后必须换行。运算符处换行时，运算符必须在新行的行首。
- 每行不得超过 `120` 个字符。
- 运算符处换行时，运算符必须在新行的行首。

``` javascript
// good example
if (user.isAuthenticated()
    && user.isInRole('admin')
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')
) {
    // Code
}

var result = number1 + number2 + number3
    + number4 + number5;


// bad example
if (user.isAuthenticated() &&
    user.isInRole('admin') &&
    user.hasAuthority('add-admin') ||
    user.hasAuthority('delete-admin')) {
    // Code
}

var result = number1 + number2 + number3 +
    number4 + number5;
```

- 在函数声明、函数表达式、函数调用、对象创建、数组创建、`for` 语句等场景中，不允许在 `,` 或 `;` 前换行。
``` javascript
// good
var obj = {
    a: 1,
    b: 2,
    c: 3
};

foo(
    aVeryVeryLongArgument,
    anotherVeryLongArgument,
    callback
);


// bad
var obj = {
    a: 1
    , b: 2
    , c: 3
};

foo(
    aVeryVeryLongArgument
    , anotherVeryLongArgument
    , callback
);
```

- 不同行为或逻辑的语句集，使用空行隔开，更易阅读。
``` javascript
// 仅为按逻辑换行的示例，不代表setStyle的最优实现
function setStyle(element, property, value) {
    if (element == null) {
        return;
    }

    element.style[property] = value;
}
```

- 在语句的行长度超过 120 时，根据逻辑条件合理缩进。
``` javascript
// 较复杂的逻辑条件组合，将每个条件独立一行，逻辑运算符放置在行首进行分隔，或将部分逻辑按逻辑组合进行分隔。
// 建议最终将右括号 ) 与左大括号 { 放在独立一行，保证与 if 内语句块能容易视觉辨识。
if (user.isAuthenticated()
    && user.isInRole('admin')
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')
) {
    // Code
}

// 按一定长度截断字符串，并使用 + 运算符进行连接。
// 分隔字符串尽量按语义进行，如不要在一个完整的名词中间断开。
// 特别的，对于HTML片段的拼接，通过缩进，保持和HTML相同的结构。
var html = '' // 此处用一个空字符串，以便整个HTML片段都在新行严格对齐
    + '<article>'
    +     '<h1>Title here</h1>'
    +     '<p>This is a paragraph</p>'
    +     '<footer>Complete</footer>'
    + '</article>';

// 也可使用数组来进行拼接，相对 + 更容易调整缩进。
var html = [
    '<article>',
        '<h1>Title here</h1>',
        '<p>This is a paragraph</p>',
        '<footer>Complete</footer>',
    '</article>'
];
html = html.join('');

// 当参数过多时，将每个参数独立写在一行上，并将结束的右括号 ) 独立一行。
// 所有参数必须增加一个缩进。
foo(
    aVeryVeryLongArgument,
    anotherVeryLongArgument,
    callback
);

// 也可以按逻辑对参数进行组合。
// 最经典的是baidu.format函数，调用时将参数分为“模板”和“数据”两块
baidu.format(
    dateFormatTemplate,
    year, month, date, hour, minute, second
);

// 当函数调用时，如果有一个或以上参数跨越多行，应当每一个参数独立一行。
// 这通常出现在匿名函数或者对象初始化等作为参数时，如setTimeout函数等。
setTimeout(
    function () {
        alert('hello');
    },
    200
);

order.data.read(
    'id=' + me.model.id,
    function (data) {
        me.attchToModel(data.result);
        callback();
    },
    300
);

// 链式调用较长时采用缩进进行调整。
$('#items')
    .find('.selected')
    .highlight()
    .end();

// 三元运算符由3部分组成，因此其换行应当根据每个部分的长度不同，形成不同的情况。
var result = thisIsAVeryVeryLongCondition
    ? resultA : resultB;

var result = condition
    ? thisIsAVeryVeryLongResult
    : resultB;

// 数组和对象初始化的混用，严格按照每个对象的 { 和结束 } 在独立一行的风格书写。
var array = [
    {
        // ...
    },
    {
        // ...
    }
];
```

- 对于 `if...else...、try...catch...finally` 等语句，推荐使用在 `}` 号后添加一个换行的风格，使代码层次结构更清晰，阅读性更好。
``` javascript
// good example
if (condition) {
    // ...
} else {
    // ...
}

try {
    // ...
} catch (ex) {
    // ...
}


// bad example
if (condition) {
    // some statements;
}
else {
    // some statements;
}
try {
    // some statements;
}
catch (ex) {
    // some statements;
}
```

### 语句
-  在 `if / else / for / do / while` 语句中，即使只有一行，也不得省略块`{...}`。
``` javascript
// good example
if (condition) {
    callFunc();
}

// bad example
if (condition) callFunc();
if (condition)
    callFunc();
```

- 函数定义结束不允许添加分号。
``` javascript
// good example
function funcName() {
}

// bad example
function funcName() {
};

// 如果是函数表达式，分号是不允许省略的。
var funcName = function () {
};
```

- `IIFE` 必须在函数表达式外添加 `(`，非 `IIFE` 不得在函数表达式外添加 `(`。
``` javascript
// good example
var task = (function () {
   // Code
   return result;
})();

var func = function () {
};


// bad example
var task = function () {
    // Code
    return result;
}();

var func = (function () {
});
```

## 命名

- `函数` `变量` `参数` `类的 方法/属性`使用 `Camel`命名法。
``` javascript
// good example
var loadingModules = {};
function stringFormat(source) {
    // ...
}
function hear(theBells) {
    // ...
}
function TextNode(value, engine) {
    this.myValue = value;
    this.myEngine = engine;
}

TextNode.prototype.clone = function () {
    return this;
};

// bad example
var loadingmoduleS = {};
function stringformaT(source) {
    // ...
}
function hear(thebellS) {
    // ...
}
function TextNode(value, engine) {
    this.myvaluE = value;
    this.myenginE = engine;
}
```

- 常量使用 `全部字母大写，单词间下划线分隔` 的命名方式。
``` javascript
// good example
var HTML_ENTITY = {};
const HTML_ENTITY = {};

// bad example
var html_entity = {};
```

-  `类` 使用 `Pascal`命名法。
``` javascript
function TextNode(options) {
    // ...
}
```

- `boolean` 类型的变量使用 `is` 或 `has` 开头。
``` javascript
// boolean variable
var isReady = false;
var hasMoreCommands = false;
```

## 注释
### 单行注释
- `//` 后跟一个空格
``` javascript
// good example
// haha

// bad example
//heihei
//  hehe
```

- 若注释占整行，则注释缩进与下一行被注释说明的代码一致。
``` javascript
// good example
    var a = 0;
    // haha
    var haha = 1;

// bad example
    var a = 0;
// heihei
    var heihei = 2;
```

### 多行注释
- 避免使用 `/*...*/` 这样的多行注释。有多行注释内容时，使用多个单行注释。
``` javascript
// good example
// hallo
// i am Aymax

// bad example
/* hallo
   i am Baymax */
```

### 函数注释
- 类型定义以 `{` 开始, 以 `}` 结束，例 ```string```、```number```
- 建议使用插件 - DocBlockr
``` javascript
// good example
/**
 * @function 取得数组中的最小值
 * @param  {Array}
 * @return {number}
 */
function getMin(arr) {
    return Math.min.apply(Math,arr);
}
```

### 文件注释
``` javascript
// good example
/**
 * @author: Aymax
 * @date: 1921.01.01
 * @contact: 88888888@qq.com
 * @description: haha
 */
```

### 特殊注释
``` javascript
// good example
// TODO: 有功能待实现。此时需要对将要实现的功能进行简单说明。
// FIXME: 该处代码运行没问题，但可能由于时间赶或者其他原因，需要优化。
// HACK: 为修正某些问题而写的不太好或者使用了某些诡异手段的代码。
// XXX: 存在一些坑要特别说明的，避免后人又踩
```
