# Giải thích cấu hình file 'haproxy.cfg'

1.  Cấu hình global:
    -   `maxconn 4096`: Giới hạn số lượng kết nối tối đa đến proxy là 4096
    -   `daemon`: Chạy HAProxy dưới dạng daemon (nền)
    -   `log 127.0.0.1 local0` và `log 127.0.0.1 local1 notice`: Cấu hình ghi log tới địa chỉ IP 127.0.0.1 và cổng local0 hoặc local1 với mức log là notice.
    -   `defaults`: Cấu hình mặc định cho các thông số timeout và log.

2.  Cấu hình mặc định (`defaults`)
    -   `timeout connect 10s`, `timeout client 30s`, `timeout server 30s`: Thiết lập thời gian chờ tối đa cho các giai đoạn kết nối, gửi dữ liệu từ client và gửi dữ liệu từ server.

3.  Cấu hình thống kê (`stats`):
    -   `stats enable`: Cho phép thống kê HAProxy.
    -   `stats uri /haproxyStats`:  Địa chỉ URL để truy cập trang thống kê.
    -   `stats auth admin:admin123`: Thông tin đăng nhập để truy cập trang thống kê.

4.  Frontend HTTP (`frontend http-in`):
    -   `bind *:80`: Liên kết frontend với cổng 80
    -   ACLs (Access Control Lists) `host_test1` và `host_test2` kiểm tra tên miền để phân loại yêu cầu đến các backend khác nhau.
    -   `use_backend bke_80_test1 if host_test1` và `use_backend bke_80_test2 if host_test2`: Sử dụng các backend khác nhau dựa trên các ACLs.

5.  Frontend HTTPS (`frontend https-in`):
    -   `bind *:443`: Liên kết frontend với cổng 443 (HTTPS)
    -   `mode tcp`, `option tcplog`: Chế độ cân bằng tải TCP và ghi log cho kết nối TCP.
    -   `tcp-request inspect-delay 10s`, `tcp-request content accept if { req_ssl_hello_type 1 }`: Kiểm tra định dạng SSL hello để xác định yêu cầu HTTPS.
    -   ACLs `acl1` và `acl2` dựa trên tên miền SSL SNI (Server Name Indication).
    -   `use_backend bke_443 if acl1 || acl2`: Sử dụng backend `bke_443` nếu một trong hai ACLs thỏa mãn.

6.  Backend `bke_80_test1` và `bke_80_test2` (HTTP backends):
    -   `balance roundrobin`:  Sử dụng cân bằng tải theo thuật toán round-robin.
    -   `option httpclose`, `option forwardfor`: Cấu hình tùy chọn HTTP cho backend.
    -   `server serverX address:port check`: Thêm các server vào backend với tên server và địa chỉ cụ thể.

7.  Backend `bke_443` (TCP backend for HTTPS):
    -   `mode tcp`, `balance source`, `option ssl-hello-chk`: Cấu hình backend cho kết nối TCP và kiểm tra SSL hello.
    -   `server server1 address:port check`: hêm server vào backend.

Nói chung, mã cấu hình này tạo ra một cơ sở cân bằng tải và reverse proxy cho các yêu cầu HTTP và HTTPS, định tuyến chúng đến các backend khác nhau dựa trên tên miền và giao thức yêu cầu.

*Lưu ý:*
-   `local0` và `local1` là các tùy chọn của cổng syslog. Có tổng cộng 8 tùy chọn (`local0`, đến `local7`), mỗi tùy chọn đại diện cho một cổng ghi log riêng biệt.
-   Cổng ghi log `local0` và `local1` có thể được cấu hình để chuyển các thông điệp đến các tệp log hoặc máy chủ ghi log từ xa.
-   Mức log `notice` đại diện cho mức cảnh báo, nó chỉ ghi lại các thông điệp log có mức cảnh báo trở lên (báo động, cảnh báo, critical, và error).
-   Cổng 443 có tác dụng: Cổng 443 đóng vai trò quan trọng trong việc đảm bảo tính bảo mật và quyền riêng tư khi truy cập các trang web và dịch vụ qua giao thức HTTPS.
    -   **Hỗ trợ HTTPS**: Cổng 443 là cổng tiêu chuẩn dành cho kết nối HTTPS, mà là phiên bản bảo mật của HTTP. Với HTTPS, dữ liệu được mã hóa và bảo mật bằng giao thức SSL/TLS, đảm bảo tính bảo mật và quyền riêng tư cho thông tin gửi qua mạng.
    -   **Sử dụng SSL/TLS**: Bằng cách cấu hình cổng 443, HAProxy có thể giải mã (decrypt) giao thức SSL/TLS của yêu cầu từ client, giúp HAProxy có thể xem và xử lý các thông tin trong yêu cầu (ví dụ: tên miền SSL SNI) để định tuyến đúng backend.
    -   **Định tuyến dựa trên SNI**: Server Name Indication (SNI) là một phần của giao thức TLS cho phép client gửi tên miền mục tiêu trong yêu cầu SSL/TLS. HAProxy có thể sử dụng thông tin này để định tuyến yêu cầu đến các backend khác nhau dựa trên tên miền.
    -   **Chuyển tiếp dữ liệu mã hóa**: HAProxy không chỉ thực hiện chức năng cân bằng tải mà còn giúp chuyển tiếp dữ liệu mã hóa từ client tới backend và ngược lại. Điều này giúp giảm tải cho backend và cho phép HAProxy kiểm soát việc cân bằng tải dựa trên thông tin được giải mã (như tên miền).
    -   **Kiểm soát cân bằng tải cho HTTPS**: Cấu hình cổng 443 cho phép HAProxy thực hiện cân bằng tải cho yêu cầu HTTPS, giúp phân phối công việc hiệu quả giữa các backend.
    -   **Cung cấp SSL Offloading**: HAProxy có thể giải mã SSL/TLS tại mức proxy, giúp giảm tải cho các backend bằng cách chuyển tiếp các yêu cầu HTTP đã giải mã. Điều này có thể giúp các backend tập trung vào xử lý logic ứng dụng hơn là tập trung vào việc giải mã SSL.

-   Luồng truy cập vào một tên miền https:
    -   **Khởi tạo Kết nối TLS**:
        -   Người dùng truy cập một trang web thông qua HTTPS bằng cách nhập tên miền vào trình duyệt.
        -   Trình duyệt của người dùng sẽ tạo một kết nối TLS bằng cách gửi một thông điệp ClientHello cho máy chủ, chứa thông tin như các phiên bản TLS hỗ trợ và danh sách các mã hóa hỗ trợ.
    -   **Xác thực SSL SNI (Server Name Indication)**:
        -   HAProxy nhận ClientHello và trích xuất tên miền được yêu cầu từ phần mở rộng SNI trong thông điệp ClientHello.
        -   HAProxy sử dụng thông tin tên miền để xác định backend tương ứng mà yêu cầu SSL/TLS sẽ được chuyển tiếp đến.
    -   **Chuyển tiếp yêu cầu đến Backend**:
        -   HAProxy sẽ chuyển tiếp yêu cầu SSL/TLS đến backend tương ứng dựa trên thông tin SNI. Điều này giúp định tuyến yêu cầu đến đúng ứng dụng hoặc máy chủ xử lý SSL/TLS cho tên miền cụ thể.
    -   **Giao tiếp giữa HAProxy và Backend**:
        -   Backend (server chạy ứng dụng web) tiếp tục giao tiếp với HAProxy thông qua giao thức SSL/TLS. Nó cung cấp chứng chỉ SSL/TLS của nó để thiết lập kết nối bảo mật.
    -   **Gửi Phản hồi từ Backend đến HAProxy**:
        -   Backend tạo và gửi phản hồi SSL/TLS, chẳng hạn như trang web, dữ liệu HTML, CSS và hình ảnh, thông qua kết nối đã thiết lập.
    -   **Chuyển tiếp Phản hồi đến Người dùng**:
        -   HAProxy nhận phản hồi từ backend và chuyển tiếp nó đến trình duyệt của người dùng thông qua kết nối TLS đã thiết lập ban đầu.
