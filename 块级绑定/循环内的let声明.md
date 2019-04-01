# 循环内的let声明

`let`声明通过有效模仿上例中`IIFE`的作用而简化了循环。在每次迭代中，都会创建一个新的 同名变量并对其进行初始化。这意味着你可以完全省略`IIFE`而获得预期的结果，就像这样：

```
var funcs = [];

for (let i = 0; i < 10; i++){
    funcs.push(function(){
        console.log(i);
    });
}

funcs.forEach(founction(func){
    func();    //从 0 到 9 依次输出
})
```

与使用`var`声明以及`IIFE`相比，这里代码能达到相同效果，但无疑更加简洁。在循环中`let`声明每次都创建了一个新的`i`变量，因此在循环内部创建的函数获得了各自的`i`副本，而每个`i`副本的值都在每次循环迭代声明变量的时候被确定了。这种方式在`for-in`和`for-of`循环中同样适用，如下所示：

```
var funcs = [];
    object = {
        a:true,
        b:true,
        c:true
    };

for (let key in object){
    funcs.push(function(){
     console.log(key); 
    });
}

funcs.forEach(function(func){
    func();     //依次输出 “a” 、“b”、“c”
});
```

本例中的`for-in`循环体现出了与`for`循环相同的行为。每次循环，一个新的`key`变量绑 定就被创建，因此每个函数都能够拥有它自身的`key`变量副本，结果每个函数都输出了一个不同的值。而如果使用`var`来声明`key`，则所有函数都只会输出`"c"`。

> 需要重点了解的是：`let`声明在循环内部的行为是在规范中特别定义的，而与不提升变量声明的特征没有必然联系。事实上，在早期`let`的实现中并没有这种行为，它是后来才添加的。

