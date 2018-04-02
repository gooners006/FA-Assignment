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
				const f7 = x => { y: x }// const f7 = x => ({ y: x })
				```
				
		* 1.3.4 True or false: arrow functions are anonymous ?
			* arrow function là biểu thức hàm vô danh
			* 
			```
			const myFunc = x => 4;
			console.log(myFunc.name);// in ra myFunc
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
			obj2.method();// lexical this sẽ nhớ được scope của cha của hàm nơi nó được dùng -> trỏ đến a trong obj2 -> in ra 10
			```
			
		* 1.3.6 Promise
			* Compare 2 Promise call below, what do you think ? If v is null or undefined what will happend ? How you handle that ?
			* nếu v null hoặc undefined thì chương trình sẽ báo lỗi. nếu dùng arrow function thì khi debug sẽ khó tìm được nơi xảy ra lỗi hơn là dùng hàm bình thường
				 
				```
				p.then(function (v) { return v.id });
				p.then(v => v.id);
				```
				br
		1.3.7 Exercise 01: rewrite all function below with arrow functions and try to avoid curly braces {} as much as possible
			* 
			```
			(() => {

				  var foo = (x) => {
				    var y = x * 2;

				    return function bar(z) {
				      if (z.length > 3) {
					return z.map( function baz(v){
					  if (v > 3) return v + y;
					  else return baz( v * 4 );
					} );
				      }
				      else {
					var obj = [];

					setTimeout( () => {
					  obj.length = 1;
					  obj[0] = this.w;
					}, 100 );

					return obj;
				      }
				    };
				  }

				  var p = foo( 2 );
				  var list1 = [1,3,4];
				  var list2 = list1.concat( 6 );

				  list1 = p.call( { w: 42 }, list1 );
				  list2 = p( list2 );

				  setTimeout( () => {
				    console.log( list1[0] === list2.reduce( (s,v) => {
				      return s + v;
				    }, 0 ) );
				  }, 200 );
				})();
			```
  	* 1.4 Classes
		* 1.4.1 Provide an example to create a new classed named Person which have 2 fields: id, name and 1 method: sayHello which print hello to the console
			
			```
			class Person{
				String id;
				String name;
				void sayHello() {
					console.log("Hello");
				}
			}
			```
			
	* 1.5 Block Scope
		* 1.4.1 Compare let and var
			* let cho phép khai báo một biến chỉ có giới hạn trong block, câu lệnh hoặc biểu thức
			* var cho phép định nghĩa một biến global hoặc local
		* 1.4.2 Closures scope, how do let work in closures, try example below
			
			```
			for (let i = 0; i < 3; i++) {
			  let btn = document.getElementById('btn' + i);
			  btn.addEventListener('click', () {
			    alert(i);
			  });
			}
			// mỗi let + for sẽ tại ra một vòng for mới -> tạo ra một biến i riêng biệt cho mỗi vòng for -> sẽ nhớ được biến i khi click
			```
			
		* 1.4.3 What is const ? Example ?
			* khai báo biến không được thay đổi giá trị bằng phép gán, các biến như array hay object vẫn có thể được modify
		* 1.4.4 Exercise: fix code below (anywhere) so the console.log will display true
			```
			const x = 2, fns = [];

			(function(){
			  const  x = 5;

			  for (let i=0; i<x; i++) {
			  fns.push(_ => i);
			  }
			})();

			console.log((x * 2) === fns[x*2]()); // must be true
			```


			
				

