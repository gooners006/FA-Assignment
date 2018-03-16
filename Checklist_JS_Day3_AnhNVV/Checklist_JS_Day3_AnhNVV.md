1 this & Object prototype
1.1 this
this là một trong những cơ chế gây rối nhất trong JS, theo em this là gì ?
  this là một con trỏ chỉ vào hàm nó nằm trong
Cách hiểu 1: this trỏ tới function f, đúng hay sai?
  Sai. this này đang trỏ tới một biến count global, không phải trong f()
Cách hiểu 2: this trỏ tới scope của function, đúng hay sai?
  Sai. this trong trường hợp này không trỏ đến được scope của hàm f()
So sánh các dạng gọi hàm như code:
  ```
  fn(); //function invocation. gọi hàm thông thường, this sẽ trỏ đến object global. (default binding)
  o.method(); //method invocation.gọi hàm dưới dạng 1 method của 1 object. this sẽ trỏ đến o. (implicit binding)
  fn.call();//  call and apply invocation. call() lấy tham số đầu tiên là 1 object để dùng cho this và gọi hàm đó với this trỏ đến object đó. (explicit binding)
  new fn();// constructor invocation. sẽ tạo 1 object mới và set nó làm object cho this. (new binding)
  ```
