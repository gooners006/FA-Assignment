1. this & Object prototype
    1. this
    this là một trong những cơ chế gây rối nhất trong JS, theo em this là gì ?
      this là một con trỏ chỉ vào hàm nó nằm trong
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
      Sai. this trong trường hợp này không trỏ đến được scope của hàm f()

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
  console.log(this.b);// báo lỗi vì lúc này this không trỏ được ra nơi biến b được khai báo
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

g(); //  g tham chiếu đến f() chứ không đến o và gọi hàm g() thì sẽ tìm biến a ở global scope -> undefined
```
Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?
```
function f() {
  console.log(this.a);
}

var o = {
  a: 2
};

var g = f.apply(o); // trả về giá trị của hàm f khi được gọi -> in ra 2 nhưng không gán được cho g

f.call(o); // in ra 2
g(); // vì g không phải là 1 hàm nên không thể gọi như một hàm => lỗi
```
Cho đoạn code sau, kết quả in ra là gì ? hàm được gọi theo cách nào? theo em trong trường hợp này this trỏ vào đối tượng nào ?
```
function f(a) {
  this.a = a;
}

var g = new f(2);
console.log(g.a); // ???
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
