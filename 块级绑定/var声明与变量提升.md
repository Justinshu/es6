# var声明与变量提升

*🎈理解*

```ES6
使用 var 声明的变量，有两种情况，一种是声明在任意函数的内部，在函数内会被当做声明在函数的顶部；另一种是不在任意函数内部声明的时候会被当做声明在全局作用域顶部；这就是所谓的变量提升（hoisting）
```

*🎈函数解释*

```
function getValue(condition){
	if	(condition){								
	     var value = "blue";
	   	 //	其他代码
		 return	value;			
	} else {
		 // value 在此处可访问，值为 undefined
		 return	null;				
	}
		 //	value 在此处可访问，值为	undefined 
}
```

