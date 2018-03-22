* 1 Programming Code
	* Program, source code, code là gì ? 
		* Program: là chương trình được tạo ra từ các câu lệnh 
		* Mã nguồn (Source Code): là các dòng lệnh để đáp ứng với một sự kiện nào đó (Click trên command button chẳng hạn). Khi người sử dụng kích hoạt sự kiện đó thì các dòng lệnh được thực thi để trả lại kết quả cho sự kiện đó. (Ví dụ: hiển thị kết quả tìm được trong các TextBox v.v…). Bạn có thể xem/chỉnh sửa mã nguồn trong môi trường phát triển (IDE) phù hợp với mục đích công việc của mình. 
		* Code: là các mã lệnh
	* syntax là gì 
		* Syntax: là một tập hợp các luật lệ phải tuân theo khi lập trình
* 2 Statements
statement (câu lệnh) là gì ? 
- Câu lệnh: là những chỉ dẫn để máy tính thực thi
Giải thích câu lệnh sau:
a = b + 2;

- Gán cho biến a giá trị b+2
3 Expressions
expression (biểu thức) là gì ? khác gì với statements ? 
- biểu thức là tập hợp hợp lệ các kí tự, biến, toán tử để tạo ra 1 giá trị 
- câu lệnh thực hiện một hành động
Câu lệnh sau có bao nhiêu biểu thức
a = b * 2;

- có 2 biểu thức
4 Executing a Program
Chạy chương trình là gì ? 
- là quá trình mà máy tính thực thi các chỉ dẫn của chương trình
làm sao máy tính có thể hiểu đc câu lệnh a = b * 2 ? 
- cần phải có trình biên dịch từ các lệnh thành ngôn ngữ máy
interpreting là gì ? 
- dịch từng câu lệnh, có thể thay đổi là chạy chương trình ngay trong runtime
compiling là gì ? 
- dịch cả chương trình rồi mới bắt đầu chạy
JS là dạng interpreted hay là compilied ? 
- compiled
Sử dụng Developer Tools của Google Chrome hoặc Firefox để chạy chương trình sau:
a = 21;

b = a * 2;

console.log( b );
5 Operators
Hiểu về operators trong JS, có các loại chính là:
Assignment =
Math: +,-,*,/
Compound Assignment: +=, -, *, /=
Increment/decrement: ++, –
Object Property Access: .
Equality: =, ==, !=, !==
Comparison: <, >, <=, >=
Logical: &&, ||
6 Values & Types
JS có bao nhiêu kiểu data types? liệt kê từng kiểu và ví dụ 
- boolean: true & false 
- undefined. VD: var undefinedVariable; // undefined 
- number. VD: var num=1; 
- string. VD: "hello world"; 
- object. VD: var x = {firstName:"John", lastName:"Doe"}; 
- array. VD: var cars = ["Saab", "Volvo", "BMW"];
Thay xxx bằng operator để xác định kiểu của dữ liệu trong JS ?
a = "hello";
typeof a; // "string"

a = 42;
typeof a; // "number"

a = true;
typeof a; // "boolean"

a = null;
typeof a; // "object"

a = undefined;
typeof a; // "undefined"

a = { name: 'A' };
typeof a; // "object"
7 Objects
Đối tượng là gì ? 
- là một kiểu data dùng để chứa các value được đặt tên
Có những cách nào để truy xuất dữ liêu trong đối tượng 
- có 2 cách: objectName.propertyName hoặc objectName["propertyName"]
Cho đoạn code sau, chỉ rõ gía trị của ??? là gì
var o = {
  a: 'hello',
  b: 10,
  c: true
};

o.a; // "hello"
o.b; // 10
o.c; // true

o['a']; // "hello"
o['b']; // 10
o['c']; // true

var k = 'a';
o.k; // undefined
o[k]; // "hello"
8 Arrays
Arrays là gì ? làm sao tạo 1 array [1, 2, 3]; 
- là một loại biến đặc biệt, dùng để lưu trữ nhiều giá trị. VD: var arr = [1,2,3];
Cho đoạn code sau, chỉ rõ gía trị của ??? là gì
var a = [
  'hello',
  10,
  true
];

a[0]; // "hello"
a[1]; // 10
a[2]; // true
arr.length; // ???
typeof a; // object
Làm sao để phân biệt array và object? 
- sử dụng instanceof
9 Functions
Function là gì ? 
- là một khối những đoạn mã dùng để thực thi một nhiệm vụ nào đó
1 hàm gồm những thành phần nào ? 
function tên_hàm(tham số) { 
code để chạy 
}
Có những cách nào để định nghĩa functions ? so sánh? 
- function tên_hàm(tham số) { 
code để chạy 
} 
- var x = tên_hàm(tham số) { 
code để chạy 
}
Cho đoạn code sau, chỉ rõ gía trị của ??? là gì
function f() {
  return 10;
}

f.a = 'Hello';

typeof f; // "function"
typeof f(); // "number"
typeof f.a; // "string"
typeof f.b; // "undefined"
10 Built-In Type Methods
Cho đoạn code sau, chạy trên Console của Chrome, theo em length, toUpperCase, toFixed là gì ? 
- length: lấy độ dài của chuỗi, mảng,... 
- toUpperCase: viết hoa 
- toFixed: convert từ number sang string
var a = 'hello';
var b = 123;

a.length;
a.toUpperCase();
b.toFixed(4);
11 Comparing Values
Làm sao để so sánh giá trị ? 
- sử dụng các toán tử so sánh
Kết quả của phép so sánh luôn luôn là dạng dữ liệu gì ? 
- boolean
12 Coercion
Cho đoạn code sau, chạy trên Console của Chrome, em có nhận xét gì về giá trị của b và c? Từ đó rút ra coercion là gì ? 
- coercion là ép kiểu
var a = 10;
var b = Number(a);
var c = a * 1;

a;
b;
c;
13 Truthy & Falsy
Khi một giá trị không phải boolean cần chuyển sang boolean gì chuyện gì xảy ra? v/d dưới sẽ log ra như nào? 
- sẽ trả về true hoặc false tùy theo giá trị đó là gì 
- VD sẽ trả về 'a is truthy' vì a trả về giá trị true, còn '' trả về giá trị false
var a = 10;
var b = '';

if (a) {
   console.log('a is truthy');
}

if (b) {
   console.log('b is truthy');
}
14 Equality
Có bao nhiêu equality operators? (==, ===, !=, !==)
So sánh khác nhau giữa: == và === 
- == là bằng nhau về giá trị, có ép kiểu 
- === là phải giống nhau cả về kiểu dữ liệu, không được ép kiểu
15 Inequality
Có bao nhiêu inequality operators? (<, >, <=, >=)
16 Varibles
Biến (variables) là gì? 
- biến dùng để lưu các giá trị
17 Function Scopes
Scope là gì ? 
- là thứ quyết định độ truy cập của một biến
Trong JS có những loại scope nào ? 
- 2 loại: cục bộ và toàn cục
18 Conditionals
Các dạng điều kiện trong JS ra sao? (if, if…else, switch, (…) ? (…) : (…) 
- if: thực thi một khối code nếu thỏa mãn điều kiện trong if 
- else: thực thi một khối code nếu không thỏa mãn điều kiện trong if đó 
- else if: chỉ ra 1 điều kiện mới nếu điều kiện trước đó sai 
- switch: chỉ ra được nhiều khối code để thực thi
19 Strict mode
Strict mode là gì ? 
- là một chế độ dùng để thực thi một đoạn code nào đó với các quy định nghiêm ngặt hơn
20 Functions as Values
Set đoạn code sau, em có nhận xét gì ? 
- có thể định nghĩa funtion bằng các biến
var f = function() { }

var g = function abc() { }

console.log(f);

console.log(g);
21 Immediately Invoked Function Expressions (IIFEs)
Xem xét đoạn code sau, em có nhận xét gì ? 
- ta có thể viết function và dùng ngay lập tức
function a() {
   console.log(abc);
};

(function b() {
   console.log(abc);
})();
