* 'NodeJS introduction
	* Node JS là gì?
		* NodeJS là một nền tảng Server side được xây dựng dựa trên Javascript Engine (V8 Engine). Node sử dụng mô hình event-driven, non-blocking I/O.
	* Điểm mạnh và điểm yếu của NodeJs?
		* Mạnh: 
			* nhanh
			* có cơ chế non-blocking I/O nên có thể đồng thời xử lý nhiều request
			* dùng JS nên cả front-end và back-end đều sử dụng chung ngôn ngữ, hiểu quả hơn
		* Yếu:
			* các API của Node chưa ổn định, thay đổi liên tục.
			* chưa hỗ trợ lập trình đa luồng nên không phù hợp với các chương trình cần nặng về tính toán
			* chưa có các thư viện chuẩn
			* hỗ trợ cho các CSDL quan hệ còn yếu
	* V8 Engine là gì?
		* là một engine JS do Google phát triển. V8 compile JS thẳng sang ngôn ngữ máy rồi thực thi.
	* Nêu mô hình client - server ?. Cụ thế mô hình client server ở trong web service
		* Mô hình: máy khách gửi request lên máy chủ, máy chủ xử lý và trả lại kết quả
		* Cụ thể: VD: người dùng truy cập facebook, tìm người có tên A, máy chủ của FB sẽ tìm trong database những người có tên A và trả lại kết quả đó cho người dùng
	* Thế nào là code js ở phía server?
		* là những lệnh viết bằng JS được xử lí bên máy chủ, không như những lệnh JS được xử lí trên trình duyệt là bên client
	* Cài đặt node và kiểm tra phiên bản của node và npm ?
		* 
		```
		node -v
		npm -v
		```
	* Use node CLI to run js script ?
		* 
		```
		node filename.js
		```
	* Viết script để lắng nghe cổng 3000 trả về Hello World ?
		* https://github.com/gooners006/FreeCodeCamp-with-Tool/blob/master/HelloWorld/helloWorld.js
* NPM
	* NPM là gì ?. Nêu các lợi ích khi sử dụng trình quản lí package ?
		* dễ quản lí các package và version của nó
	* File package.json dùng để làm gì ? Cách tạo file và nêu chức năng của từng trường trong file package.json
		* dùng để lưu thông tin các package, người khác chỉ cần file này có thể tải về các package cần thiết
	* Dependency la gì ?, devDependencies là gì ?
		* dev dùng khi build, dependency dùng khi chạy
* Dev-tools
	* Tìm hiểu node debugger là gì ?
		* là debugger của node js
	* Phân biệt babel-cli, babel-presets-es2015, babel-presets-stage-2 ?
		* babel-cli: command line
		* babel-presets-es2015: chuẩn es6
		* babel-presets-stage-2: các tính năng mới đang chờ approve
	* Webpack là gì ?. Ứng dụng của Webpack trong dự án NodeJS
		* là một module bundler(nhiều module được nhóm lại, manage and load interdependent modules, but do it as part of the application build rather than at runtime.)
	* Linter là gì ?, Cài đặt ES Lint bằng NPM
		* là trình kiểm tra coding convention
* Node core
	* Để trở thành một webserver thì hệ thống cần đảm bảo những tiêu chí gì ?
		* khả năng tổ chức các code để có thể tái sử dụng
		* khả năng xử lí các file(đọc, ghi, lưu, ...)
		* khả năng xử lí các CSDL(CRUD)
		* khả năng liên lạc qua internet
		* khả năng nhận request và phản hồi đúng chuẩn
		* khả năng xử lí những công việc tốn nhiều thời gian
	* Module Pattern là gì ?
		* là phương pháp viết code theo thành các module riêng biệt với rất nhiều lợi thế:
			* Scalable: rất dễ thêm, sửa, xóa các tính năng mà ko gây ảnh hưởng đến các module khác
			* giảm thiểu conflict vì mỗi module đều được viết riêng, ko dùng chung
			* quản lí các biến local tốt, ko sợ khai báo nhiều biến global gây conflict
			* dễ dàng mở rộng mà ko gây ảnh hưởng đến module gốc
	* Các phương thức require, exports, module.exports dùng để làm gì ?
		* dùng để xuất và nhập các module để đem vào sử dụng trong code
	* So sánh require ES5 => import Es6, sử dụng Babel để convert từ ES6 về  ES5
		* compare
			* Require:
				* You can have dynamic loading where the loaded module name isn't predefined /static, or where you conditionally load a module only if it's "truly required" (depending on certain code flow).
				* Loading is synchronous. That means if you have multiple requires, they are loaded and processed one by one.
			* Import:
				* You can use named imports to selectively load only the pieces you need. That can save memory.
				* Import can be asynchronous (and in current ES6 Module Loader, it in fact is) and can perform a little better.
		* convert
		```javascript
		import booWho from "../BooWho/booWho"; 
		```
		=>
		```javascript
		var _booWho = require("../BooWho/booWho");

		var _booWho2 = _interopRequireDefault(_booWho);
		```
		
	* Node APIs là gì ?
		* là những api được viết riêng cho node dùng khi lập trình server
	* Fs module trong NodeJS dùng để làm gì ?
		* là một module cho phép làm việc với các file hệ thống trên máy tính
		* các thao tác thông dụng:CRUD, rename
	* Viết  chương trình tạo, viết và đọc file ?
		* https://github.com/gooners006/Checklist-Exercise/tree/master/CRU
	* Sự khác biệt giữa Fs asynchronous và Fs synchronous là gì ?
		* async vẫn có thể tiếp tục thực hiện các thao tác khác khi đang đọc, ghi, ... file, còn sync thì cần phải xong tác vụ này mới có thể làm tiếp tác vụ khác
	* Http module trong NodeJS dùng để làm gì ?
		* module này cho phép node truyền dữ liệu bằng phương thức http
	* Tạo một server đơn giản lẳng nghe ở cổng 8000, request trả lại "Hello world" sử dụng Http APIs
		* https://github.com/gooners006/FreeCodeCamp-with-Tool/blob/master/HelloWorld/helloWorld.js
	* Event emitter trong nodejs là gì ?. Kể tên và nêu chức năng của các phương thức trong lớp Event emitter
		* Event Emitter là một class chứa tất cả những object mà emit ra một event chúng ta có thể dùng event emitter để tạo ra những event 
		* Các phương thức:
			* EventEmitter.defaultMaxListeners: đặt giới hạn số lượng listener cho 1 event
			* emitter.addListener(eventName, listener): đặt một listener cho 1 sự kiện
			* emitter.emit(eventName[, ...args]): lần lượt gọi các listener của event
			* emitter.eventNames(): trả lại 1 mảng tên các sự kiện đã có listener trong emitter
			* emitter.getMaxListeners(): trả lại giá trị listener tối đa của emitter
			* emitter.listenerCount(eventName): trả lại số lượng listener của 1 event
			* emitter.listeners(eventName): trả lại bản sao của mảng các listener của event
			* emitter.on(eventName, listener): giống emitter.addListener
			* emitter.once(eventName, listener): đặt 1 listener dùng 1 lần, sau khi dùng sẽ mất
			* emitter.prependListener(eventName, listener): thêm listener lên đầu mảng
			* emitter.prependOnceListener(eventName, listener):thêm listener lên đầu mảng dùng 1 lần
			* emitter.removeAllListeners([eventName]): gỡ hết các listener
			* emitter.removeListener(eventName, listener): gỡ 1 listener 
			* emitter.setMaxListeners(n): đặt số lượng listener tối đa
			* emitter.rawListeners(eventName): trả lại bản sao của mảng các listener của event, có cả wrapper
	* Chức năng của Event Loop là gì ?.  Event loop trong nodeJs có giống Event loop trong engine V8 hay không ?
		* Tương tự như trong V8
	*  Trình bày các khái niệm: Event Driven, Non - Blocking trong nodeJS 
		* hướng sự kiện
		*non-blocking là nhờ async
	* Phân biệt giữa asynchronous và Non - Blocking trong NodeJS ?
		* non-blocking là nhờ dùng async
* Express
	* Express là gì ?. Nếu chức năng của framework này ? 
		* là một framework hỗ trợ cho nodejs trong việc phát triển các ứng dụng web
	* WebServices la gi ? Có bao nhiêu loại: RESTful, SOAP
		* là những thành phần ứng dụng để chuyển từ 1 ứng dụng thành ứng dụng web. Các ứng dụng web có thể liên lạc vs nhau để trao đổi dữ liệu
		* có 2 loại chính là RESTful và SOAP
			* SOAP: là một giao thức nền tảng XML, dùng để truy cập các web service
			* RESTful: là một phong cách thiết kế, không phải là một giao thức như SOAP, do đó RESTful có thể dùng SOAP
		* Có các loại RESTFull method nào ?
			* POST: dùng để tạo tài nguyên mới
			* GET: dùng để đọc tài nguyên
			* PUT: update thông tin tài nguyên
			* PATCH: thay đổi thông tin của tài nguyên
			* DELETE: xóa tài nguyên
		* Các bước tạo ra web server đơn giản bằng Express ?
			* https://github.com/gooners006/Checklist-Exercise/tree/master/ExpressHelloWorld
		* Routing là gì ?
			* định tuyến là quyết định đường đi của các request sẽ có những phản hồi như thế nào từ ứng dụng
		* Nếu các khái niệm Route method, Route path, Route param ?
			* Route method: là các method http, nó gắn lienf với instance của class express
			* route path: là đường dẫn đến nơi và client gửi request
			* route param: những tham số để bắt các giá trị trên đường dẫn
		* Template engine là gì ?, trình bày cách để tạo template trong express
			* 
