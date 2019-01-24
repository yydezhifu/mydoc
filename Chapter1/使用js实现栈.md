# 第6节：使用js实现栈

> 首先了解一下什么是栈，栈是一个后进先出的一种数据结构，执行起来效率比较高。
>
> 对于栈主要包括一些方法，出栈pop()，弹出栈顶元素，并删除该元素；入栈push()，向栈中添加元素，栈长度增加；读取栈顶元素peek()
>
> 使用js的构造模式创建栈类，原型进行共享主要方法

#### 代码实现如下 ####

```
(function(window){
    function Stack() {
        this.dataStore = [];
    }
    
    Stack.prototype = {
    	constructor: Stack,
        pop: function() {
            return this.dataStore.pop(); // 出栈，返回栈顶元素，元素个数减一
        },
        push: function(value) {
            return this.dataStore.push(value); // 入栈，在栈顶添加元素，元素个数加一
        },
        peek: function() {
            return this.dataStore[this.dataStore.length - 1];
        },
        isEmpty: function() {
            return this.dataStore.length === 0;
        },
        clear: function() {
            return this.dataStore = [];
        },
        size: function() {
            return this.dataStore.length;
        }
    }
    
    window.Stack = Stack;
    
})(window)
```

