* 1 Async
* 1.1 Sync vs Async
  * Sync code (code đồng bộ) là gì ?
  	* là xử lý đồng bộ, chương trình sẽ chạy theo từng bước và chỉ khi nào bước 1 thực hiện xong thì mới nhảy sang bước 2, khi nào chương trình này chạy xong mới nhảy qua chương trình khác.
  * Async code (code bất đồng bộ) là gì ?
  	* là chương trình có thể nhảy đi bỏ qua một bước nào đó.
  * Theo em JavaScript là ngôn ngữ đồng bộ hay bất đồng bộ
  	* ngôn ngữ lập trình không đồng bộ. Đó là do:
    * JS là ngôn ngữ thực hiện nhiều bên client. Khi thực hiện thì client cần gửi request lên server, và trong lúc chờ server trả lời thì sẽ gửi tiếp những request khác để tiết kiệm thời gian. Đó là xử lí bất đồng bộ.
  * Cách hoạt động: 
    * Trong JS, hàm không bao giờ được gọi trực tiếp, mà phải qua message.
    * JS sử dụng 1 messages queue để lưu trữ các message hay event được gửi đến. Một event-loop điều phối message lần lượt đến một call-stack, ở đây các hàm tương ứng của các message được xếp chồng lên nhau thành các frame(các argument và variable của hàm) để thực thi
    * call-stack sẽ giữ frame của hàm ban đầu được gọi ở trên cùng
    * khi một message mới tham gia vào hàng chờ(queue), nó sẽ đợi cho đến khi call-stack không còn frame nào của message trước nữa, và khi đó thì event-loop sẽ bỏ message trước khỏi hàng chờ và thêm những frame của message hiện tại vào call-stack
    * message đó sẽ lại đợi cho đến khi call-stack hết những frame của chính nó(tức là khi đã thực thi hết những function được stack) thì nó rời hàng chờ
* 1.2 setTimeout
  * Cho hàm setTimeout có định nghĩa như sau: https://www.w3schools.com/jsref/met_win_settimeout.asp
  * Set đoạn code sau, hãy mô tả chính xác những gì xảy ra và kết quả in ra là gì ?
 ```
 console.log('Hi');// in ra "Hi"

setTimeout(function () {
  console.log('there');
}, 1000);// chờ 1s, sau đó in ra "there"

setTimeout(function () {
  console.log('General Kenobi');
}, 1500);
```
 * How about this one, can you guess ?
 ```
 console.log('Hi');

setTimeout(function () {
  console.log('there');
}, 0);
console.log('Hi again');
```
  * Từ ví dụ trên em có nhận xét gì ?
    * setTimeout sẽ được thực thi sau cùng
* 1.3 Event Loop
  * Tìm hiểu về Event loop, và giải thích lại đoạn code trên theo ý hiểu của em.
  
