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