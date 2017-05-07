1. let 和 const 命令
let 用来声明变量，类似var，但是声明的变量只在let命令所在代码块内有效
 {
 	let a = 1;
 	var b = 1;
 }

 a //a is not defined
 b //1

 for (let i = 0; i < 10; i++) {console.log(i)};

 console.log(i); // i is not defined

 上面代码中 计数器i只在for循环体内有效，在循环外引用就会报错

 var a = [];

 for (var i = 0; i < 10; i++) {
 	a[i] = function() {
 		console.log(i);
 	}
 }

 a[6](); // 10;

 var a = [];

 for (let i = 0; i < 10; i++) {
 	a[i] = function() {
 		console.log(i);
 	};
 }

 a[6]();// 6;

另外，for循环还有一个特别之处，就是循环语句部分是一个父作用域，
而循环体内部是一个单独的子作用域。
 for (let i = 0; i < 3; i++) {
 	let i = 'abc';
 	console.log(i);
 }

 //abc
 //abc
 //abc

 上面代码输出了3次abc，这表明函数内部的变量i和外部的变量i是分离的

 不存在变量提升
 var 命令会发生'变量提升'现象，即变量可以在声明之前使用，但值为undefined，
 但是let纠正了这种现象，改变了语法，如果在声明变量之前使用就是报错

 //var 的情况
 console.log(foo); //undefined
 var foo = 2; // ===> 它先声明var foo; 然后foo = 2;

 //let的情况
 console.log(bar); //报错 ReferenceError: bar is not defined
 let bar = 2;