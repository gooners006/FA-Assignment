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
		* 1.4.2 What is keyword extends and super, provide an example that used both keyword ?
			* extends: dùng khi khai báo class để tạo một class là con của class khác
			* super: dùng để truy cập và gọi vào hàm của object cha
			* VD: 
			```
			class Rectangle {
			  constructor(height, width) {
			    this.name = 'Rectangle';
			    this.height = height;
			    this.width = width;
			  }
			  sayName() {
			    console.log('Hi, I am a ', this.name + '.');
			  }
			  get area() {
			    return this.height * this.width;
			  }
			  set area(value) {
			    this.height = this.width = Math.sqrt(value);
			  }
			}

			class Square extends Rectangle {
			  constructor(length) {
			    this.height; // ReferenceError, super needs to be called first!

			    // Here, it calls the parent class' constructor with lengths
			    // provided for the Rectangle's width and height
			    super(length, length);

			    // Note: In derived classes, super() must be called before you
			    // can use 'this'. Leaving this out will cause a reference error.
			    this.name = 'Square';
			  }
			}
			```
		* 1.4.3 Consider the following code, what will be printed out?
			```
			class Cha {
			  constructor() { this.id = 'a' }
			  method() {
			    console.log('Cha', this.id)
			  }
			}

			class Con extends Cha {
			  method() {
			    super.method();
			    console.log('Con', this.id)
			  }
			}
			// in ra Cha a và Con a
			```
		* 1.4.4 What is static keyword ?
			* dùng để định nghĩa một static method. Một static method được gọi trực tiếp trên class, không thể gọi trên instance của nó
			
	* 1.5 Block Scope
		* 1.5.1 Compare let and var
			* let cho phép khai báo một biến chỉ có giới hạn trong block, câu lệnh hoặc biểu thức
			* var cho phép định nghĩa một biến global hoặc local
		* 1.5.2 Closures scope, how do let work in closures, try example below
			
			```
			for (let i = 0; i < 3; i++) {
			  let btn = document.getElementById('btn' + i);
			  btn.addEventListener('click', () {
			    alert(i);
			  });
			}
			// mỗi let + for sẽ tại ra một vòng for mới -> tạo ra một biến i riêng biệt cho mỗi vòng for -> sẽ nhớ được biến i khi click
			```
			
		* 1.5.3 What is const ? Example ?
			* khai báo biến không được thay đổi giá trị bằng phép gán, các biến như array hay object vẫn có thể được modify
		* 1.5.4 Exercise: fix code below (anywhere) so the console.log will display true
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
	* 1.6 Default Values and the Gather/Spread Operator
		* 1.6.1 Default Values: how to define a functon with default value in ES5 ? And in ES6 ?
			* Trong ES5: 
				```
				function multiply(a, b) {
				  b = (typeof b !== 'undefined') ?  b : 1;
				  return a * b;
				}

				```
			* Trong ES6: 
				```
				function multiply(a, b = 1) {
				  return a * b;
				}
				```
		* 1.6.2 Lazy expression, evaluate the following code, how many times g have been called ?
			```
			function g() {
			  console.log('g');
			}

			function f(x = g()) {
			}

			f(1);
			f();
			f();
			// g được gọi 2 lần, f(1) không gọi g vì x=1. Nếu gán default value bằng 1 hàm thì khi gọi hàm chứa nó sẽ thực thi luôn hàm được gán làm giá trị mặc định
			```
		* 1.6.3 Evaluate the following code
			```
			var x = 1;
			function f(x = 2, fn = function() { return x }) {
			  console.log(fn());
			}

			f();
			// fn sẽ tìm biến x trong block scope của hàm f, lúc này x=2 -> x trong fn có giá trị 2 -> thực thi f sẽ in ra giá trị return của fn là 2
			```
		* 1.6.4 What's a variadic arguments?
			* nó cho phép function nhận nhiều arguments, gần giống như rest parameter
		* 1.6.5 What is arguments in a JavaScript function ?
			* object arguments(đối số) là một biến cục bộ, gần giống với 1 array,có ở trong mọi function trừ arrow function
		* 1.6.6 … operator can be used in 2 differents ways, see code below:
			```
			function f(...args) { // gather arguments
			}

			var x = [1, 2, 3];
			var y = [4, 5];
			var z = [0, ...x, ...y ]; // spread out
			```
		* 1.6.7 In which way the … operator is used in following code
			```
			function g(...arr) { // gather arguments
			}

			var a = [1, 2, 3];
			var b = [4, 5, 6];

			g(...a, ...b); // spread out
			```
		* 1.6.8 Exercise: fix the following code so console.log will print true
			```
			function f(...arr) { 
			arr[0].pop();
			arr[1].shift();
			return arr[0].concat(arr[1]);
			}
			function g() {
			  var a1 = [2, 4];
			  var a2 = [6, 8, 10, 12];

			  return f(a1,a2);
			}

			console.log(g().join("") === "281012"); // must print true
			```
	* 1.7 Destructuring
		* 1.7.1 What is destructuring ? Example ?
			*  là một cú pháp cho phép tách dữ liệu được lưu trữ bên trong Objects hoặc Arrays và gán chúng cho các biến riêng biệt.
			* VD: 
			```
			const person = { first: 'Foo', last: 'Bar' };
			const {first, last} = person;

			console.log(first); // Foo
			console.log(last);  // Bar

			//------------------------------------------
			// Aliases

			let characters = {a: 'a', b: 'b', c: 'c'};
			let {a: d, b: e, c: f} = characters;

			console.log(d, e, f); // a b c
			console.log(a);		// Uncaught ReferenceError: a is not defined
			```
		* 1.7.2 Can you use destructuring and default values together ? Provide example?
			* VD: 
			```
			let arr = ['a'];
			let [main, sub = 'b'] = arr;
			
			console.log(main);//a
			console.log(sub);//b
			```
		* 1.7.3 Dumping values: provide example that extract the 3rd element in an array and don't care about the 1st, 2nd element ? Provide example that swap 2 numbers ?
			* extract the 3rd element in an array and don't care about the 1st, 2nd element
			```
			let date = [10, 03, 2016]
			let [, , y] = date;
			```
			* swap 2 numbers
			```
			let date = [ 10, 03 ];
			let [day , month] = date;
			[day , month] = [month, day];
			```
		* 1.7.4 Nested Array Destructuring: in case we have an array like this [[1, 2], [3, 4], [5, 6]] use destructuring to extract the number 1 to variabled called a
			* VD: 
			```
			let arr=[[1, 2], [3, 4], [5, 6]]
			let [[a, b], [c, d], [e, f]]=arr
			```
		* 1.7.5 Object Destructuring: provide an example that use destructuring to extract property in an object ?
			* VD: 
			```
			let characters = {a: 'a', b: 'b', c: 'c'};
			let {a: d, b: e, c: f} = characters;

			console.log(d, e, f); // a b c
			```
		* 1.7.6 Nested Object Destructuring: in case we have an object like this { nested: { a: 10 } }, provide an example that use destructuring to extract value of a in inside nested object
			* VD:
			```
			let obj={ nested: { a: 10 } };
			let {nested: {a} }=obj;
			console.log(a);//10
			```
		* 1.7.7 Destructuring and Function Parameters: consider the array destructuring for parameters what will be printed out ?
		```
		function fn([ x, y ]) {
		  console.log(x, y);
		}

		fn([ 1, 2 ]); // 1 2
		fn([ 1 ]); // 1 undefined
		fn([ ]); // undefined undefined
		```
		* 1.7.8 Exercise: practice object destructuring, object constructuring
		```
		function ajax(url,cb) {
		  // fake ajax response:
		  cb({
		    foo: 2,
		    baz: [ 6, 8, 10 ],
		    bam: {
		      qux: 12
		    }
		  });
		}

		function check(data) {
		  console.log(
		    56 === (
		      data.foo +
		      data.bar +
		      data.baz[0] + data.baz[1] + data.baz[2] +
		      data.bam.qux +
		      data.bam.qam
		    )
		  );
		}

		var defaults = {
		  foo: 0,
		  bar: 4,
		  bam: {
		    qux: 0,
		    qam: 14
		  }
		};

		function response(/* TODO: object destructuring */) {

		  check({
		  /* TODO: object constructuring */
		  });

		}

		ajax("http://fun.tld",response);
		```
	* 1.8 Object Literal Extensions
		* 1.8.1 Concise properties: consider the following code what do you think ?
			```
			var x = 2, y = 3;
			var o1 = {
			  x: x,
			  y: y
			}

			var o2 = {
			  x,
			  y
			}
			console.log(o1); // ??
			console.log(o2); // ??
			// nếu thuộc tính có trùng key và value thì chỉ cần viết 1 lần
			```
		* 1.8.2 Concise Methods: consider the following code what do you think ?
			```
			var o1 = {
			  x: function() {
			    console.log('o1.x');
			  },
			  y: function() { }
			}

			o1.x();

			var o2 = {
			  x() {
			     console.log('o2.x');
			  },
			  y() {}
			}
			o2.x();
			// cũng có thể rút gọn khi viết phương thức giống như thuộc tính
			```
		* 1.8.3 ES5 Getter/Setter: consider the following code
			```
			var o = {
			  _id: 10,
			  get id() { return this._id++; },
			  set id(v) { this._id = v; }
			}

			o.id; // 10
			o.id = 100;
			o.id; // 100
			```
	* 1.9 Template Strings
		* 1.9.1 Template Strings: what is template strings ?
			* là kiểu string cho phép nhúng biểu thức vào nó.
		* 1.9.2 Consider this code below, rewrite it using ES6 template string
			```
			var name = 'That Duy';
			var chaoDuy = 'Hello ' + name + '!';

			console.log(chaoDuy);
			console.log(typeof chaoDuy);
			
			//rewrite
			var name = 'That Duy';
			var chaoDuy = `Hello ${name} !`;

			console.log(chaoDuy);//Hello That Duy !
			console.log(typeof chaoDuy);//string
			
			```
		* 1.9.3 Interpolated Expression: can we use function inside ${…} if yes provide an example
			```
			function upper(s) {
				return s.toUpperCase();
			}

			var who = "reader";

			var text =
			`A very ${upper( "warm" )} welcome
			to all of you ${upper( `${who}s` )}!`;

			console.log( text );
			// A very WARM welcome
			// to all of you READERS!
			```
		* 1.9.4 Tag Functions: consider the code below
			```
			function f(strings, ...values) {
			  console.log(strings);
			  console.log(values);
			}

			var s = 'Fresher Academy';
			f`Hello ${s}`; // in ra 2 mảng trong đó strings=['Hello', ""],values=['Fresher Academy'] 
			```
		* 1.9.5 Exercise
			```
			function upper(strings,...values) {
			  // TODO
			let [a,c,e,g]=strings;
			let [b,d,f]=values;
			return a+b.toUpperCase()+c+d.toUpperCase()+e+f.toUpperCase()+g;
			}

			var name = 'Nguyen Van A',
			  account = 'anv',
			  classname = 'Fresher Academy ES6';

			console.log(
			  upper`Hello ${name} (@${account}), welcome to the ${classname}!` ===
			  'Hello NGUYEN VAN A (@ANV), welcome to the FRESHER ACADEMY ES6!'
			);
			```
	* 1.10 Modules
		* 1.10.1 What is module pattern ?
			* là một design pattern, một module là 1 IIFE
		* 1.10.2 What is ES6 import/export ?
			* export: dùng để trích các function, object, kiểu nguyên thủy từ một module ra để chương trình sử dụng
			* import: nhận các dữ liệu được export từ module khác để sử dụng
			* VD: 
			trong module: 
			```
			// module "my-module.js"
				function cube(x) {
				  return x * x * x;
				}
				const foo = Math.PI + Math.SQRT2;
				var graph = {
				    options:{
					color:'white',
					thickness:'2px'
				    },
				    draw: function(){
					console.log('From graph draw function');
				    }
				}
				export { cube, foo, graph };
			```
			trong chương trình: 
			```
			import { cube, foo, graph } from 'my-module';
			graph.options = {
			    color:'blue',
			    thickness:'3px'
			}; 
			graph.draw();
			console.log(cube(3)); // 27
			console.log(foo);    // 4.555806215962888
			```
		* 1.10.3 What is export default ? How to import a exported default function ?
			* export default là một cách viết 1 module chỉ có 1 export, nếu dùng named export thì sẽ có nhiều export
			* có 2 cách viết default export:
				```
				function f(..) {
					// ..
				}

				export default f;
				//cách này sẽ export giá trị của biểu thức hàm f, ko phải identifier f, nghĩa là nó nhận một biểu thức. Nếu sau này trong module ta gán f cho 1 giá trị khác thì khi import sẽ lấy giá trị ban đầu, không lấy giá trị mới
				```
				```
				function f(..) {
					// ..
				}

				export { f as default };
				//dùng cách này thì khi thay đổi giá trị của f thì bên import cũng sẽ thay đổi giá trị theo
				```
			* cách để import một default export:
				```
				import f from "f";

				// or:
				import { default as f } from "f";
				```
		* 1.10.4 Circular Module Dependency: A imports B, B imports A, how does this work ?
			* Cách hoạt động:
				* module A được load trước, đầu tiên sẽ quét file và phân tích tất cả các export để ghi các binding khả dụng để import, sau đó sẽ xử lí phần "import .. from "B"",bắt đầu đi tìm B
				* khi engine load xong B, nó lại tiếp tục phân tích các export. Khi thấy "import .. from "A"" thì nó đã biết được API của A từ trước rồi nên engine sẽ verify các import là chuẩn. Bây giờ engine đã biết được API của B nên nó có thể xác nhận phần "import .. from "B"" đang đợi ở A là chuẩn
	* 1.11 Module Loaders
		* cung cấp khả năng load các module dynamically và kiểm soát các module đã được load bằng một thanh ghi module (module registry)
