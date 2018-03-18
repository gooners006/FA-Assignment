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
console.log(g.a); // in ra 2
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
    * Em chưa hiểu lắm về phần này
* 1.3 Iteration
* Có những cách nào để duyệt các phần tử trong 1 array ? Viết code ví dụ
    * Sử dụng vòng lặp for để duyệt qua các index. VD: 
        * var myArray = [1, 2, 3];
        * for (var i = 0; i < myArray.length; i++) {
	        * console.log( myArray[i] );
        * }
        * ngoài ra còn có thêm một số cách nữa như forEach(), every(), some()
    * ES6 hỗ trợ for...of để duyệt qua giá trị của phần tử
* Có những cách nào để duyệt các thuộc tính trong 1 object? Viết code ví dụ
    * Cũng có thể dùng for...of
* 1.4 Class Theory
* Nhớ lại OOP là gì ? các thuộc tính của OOP? 
    * Lập trình hướng đối tượng: đối tượng chứa đựng các dữ liệu, trên các trường, thường được gọi là các thuộc tính; và mã nguồn, được tổ chức thành các phương thức. Phương thức giúp cho đối tượng có thể truy xuất và hiệu chỉnh các trường dữ liệu của đối tượng khác, mà đối tượng hiện tại có tương tác (đối tượng được hỗ trợ các phương thức "this" hoặc "self"). 
    * 4 thuộc tính: 
    	* Tính trừu tượng (abstraction): Đây là khả năng của chương trình bỏ qua hay không chú ý đến một số khía cạnh của thông tin mà nó đang trực tiếp làm việc lên, nghĩa là nó có khả năng tập trung vào những cốt lõi cần thiết. Mỗi đối tượng phục vụ như là một "động tử" có thể hoàn tất các công việc một cách nội bộ, báo cáo, thay đổi trạng thái của nó và liên lạc với các đối tượng khác mà không cần cho biết làm cách nào đối tượng tiến hành được các thao tác. Tính chất này thường được gọi là sự trừu tượng của dữ liệu. Tính trừu tượng còn thể hiện qua việc một đối tượng ban đầu có thể có một số đặc điểm chung cho nhiều đối tượng khác như là sự mở rộng của nó nhưng bản thân đối tượng ban đầu này có thể không có các biện pháp thi hành. Tính trừu tượng này thường được xác định trong khái niệm gọi là lớp trừu tượng hay lớp cơ sở trừu tượng.
		* Tính đóng gói (encapsulation) và che giấu thông tin (information hiding): Tính chất này không cho phép người sử dụng các đối tượng thay đổi trạng thái nội tại của một đối tượng. Chỉ có các phương thức nội tại của đối tượng cho phép thay đổi trạng thái của nó. Việc cho phép môi trường bên ngoài tác động lên các dữ liệu nội tại của một đối tượng theo cách nào là hoàn toàn tùy thuộc vào người viết mã. Đây là tính chất đảm bảo sự toàn vẹn của đối tượng.
		* Tính đa hình (polymorphism): Thể hiện thông qua việc gửi các thông điệp (message). Việc gửi các thông điệp này có thể so sánh như việc gọi các hàm bên trong của một đối tượng. Các phương thức dùng trả lời cho một thông điệp sẽ tùy theo đối tượng mà thông điệp đó được gửi tới sẽ có phản ứng khác nhau. Người lập trình có thể định nghĩa một đặc tính (chẳng hạn thông qua tên của các phương thức) cho một loạt các đối tượng gần nhau nhưng khi thi hành thì dùng cùng một tên gọi mà sự thi hành của mỗi đối tượng sẽ tự động xảy ra tương ứng theo đặc tính của từng đối tượng mà không bị nhầm lẫn. 
			* Ví dụ khi định nghĩa hai đối tượng "hinh_vuong" và "hinh_tron" thì có một phương thức chung là "chu_vi". Khi gọi phương thức này thì nếu đối tượng là "hinh_vuong" nó sẽ tính theo công thức khác với khi đối tượng là "hinh_tron".
		* Tính kế thừa (inheritance): Đặc tính này cho phép một đối tượng có thể có sẵn các đặc tính mà đối tượng khác đã có thông qua kế thừa. Điều này cho phép các đối tượng chia sẻ hay mở rộng các đặc tính sẵn có mà không phải tiến hành định nghĩa lại. Tuy nhiên, không phải ngôn ngữ định hướng đối tượng nào cũng có tính chất này.
* So sánh "class" và "instance"
	* Class chỉ là một bản thiết kế. Để có một object ta có thể tương tác thì ta cần khởi tạo từ một class, kết quả của việc khởi tạo này là một instance, ta có thể gọi trực tiếp các phương thức lên nó và truy cập các dữ liệu thuộc tính public.
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
	* là một object được built-in  ở  [[Property chain]] (_proto_), chứa các tiện ích thường xuyên được dùng như .toString() hay .hasOwnProperty(..)
 
