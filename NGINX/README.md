Ngnix là một máy chủ web và máy chủ proxy ngược (reverse proxy) mã nguồn mở được thiết kế để xử lý các yêu cầu HTTP và TCP. Nó được phát triển ban đầu bởi lgor Sysoev và hiện nay được sử dụng rộng rãi để phục vụ các ứng dụng web, tạo ra các dịch vụ proxy, cân bằng tải, và cung cấp một số chức năng.

Các chức năng chính của Ngnix bao gồm:
1.  *Web Server*: Nginx có thể hoạt động như một máy chủ web chính, cho phép nó xử lý và phản hồi với các yêu cầu HTTP từ các trình duyệt web. Nó hỗ trợ đa dạng các tính năng cần thiết cho việc phục vụ trang web như tập tin tĩnh (ví dụ: HTML, CSS, hình ảnh), các yêu cầu động thông qua các cổng thông tin (CGI), và nhiều khả năng khác.
2.  *Reverse Proxy*: Nginx có thể hoạt động như một máy chủ proxy ngược, làm trung gian giữa máy chủ ứng dụng và người dùng cuối. Khi có yêu cầu từ người dùng, Nginx có thể chuyển tiếp yêu cầu này đến máy chủ ứng dụng thích hợp và sau đó chuyển tiếp kết quả trả về cho người dùng. Điều này giúp cân bằng tải tốt hơn và bảo vệ máy chủ ứng dụng khỏi các tác động trực tiếp từ người dùng.
3.  *Cân bằng tải*:  Nginx có thể được cấu hình để phân phối yêu cầu từ người dùng đến nhiều máy chủ ứng dụng khác nhau, nhằm đảm bảo rằng tải được phân phối đồng đều giữa các máy chủ. Điều này giúp tối ưu hiệu suất và đảm bảo sự ổn định của ứng dụng. 
4.  *SSL/TLS Termination*: Nginx có khả năng xử lý SSL/TLS, cho phép nó giải mã yêu cầu SSL/TLS từ trình duyệt và sau đó gửi yêu cầu không mã hóa tới máy chủ ứng dụng. Điều này giúp giảm tải cho máy chủ ứng dụng và tăng tốc độ xử lý.
5.  *Cache*: Nginx có khả năng lưu trữ cache cho các tài nguyên tĩnh như hình ảnh, CSS và JavaScript. Điều này giúp giảm tải cho máy chủ và cải thiện thời gian tải trang web đối với người dùng.
6.  *Giám sát và ghi nhật ký*:  Nginx cung cấp các tính năng giám sát hoạt động máy chủ và ghi lại thông tin liên quan đến yêu cầu và hoạt động. Điều này giúp quản trị viên theo dõi và phân tích hiệu suất hệ thống.
7.  *Virtual Hosting*: Nginx cho phép bạn cấu hình nhiều tên miền hoạt động trên cùng một máy chủ vật lý. Điều này giúp bạn chạy nhiều trang web hoặc ứng dụng trên cùng một hạ tầng.
8.  *Gzip Compression*: Nginx hỗ trợ nén Gzip để giảm kích thước dữ liệu được truyền tải qua mạng, cải thiện thời gian tải trang web cho người dùng.
9.  *Authentication*: Bạn có thể cấu hình Nginx để yêu cầu xác thực từ người dùng trước khi truy cập vào các phần của trang web hoặc ứng dụng.
10. *URL Rewriting*: Nginx cho phép bạn thay đổi hoặc tái viết URL một cách linh hoạt. Điều này có thể hữu ích cho việc tối ưu hóa SEO hoặc điều hướng yêu cầu.
11. *IPv6 Support*: Nginx hỗ trợ IPv6, cho phép bạn xử lý các kết nối và yêu cầu từ các địa chỉ IPv6.
12. *WebSockets*: Nginx có thể cấu hình để hỗ trợ kết nối WebSockets, cho phép giao tiếp hai chiều liên tục giữa máy chủ và trình duyệt.
13. *Security Features*: Nginx có thể được cấu hình để bảo vệ khỏi các loại tấn công như DDoS, SQL injection và cross-site scripting (XSS) bằng cách sử dụng các tùy chọn bảo mật như hạn chế tần suất kết nối, kiểm tra chính xác dữ liệu đầu vào, v.v.
14. *Load Balancing Algorithms*: Nginx cung cấp một loạt các thuật toán cân bằng tải, cho phép bạn tùy chỉnh cách các yêu cầu được phân phối đến các máy chủ khác nhau, ví dụ như round-robin, least connections, và IP hash.
15. *FastCGI Support*: Nginx hỗ trợ FastCGI, một giao thức để kết nối máy chủ web với các ứng dụng động như PHP. Điều này giúp cải thiện hiệu suất khi xử lý các yêu cầu động.
16. *Server-Side Includes (SSI)*: Nginx hỗ trợ SSI, cho phép bạn chèn nội dung động vào các trang tĩnh.
