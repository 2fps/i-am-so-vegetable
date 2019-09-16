# React事件
## 合成事件和原生事件
区别：


## 绑定事件的四种方式

### 1.
```js
class AA extends react.Component {
    constructor(props) {
        super(props)
        this.handleClick1 = this.handleClick1.bind(this)
    }
    //方式1：在构造函数中使用bind绑定this，官方推荐的绑定方式，也是性能最好的方式
    handleClick1() {
        console.log('this is:', this)
    }
    //方式2：在调用的时候使用bind绑定this
    handleClick2() {
        console.log('this is:', this)
    }
    //方式3：在调用的时候使用箭头函数绑定this
    // 方式2和方式3会有性能影响并且当方法作为属性传递给子组件的时候会引起重渲问题
    handleClick3() {
        console.log('this is:', this)
    }
    //方式4：使用属性初始化器语法绑定this，需要babel转义
    handleClick4 = () => {
        console.log('this is:', this)
    }
    render() {
        return (
            <div>
                <button onClick={this.handleClick1}>Click me</button>
                <button onClick={this.handleClick2.bind(this)}>Click me</button>
                <button onClick={() => this.handleClick3}>Click me</button>
                <button onClick={this.handleClick4}>Click me</button>
            </div>
        )
    }
}
```
