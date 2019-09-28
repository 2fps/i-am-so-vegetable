# this问题

## new 操作符

### new 操作符执行过程
1. 创建一个空对象，构造函数中的this指向这个空对象。
2. 这个新对象被执行 [[原型]] 连接。
3. 执行构造函数方法，属性和方法被添加到this引用的对象中。
4. 如果构造函数中没有返回其它对象，那么返回this，即创建的这个的新对象，否则，返回构造函数中返回的对象。

### 模拟实现 new
```js
function newCo(constructor, ...args) {
    // 1.
    let obj = {},
        res = null;
    // 2.
    obj.__proto__ = constructor.prototype;
    // 3.
    res = constructor.apply(obj, args);
    // 4.
    return typeof res === 'object' ? res : obj;
}
```

### this 校验
使用 es6 的箭头函数做构造函数时，new会报错。
```js
var Te = () => {}

var obj1 = new Te();    // Uncaught TypeError: Te is not a constructor
```

在 newCo 基础上，增加对 constructor 的检测。
```js
// ....
    if (!constructor.prototype) {
        throw new Error(constructor.name + ' is not a constructor');

        return;
    }

//....
```

## call、apply、bind 

三者都是用来改变this指向的。
区别是，
+ call和apply是在函数执行的时候改变this指向，而bind是返回一个已经改变this指向的新函数。
+ call和apply的区别是，call只支持参数单个传入，而apply不仅支持单个传，还支持数组的形式传参，所以apply用的稍微比call广些。
+ 我们可以通过 bind 实现柯里化。

### 模拟实现 call 方法
```js
// ES5 版
function callES5() {
    var ctx = arguments[0] || window,
        args = [];

    ctx.fn = this;

    for (var i = 1, len = arguments.length; i < len; i++) {
        args.push('arguments[' + i + ']');
    }
    var result = eval('ctx.fn(' + args +')');

    delete ctx.fn;

    return result;
}

// ES6 版
function callES6(ctx, ...args) {
    ctx = ctx || window;
    ctx.fn = this;

    let result = ctx.fn(...args);

    delete ctx.fn;

    return result;
}

```

### 模拟实现 apply 方法

```js
function applyES5() {
    var ctx = arguments[0] || window,
        argu = arguments[1],
        args = [];

    ctx.fn = this;

    for (var i = 0, len = argu.length; i < len; i++) {
        args.push('argu[' + i + ']');
    }
    var result =  eval('ctx.fn(' + args +')');

    return result;
}

function applyES6(ctx, args) {
    ctx = ctx || window;
    ctx.fn = this;
    args = args || [];

    let result = ctx.fn(...args);
    delete ctx.fn;

    return result;
}
```

### 模拟实现bind方法

``` js
Function.prototype.mybind = function() {
    var ctx = arguments[0] || window,
        args = Array.prototype.slice.call(arguments, 1),
        that = this;

    return function() {
        args = args.concat(Array.prototype.slice.call(arguments));
        that.apply(ctx, args);
    }
}
```