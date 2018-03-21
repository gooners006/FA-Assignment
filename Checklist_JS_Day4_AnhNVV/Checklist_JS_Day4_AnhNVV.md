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
   * Đầu tiên chương trình chạy console.log đầu tiên, sau đó khi thấy setTimeout sẽ được API thực hiện, rồi đưa xuống queue. Chương trình chạy tiếp console.log thứ 2. Khi này stack đã empty thì event-loop mới đẩy function từ queue lên stack
* 1.4 Callbacks
  * Tìm hiểu về callback funtions trong JS: 
   * trong JS, function là object nên có thể nhận function khác làm argument và trả lại một fuction khác, chúng gọi là higher-order function. những function bị truyền vào dưới dạng một argument và được gọi bởi higher-order function đó là callback function
   * Người ta nói callback functions đóng gói tính liên tục của chương trình. Theo em chương trình dưới sẽ được chạy liên tục ra sao?
    * 1-3-2: chương trình chạy đến 1, sau khi chạy xong sẽ đến setTimeout, khi đó sẽ đưa function chứa 2 vào api đợi 1s. trong lúc đó chương trình chạy 3. sau khi đợi hết 1s thì function chứa 2 sẽ được đưa vào queue, khi event-loop thấy trong queue có message và stack đang empty thì sevent-loop đẩy function 2 lên stack. Khi đó chương trình thực hiện function 2.
 * 1.4.1 Nested/Chained Callbacks
  * Set đoạn code sau, khi người dùng click vào btn thì điều gì xảy ra?
  ```
  // (0)
var btn = document.getElementById('btn');
btn.addEventListener('click', function () {
  // (1)
  setTimeout(function () {
    // (2)
  }, 1000);
  // (3)
});
// chương trình sẽ chạy 0->1->3->2
```
* Theo em những điểu bất lợi của callbacks là gì ? liên quan đến: code readability, code security, handle errors code, code reusability
  * lạm dụng callback sẽ dẫn đến 1 số tác hại như: 
    * sẽ phải viết nhiều callback, lặp lại nhiều lần nếu như chương trình có quy mô lớn -> dễ quên không check error -> khó tìm bug
    * phải lùi đầu dòng nhiều -> khó đọc
* 1.5 Promises
 * Tìm hiểu về Promises: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
 * What is a future value ?
   * là một giá trị giữ chỗ thay cho giá trị thật, khi nào chương trình có giá trị thật thì sẽ thay giá trị đó vào giá trị giữ chỗ. Giá trị giữ chỗ giúp cho giá trị thật không phụ thuộc vào thời gian, phục vụ cho việc lập trình bất đồng bộ
 * Promise value ?
 * Promise Events ?
 * How to get Promise value?
 * How to handle error in Promise ?
  	* sử dụng split callback: 1 callback cho việc hoàn thành và 1 callback cho việc báo lỗi
  	* sử dụng catch()
 * How to chain Promises ?
 	* sử dụng then()
