* 1 Scope & Closures
	* 1.1 Function Declartion vs Function Expressions
		* Xem xét đoạn code sau, em có nhận xét gì? 
			* cả console.log(b) và b() đều in ra kết quả giống nhau
```
function b() {
   console.log(b); // ??
}

console.log(b); // ??
b(); // ??
```
* Xem xét đoạn code sau, em có nhận xét gì? 
	* b() sẽ báo lỗi chưa được định nghĩa
var a = function b() {
   console.log(a, b); // ??
}

a(); //  ??
b(); // ??
1.2 What is Scope?
1.2.1 Nested Scope
Xem xét đoạn code sau, em có nhận xét gì ? 
- biến toàn cục dù khai báo sau vẫn có thể được hàm ở trước nó sử dụng
function foo(a) {
  console.log(a + b);
}

var b = 2;

foo(2); // 4
1.2.2 Errors
Xem xét đoạn code sau, em có nhận xét gì ? 
- b1 chưa được định nghĩa nên sẽ báo lỗi

function f1(a) {
  console.log(a + b1);
}

f1(2);
Xem xét đoạn code sau, em có nhận xét gì ? 
- sẽ thực thi như bình thường bởi vì b2 lúc này đã là biến toàn cục

function f2(a) {
  b2 = a;
  console.log(a + b2);
}

f2(2);
Nếu thêm strict mode vào f1 và f2 thì chuyện gì xảy ra ? 
- f2 sẽ báo lỗi vì không đúng cú pháp
1.3 Lexical Scope
Xem xét đoạn code sau, kết quả in ra là gì ? em có thể giải thích tại sao? có bao nhiều scope đc tạo ra ? Trong từng scope có những biến gì ? 
- in ra 2 4 12 
- khi gọi foo(2) -> gán a = 2 -> b = 4. gọi bar(b*3) -> gán c = b * 3 = 12 
- có 3 scope được tạo ra. Trong đó: 
- 1: scope toàn cục, chỉ chứa foo 
- 2: scope của foo, chứa a, b, bar 
- 3: scope của bar, chỉ chứa c
function foo(a) {

  var b = a * 2;

  function bar(c) {
    console.log(a, b, c);
  }

  bar(b * 3);
}

foo(2); // ?? ?? ??
1.4 Function vs Block Scope
Xử dụng IIFE để tạo function scope 
var a = 2; 
(function IIFE(){ 
var a = 3; 
console.log( a ); 
})(); 
console.log( a );
Trong JS có cách nào để tạo block scope? 
- function hoặc các condition
1.5 Hoisting
Xem xét đoạn code sau, em có nhận xét gì ? 
- vẫn sẽ in ra 2
a = 2;

var a;

console.log( a );
Xem xét đoạn code sau, em có nhận xét gì ? 
- trả về undefined vì lúc in ra thì biến a chưa được khai báo
console.log( a );

var a = 2;
Từ 2 ví dụ trên, theo em hoisting là gì ? 
- khai báo sẽ luôn được đưa lên đầu đoạn code, sau đó mới thực hiện các lệnh khác
Em có nhận xét gì về đoạn code sau: 
- sẽ trả về undefined bởi vì hoisting chỉ thực hiện trong scope đó, không ra ngoài
foo();

function foo() {
  console.log( a ); // undefined

  var a = 2;
}
1.6 Scope Closures
Xem xét đoạn code sau, em có nhận xét gì ?
function foo() {
  var a = 2;

  function bar() {
    console.log( a );
  }

  return bar;
}

var baz = foo();

baz(); // ???
Theo em closure là gì ?
2 Assignment
Tạo hàm range(a, b) trả về array các số tự nhiên liên tiếp từ a => b. Ví dụ: range(1, 4) = [1, 2, 3, 4] 
function range(first,last) { var arr=[]; for(i=first;i <=last;i++){ arr.push(i); } return arr; }
Tạo hàm sum(array) tính tổng các số trong array. V/d sum([1, 2, 3, 4]) = 10; 
function sum(arr) { var tong=0; for(i=0;i<arr.length;i++){ tong+=arr[i]; } return tong; }
Tính sum(range(1, 10)) 
function range(first,last) { var arr=[]; for(i=first;i <=last;i++){ arr.push(i); } return arr; } function sum(arr) { var tong=0; for(i=0;i<arr.length;i++){ tong+=arr[i]; } return tong; }
Sử dụng đệ quy để viết hàm isEven(n); isEven(10) => true; isEven(3) => false 
function isEven( n) { if (n == 0) { return true; } else if (n == 1) { return false; } else { return isOdd(n - 1); } } function isOdd( n) { if (n == 0) { return false; } else if (n == 1) { return true; } else { return isEven(n - 1); } }
Viết nốt body của hàm dưới, sao cho khi gọi sẽ hiện thị như comment 
fn(s);
function print(fn, s) {
  // TODO
}

print(console.log, 'a'); // hiển thị 'a'
print(console.log, 10); // hiện thị 10
Viết nốt body của hàm dưới, sao cho khi gọi sẽ hiện thị như comment
function add(a, b) {
  return a + b
}

function sub(a, b) {
  return a - b;
}

function op(fn, a, b) {
  // TODO
  return ...;
}

var opAdd = op(add);
opAdd(1, 2); // trả về 1 + 2

var opSub = op(sub);
opSub(3, 2); // trả về 3 - 1
Viết hàm repeat nhận 2 tham số, tham số đầu tiên là 1 hàm fn, tham số thứ 2 là n, và gọi hàm fn n lần. Ví dụ: 
for(i=0;i<n;i++){ console.log(fn()); }
function foo() {
   console.log('a');
}

function repeat(fn, n) {
// TODO
}

repeat(foo, 10); // hiện thị ra a 10 lần
