# var声明与变量提升

*🎈理解*

> 使用 var 声明的变量，有两种情况，一种是声明在任意函数的内部，在函数内会被当做声明在函数的顶部；另一种是不在任意函数内部声明的时候会被当做声明在全局作用域顶部；这就是所谓的变量提升（hoisting）

*🎈函数解释*

```变量提升
function getValue(condition){
	if (condition){								
	     var value = "blue";
	   	 // 其他代码
		 return value;			
	} else {
		 // value 在此处可访问，值为 undefined
		 return null;				
	}
		 // value 在此处可访问，值为 undefined 
}
```

上述函数，如果是我初学的时候会认为，只有在`condition`的值为`true`时才会创建变量`value`其实不是这样的，实际上，`value`无论如何都会被创建，`JS引擎`在后台对`getValue`函数进行了调整，结果如下函数：

```后台渲染
function getValue(condition){
	var value;
	// 实际上是在函数顶部声明了value，相当于声明变量提升了
    if (condition){
    	value = "blue";
    	//在这里初始化了value
    	// 其他代码
    	return value;
    }else{ 
    
        //这里也可以访问到value，因为没有被初始化，所以拿到的value是undefined
        return null;
    }
    // 在这里可以拿到声明的value，但是没有初始化值，所以是undefined
}
```

上述函数解释了var声明以及变量提升的函数式情况；未在任意函数内使用var进行声明变量的情况类似，只是变量被提升到了全局顶部；

*🎈总结*

**由于这种情况的出现会导致变量污染，所以在es6中出提出了块级作用域的定义，一方面是为了防止变量污染让变量的生命周期变得更加可控，另一方面是为了与其他语言的规范一致，利于开发者理解**



