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