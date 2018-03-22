* 1. this & Object prototype
    * this là một trong những cơ chế gây rối nhất trong JS, theo em this là gì ?
    	* this là một con trỏ, nơi nó chỉ vào phụ thuộc vào cách nó được gọi như thế nào
    * Cách hiểu 1: this trỏ tới function f, đúng hay sai?
    ```
    function f(num) {
      console.log("f: " + num);
      this.count++; // ghi lại gía trị đếm hàm f được gọi bao nhiêu lần
    }
    f.count = 0;

    f(1);
    f(2);
    f(3);
    f(4);
    f(5);

    // in ra số lần hàm f đc gọi: 5 lần
    console.log(f.count); // ???
    ```
      Sai. this này đang trỏ tới một biến count global, không phải trong f()
    * Cách hiểu 2: this trỏ tới scope của function, đúng hay sai?
    ```
    function f() {
      var a = 2;
      this.g();
    }

    function g() {
      console.log(this.a);
    }

    f();
    ```
      Sai. this trong trường hợp này không trỏ đến được scope của hàm f(), vẫn trỏ đến global

    * So sánh các dạng gọi hàm như code:
      ```
      fn(); //function invocation. gọi hàm thông thường, this sẽ trỏ đến object global. (default binding)
      o.method(); //method invocation.gọi hàm dưới dạng 1 method của 1 object. this sẽ trỏ đến o. (implicit binding)
      fn.call();//  call and apply invocation. call() lấy tham số đầu tiên là 1 object để dùng cho this và gọi hàm đó với this trỏ đến object đó. (explicit binding)
      new fn();// constructor invocation. sẽ tạo 1 object mới và set nó làm object cho this. (new binding)
      ```
      
      Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?
```
function f() {
  console.log(this.a);
}

var a = 2;

f(); // in ra 2 -> trỏ vào đối tượng global a=2.
```

Cho đoạn code sau, kết quả in ra là gì ?
```
function g() {
  "use strict";
  console.log(this.b);// báo lỗi vì lúc này this sẽ là undefined
}

var b = 2;

g(); // ??
```
Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?
```
function f() {
  console.log(this.a);
}

var o = {
  a: 2,
  f: f
};

o.f(); // in ra 2 -> this trỏ vào a trong object
```
Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?
```
function f() {
  console.log(this.a);
}

var o = {
  a: 2,
  f: f
};

var g = o.f;

g(); //  gọi g() như vậy thì là function invocation -> this trỏ tới global
```
Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?
```
function f() {
  console.log(this.a);
}

var o = {
  a: 2
};

var g = f.apply(o); // trả về giá trị của hàm f khi được gọi -> in ra 2 nhưng không gán được cho g, this trỏ vào o

f.call(o); // in ra 2, this trỏ vào o
g(); // vì g không phải là 1 hàm nên không thể gọi như một hàm => lỗi
```
Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?
```
function f(a) {
  this.a = a;
}

var g = new f(2); 
console.log(g.a); // in ra 2, this trỏ vào g
```
* Viết dụ kết hợp cả 4 cách gọi hàm để chỉ ra thứ tự khi gọi hàm ảnh hưởng đến this ra sao?
    * Từ đó theo em quy tác để xác định this là gì?
    * new (new binding) -> call or apply (explicit binding) ->  (implicit binding) ->  (default binding)
* 1.2 Objects
* Liệt kê lại 6 kiểu nguyên thuỷ trong JS ? liệt kê những kiểu Object có sẵn trong JS?
    * 6 kiểu nguyên thủy:
        * string
        * number
        * boolean
        * null
        * undefined
        * object
    * những kiểu Object có sẵn trong JS: 
        * String
        * Number
        * Boolean
        * Object
        * Function
        * Array
        * Date
        * RegExp
        * Error
* Có những cách nào để clone 1 object ?
    * var b = JSON.parse(JSON.Stringify(a))
* 1.3 Iteration
* Có những cách nào để duyệt các phần tử trong 1 array ? Viết code ví dụ
    * for
    * while 
    * forEach()
    * map()
    * for ... of, for ... in
* Có những cách nào để duyệt các thuộc tính trong 1 object? Viết code ví dụ
    * for...of, for ... in
* 1.4 Class Theory
* Nhớ lại OOP là gì ? các thuộc tính của OOP? 
    * Lập trình hướng đối tượng: là một kỹ thuật lập trình mô hình hóa đối tượng ngoài đời thành các đối tượng trong chương trình code, nhắm vào sự tương tác giữa các đối tượng
    * 4 thuộc tính: 
    	* Tính trừu tượng (abstraction): khả năng tập trung vào cốt lõi cần thiết của đối tượng mà chương trình đang làm việc lên, bỏ qua một số khía cạnh thông chi tiết. Tính trừu tượng còn thể hiện qua việc một đối tượng ban đầu có thể có nhiều đặc điểm chung cho nhiều đối tượng khác nhưng bản thân nó không có các biện pháp thi hành. 
			* VD: class con người ai cũng có method ăn, nói, đi, chạy,...
		* Tính đóng gói (encapsulation) và che giấu thông tin (information hiding): đảm bảo được thông tin của đối tượng, không cho bên ngoài có quyền thay đổi các thuộc tính hay phương thức của đối tượng. 
			* VD: có người qua nhà muốn mượn đồ nhưng mình không cho vào nhà mượn mà tự mình lấy đồ cho họ mượn
		* Tính đa hình (polymorphism): các đối tượng có phương thức giống nhau nhưng thực thi khác nhau.
			* VD: khi định nghĩa hai đối tượng "hinh_vuong" và "hinh_tron" thì có một phương thức chung là "chu_vi". Khi gọi phương thức này thì nếu đối tượng là "hinh_vuong" nó sẽ tính theo công thức khác với khi đối tượng là "hinh_tron".
		* Tính kế thừa (inheritance): Đặc tính này cho phép một đối tượng có thể có sẵn các đặc tính mà đối tượng khác đã có thông qua kế thừa. Điều này cho phép các đối tượng chia sẻ hay mở rộng các đặc tính sẵn có mà không phải tiến hành định nghĩa lại. 
			* VD: con có các gien giống cha như màu mắt, tóc,...
* So sánh "class" và "instance"
	* Class là một khung mô tả những thuộc tính và phương thức mình muốn thiết kế. Instance là vật thể được tạo ra từ class
* Constructor là gì?
	* hàm constructor được dùng để định nghĩa các thuộc tính và phương thức ban đầu cho đối tượng 
* 1.5 Prototypes
* Xem xét đoạn code sau, em có nhận xét gì ?
```
var o1 = {
  a: 2
}

var o2 = Object.create(o1);

console.log(o2.a); // in ra 2

o1.a = 10;
console.log(o2.a); // in ra 10
Nhận xét: o2 như là clone của o1, khi các key trong o1 thay đổi thì các giá trị trong o2 cũng thay đổi theo
```
* Tìm hiểu về Oject.prototype    
	* là một object được built-in  ở  [[Property chain]] (_ proto _), chứa các tiện ích thường xuyên được dùng như .toString() hay .hasOwnProperty(..)
 
