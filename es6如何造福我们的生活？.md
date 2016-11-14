##ES6如何造福我们的生活？
###1.${}
之前，我们在拼接一段字符串的时候，往往需要使用好多个‘＋’，一个小例子。

	let Person = {
	  firstName:`Yue`,
	  lastName:`Zhang`,
	  sayName:function(){
	    return `My name is ` + this.firstName + ' ' + this.lastName;
	  }
	}
	
	console.log(Person.sayName());  //"My name is Yue Zhang"

有了${},就可以这样使用。
	
	let Person = {
	  firstName:`Yue`,
	  lastName:`Zhang`,
	  sayName:function(){
	    return `My name is ${this.firstName} ${this.lastName}`;  //这一行
	  }
	}
	
	console.log(Person.sayName());  //"My name is Yue Zhang"

${}内部的内容不会再被直接输出，而是被解析成该变量所对应的内容。

###2.定义函数的简化写法
还是上面的例子，Person对象中定义了一个成员函数，在ES6中可以简化为：
	
	let Person = {
	  firstName:`Yue`,
	  lastName:`Zhang`,
	  sayName(){            //这一行
	    return `My name is ${this.firstName} ${this.lastName}`;
	  }
	}
	
	console.log(Person.sayName());
少写了几个字，生活又美好了许多。

###3.=>
再来一个例子，现在有1，2，3，4，5这个简单的数组，把数组中的每个元素乘以2，通常会写成：
	
	let numbers = [1,2,3,4,5];
	let doubles = numbers.map(function(n){
	  return n * 2;
	})
	
	console.log(doubles); //[2, 4, 6, 8, 10]
用上了＝>,就会简化为：

	let numbers = [1,2,3,4,5];
	let doubles = numbers.map(n => n * 2);  //这一行
	
	console.log(doubles); //[2, 4, 6, 8, 10]
当然不仅仅是这样，再来一个例子
	
	let  Person = {
	  name:`ZhangYue`,
	  hobbies:[`reading`,`computer`,`serial`],
	  showHobbies(){
	    this.hobbies.forEach(function(hobby){
	      console.log(`${this.name} likes ${hobby}`); 
	    })
	  }
	}
	
	Person.showHobbies();
	//"JS Bin Output  likes reading"
	//"JS Bin Output  likes computer"
	//"JS Bin Output  likes computer"
这个当然是一种错误的写法，得不到我们想要的结果，因为在forEach函数中，this指代的不再当前对象。

	var  Person = {
	  name:`ZhangYue`,
	  hobbies:[`reading`,`computer`,`serial`],
	  showHobbies(){
	    this.hobbies.forEach( hobby => {
	      console.log(`${this.name} likes ${hobby}`);
	    });
	  }
	}
	Person.showHobbies();
	//"ZhangYue likes reading"
	//"ZhangYue likes computer"
	//"ZhangYue likes computer"
在使用=>的时候，this指代的始终都是当前对象。

###4. ...args（剩余参数）
我们所知道的是arguments是函数的参数对象。一个例子来使用这个arguments。求所有参数的和。

	let sum = function() {
	  return Array.prototype.reduce.call(arguments,(prev,curr) => {
	    return prev + curr;
	  });
	}
	
	console.log( sum(1,2,3,4) ); //10
再看看...args是什么。
	
	let sum = function(...args) {
	  console.log(args);
	}
	
	sum(1,2,3,4); //[1, 2, 3, 4]
由此可以看出，...args是由参数组成的数组。

	let sum = function(a,...args) {
	  console.log(a,args);
	}
	
	sum(1,2,3,4); 
	//1
	//[2, 3, 4]
此时，...args就是除了参数a之外剩余的参数。如果使用...args,该如何求参数之和呢。

	let sum = function(...args) {
	  return args.reduce((prev,curr) => {
	    return prev + curr;
	  })
	}
	
	console.log(sum(1,2,3,4));

比直接使用arguments对象又方便了许多，当然不止这样。
	
	let mult = function(mul,...args) {
	  return args.map((n) => {
	    return mul * n;
	  })
	}
	
	console.log(mult(1,2,3,4)); //[2, 3, 4]

使用args很方便实现了第一个参数和剩余的参数分别相乘，并返回了一个新的数组。
求一个数组中最大的值，我们常常这样使用。

	let max = Math.max(1,2,3,5,9,3);
	
	console.log(max);
但是，往往会出现这样的情况，知道一个数组，直接把数组作为参数放进去？

	let arr = [1,4,7,9,5];
	let max = Math.max(arr);
	
	console.log(max); //NaN
这样显然不行。需要使用apply函数才能直接使用数组作为参数。
	
	let arr = [1,4,7,9,5];
	let max =  Math.max.apply(null,arr);
	
	console.log(max); //9
使用...args,又是如何实现的呢？

	let arr = [1,4,7,9,5];
	let max =  Math.max(...arr);
	
	console.log(max);
也不需要使用apply，又方便了一些。最后再来一个例子，通常我们使用concat来实现数组的拼接，这里使用...args同样是很方便。

	let arr = [1,4,7,9,5];
	let new_arr =  [1,2,4,5,...arr]; 
	
	console.log(new_arr);  //[1, 2, 4, 5, 1, 4, 7, 9, 5]
同理，不仅可以拼接在开头结尾，它可以在新数组的任意位置。
	
	let arr = [1,4,7,9,5];
	let new_arr =  [1,2,...arr,4,5]; 
	
	console.log(new_arr); //[1, 2, 1, 4, 7, 9, 5, 4, 5]

###5.Destructuring(解构)
获取对象的部分属性或方法，以及获取数组的部分元素。

	let Person = {
	  name:'ZhangYue',
	  age:18,
	  location:'NanJing'
	}
	let {name:myname,age:myage} = Person;
	console.log(myname,myage);
	
	
	let numbers = [1,2,3,4,5];
	let [first,second,...rest] = numbers; //结合之前的剩余参数
	console.log(first,second,rest);
###6.gulp_babel
1)在项目中安装gulp
2)安装gulp-babel、babel-preset-es2015
3)gulpfile.js
	
	const gulp = require('gulp');
	const babel = require('gulp-babel');
	
	gulp.task('es6', () => {
		return gulp.src('src/app.js')
			.pipe(babel({
				presets: ['es2015']
			}))
			.pipe(gulp.dest('build'));
	});
	
	gulp.task('default',['es6'], () => {
		gulp.watch('src/app.js',['es6'])
	});
4)在src/app.js（被编译的es6）
	
	let name = 'Zhangyue';

	let add = (a,b) => a + b;
	
	let sum = (...numbers) => {
		return numbers.reduce((prev,curr) => {
			return prev + curr;
		})
	}
5)运行gulp
6)编译成js的严格模式
	
	'use strict';

	var name = 'Zhangyue';
	
	var add = function add(a, b) {
		return a + b;
	};
	
	var sum = function sum() {
		for (var _len = arguments.length, numbers = Array(_len), _key = 0; _key < _len; _key++) {
			numbers[_key] = arguments[_key];
		}
	
		return numbers.reduce(function (prev, curr) {
			return prev + curr;
		});
	};