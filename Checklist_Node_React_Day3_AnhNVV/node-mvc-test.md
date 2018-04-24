* 1 Concept
	* 1.1 MVC Pattern
		* 1.1.1 Understand MVC Pattern
			* https://www.codecademy.com/articles/mvc
			* https://softwareengineering.stackexchange.com/questions/127624/what-is-mvc-really
		* 1.1.2 What is its advantages/disadvantages ?
			* Advantages: 
				* giúp viết code có tổ chức hơn, dễ quản lí
				* có thể tạo nhiều view cho 1 model, ko sợ bị duplicate code
				* hỗ trợ bất đồng bộ
				* khi có thay đổi ở model không làm ảnh hưởng đến toàn bộ code vì model ko bị phụ thuộc vào views
				* dữ liệu trả về ko bị format -> có thể làm việc với nhiều interface
				* làm việc tốt với search engine
			* Disadvantages: 
				* phức tạp hơn
				* cần phải hiểu cả code bên client
				* tự động gen ra các câu lệnh SQL -> khó hoặc có thể không can thiệp vào để tối ưu 
		* 1.1.3 When to use MVC ?
			* nên luôn sử dụng mvc mỗi khi code
	* 1.2 ORM
		* 1.2.1 Understand ORM and why its important ?
			* https://medium.freecodecamp.org/a-comparison-of-the-top-orms-for-2018-19c4feeaa5f
			* là một kĩ thuật, cơ chế lập trình, ánh xạ từ mô hình đối tượng với các table trong cơ sở dữ liệu quan hệ, các đối tượng ánh xạ với các bảng và quan hệ của table trong database sẽ được ánh xạ với sự ràng buộc liên quan trong đối tượng
	* 1.3 Testing
