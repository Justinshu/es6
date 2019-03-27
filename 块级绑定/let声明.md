# let声明

### 🎈解释

`let` 声明变量的方式与`var`基本一致，区别在于`let`声明的变量的作用域会被限制在当前代码块中（除此之外还有一些细微的差别），由于`let`声明的变量不会被提升到代码块的顶部，所以需要你手动将其提升到代码块的顶部（如果需要的话），以便让变量在整个代码块可用，下面是函数范例：

```
function getValue(condition){
    if (condition){
        let value = "blue";
        
        //其他代码
        
        return value；
        
    }else{
        //在这里拿不到value
        
        return value;
    }
    //在这里也拿不到value
}
```



如你所见，这种写法的`getValue`函数的方式更加接近其他类`C`语言，这种使用`let`而不是`var`声明变量的方式，变量不会被提升到函数内顶部，所以在`else`分支是拿不到`value`的而在`if`代码块之外更是拿不到`value`的，并且当`condition`的值为`false`时，变量`value`永远不会被声明和初始化

