# 第5节：setTimeout

一个关于setTimeout与循环闭包的思考题。

> 利用闭包，修改下面的代码，让循环输出的结果依次为1， 2，3，4，5
>
> ```
> for(var i = 1; i <= 5; i++) {
>  setTimeout(function(){
>      console.log(i);
>  });
> }
> ```
>

  上面例子 在控制台打印出来的结果是 5 个 6，setTmeout是在程序执行完成之后才开始执行的，也就是在for循环执行的时候程序并没有立即开始执行setTimeout语句体的内容，而是每次执行的时候都将setTimeout添加到了js事件队列中，等for循环执行完，也就是js程序空闲的时候，才开始执行，而那个时候 i 的值跳出循环后变成了6，所以后面程序执行了5次 setTimeout 输出了5次 '6'。



如果我们想要让输出的结果依次执行，我们就必须借助闭包的特性，每次循环时，都将i值保存再一个闭包中，当setTimeout 中定义的操作执行时，则访问对应闭包中保存的i值即可。(利用闭包保存每次循环时i的值，执行setTimeout 时访问闭包中的i)。

```
for(var i = 1; i <= 5; i++){
    (function(i){
        setTimeout(function(){
         	console.log(i);
        })
    })(i)
}
```

也可以在setTimeout的第一个参数处利用闭包。

```
for(var i = 1; i <= 5; i++) {
    setTimeout(function(i){
        return function() {
            console.log(i);
        }
    })
}
```

