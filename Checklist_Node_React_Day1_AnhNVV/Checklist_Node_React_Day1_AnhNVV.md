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
		* (https://github.com/gooners006/FreeCodeCamp-with-Tool/blob/master/HelloWorld/helloWorld.js)
