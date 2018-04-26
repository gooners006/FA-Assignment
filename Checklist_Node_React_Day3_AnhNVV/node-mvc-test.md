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
				* tự động gen ra các câu lệnh SQL 
		* 1.1.3 When to use MVC ?
			* nên luôn sử dụng mvc mỗi khi code
	* 1.2 ORM
		* 1.2.1 Understand ORM and why its important ?
			* https://medium.freecodecamp.org/a-comparison-of-the-top-orms-for-2018-19c4feeaa5f
			* là một kĩ thuật, cơ chế lập trình, ánh xạ từ mô hình đối tượng với các table trong cơ sở dữ liệu quan hệ, các đối tượng ánh xạ với các bảng và quan hệ của table trong database sẽ được ánh xạ với sự ràng buộc liên quan trong đối tượng
	* 1.3 Testing
		* 1.3.1 Understand TDD, BDD: https://codeutopia.net/blog/2015/03/01/unit-testing-tdd-and-bdd/
			* TDD: viết test trước rồi dựa theo test mà viết code.
			* BDD: là sự mở rộng của TDD, BDD là xây dựng kịch bản để viết test, thực thi test
		* 1.3.2 Understand about Unit Test:
			* https://medium.com/@lazlojuly/how-to-get-started-with-unit-testing-part-1-7f490bbf560a
			* https://stackoverflow.com/questions/16860/getting-started-with-unit-testing
			* https://blog.risingstack.com/node-hero-node-js-unit-testing-tutorial/
			* https://hackernoon.com/a-crash-course-on-testing-with-node-js-6c7428d3da02
			* Unit test: là test từng đơn vị code một như một function hay module.
		* 1.3.3 Understand about Test runner (e.g jest, mocha)
			* là một thư viện hoặc tool dùng để test các unit test do mình viết
		* 1.3.4 Understand about Test Assertion Framework (e.g chai, jasmine)
			* Karma is an example of a test runner
			* Mocha is an example of a testing framework
			* Chai is an example of an assertion library
			* Sinon is an example of a testing plugin
			* trong it là assertion library, ngoài it là của testing framework 
		* 1.3.5 Understand about spies, stubs and mocks (e.g sinon) 
			* spies: dùng để lấy thông tin của function call như nó được gọi bao nhiêu lần, có những đối số nào, trả về giá trị gì, có err gì được throw ra,... Spies thường sử dụng khi muốn xác nhận rằng đã có điều gì đó xảy ra
			* stubs: 
				* dùng để thay thế những đoạn code rắc rối như cần phải kết nối vs mạng hay DB
				* kích hoạt những path đáng lẽ sẽ ko xảy ra như error handling
			* mock:
				* should be used primarily when you would use a stub, but need to verify multiple more specific behaviors on it.
				* expect được đặt ở ngay trong mock function chứ ko để ở cuối như spies và stub
		* 1.3.6 Understand code coverage (e.g nyc)
			* dùng để kiểm tra xem code được tự động test bao nhiêu %, càng cao càng tốt
		* 1.3.7 Understand HTTP mocking (e.g nock)
			* dùng để test các http request một các độc lập, không cần phải có request thật
	* 1.4 API Security
		* 1.4.1 Understand Authentication vs Authorization (https://blog.restcase.com/restful-api-authentication-basics/)
	* 1.5 API Testing with postman
	* 1.6 Practice
		* 1.6.1 Build Node MVC app with mongoose:
