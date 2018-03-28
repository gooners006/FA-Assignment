* 1 ES 6
	* 1.1 Reference:
		* 1.1.1 ES6: http://blog.thefirehoseproject.com/posts/12-reasons-es6-future-javascript-web-development/
		* 1.1.2 ES6 Features
			* https://github.com/lukehoban/
			* http://es6-features.org/#Constants
		* 1.1.3 JS Engines: https://developer.telerik.com/featured/a-guide-to-javascript-engines-for-idiots/
		* 1.1.4 Transpilers: https://scotch.io/tutorials/javascript-transpilers-what-they-are-why-we-need-them
	* 1.2 History
		* 1.2.1 What's is ECMAScript ?
			* là một chuẩn, được tạo ra để chuẩn hóa JS
		* 1.2.2 What is JavaScript Engine ? Can you name a few JavaScript Engine used in some popular Browsers such as Chrome, Firefox, IE
			* là một chương trình hoặc 1 bộ thông dịch có nhiệm vụ thực thi các mã JS. 
			* một số engine thông dụng: 
				* SpiderMonkey của Firefox
				* V8 của Chrome
				* JavaScriptCore của Safari 
				* Chakra của Edge
		* 1.2.3 What is Future JavaScript ?
			* là các phiên bản mới nhất của JS như ES6 hay ES7
		* 1.2.4 What is problem you have if you want to use Future JavaScript in Present Browsers?
			* 
		* 1.2.5 What is transpiler ?
			* là một bộ dịch từ phiên bản mới về phiên bản cũ
		* 1.2.6 What is Babel ? Try Babel online here: https://babeljs.io/repl/
			* Babel là 1 transpiler
	* 1.3 Arrow Function
		* 1.3.1 Arrow Function syntax ?
			* ```(param1, param2, …, paramN) => { statements } 
				(param1, param2, …, paramN) => expression
				// equivalent to: => { return expression; } 

				// Parentheses are optional when there's only one parameter name:
				(singleParam) => { statements }
				singleParam => { statements }

				// The parameter list for a function with no parameters should be written with a pair of parentheses.
				() => { statements }
				```
				
		* 1.3.2 Compare arrow function syntax to ES5 function syntax ?
			* 2 cú pháp tương tự nhau, chỉ khác ở function và =>
		* 1.3.3 Arrow function variations, try them in Babel Repl, fix error if any
			* ```const f1 = () => 10;
				const f2 = x  => 3;
				const f3 = (...x) => 3;// ...
				const f4 = (x, y) => 3;
				const f5 = x => {
				  try {
				    1;
				  } catch (e) {}
				}
				const f6 = x => { return 10; }
				const f7 = x => { y: x }// ...
				```
				
		* 1.3.4 True or false: arrow functions are anonymous ?
			* arrow function là biểu thức hàm vô danh
			* 
			```
			const myFunc = x => 4;
			console.log(myFunc.name);
			```
			
		* 1.3.5 this
			* Evaluate the code below, can you explain what happens ?
			```
			var obj = {
			  a: 10,
			  method: function method() {
			    setTimeout(function () {
				console.log(this.a);
			    }, 200);
			  }
			}

			var obj2 = {
			  a: 10,
			  method: function method() {
			    setTimeout(() => {
				console.log(this.a);
			    }, 200);
			  }
			}

			obj.method(); // setTimeout được khai báo ở window -> this trỏ ra window -> undefined
			obj2.method();// ...
			```
			
		* 1.3.6 Promise
			* Compare 2 Promise call below, what do you think ? If v is null or undefined what will happend ? How you handle that ?
				* 
				```
				p.then(function (v) { return v.id });

				p.then(v => v.id);
				```

