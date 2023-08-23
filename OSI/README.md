Mô hình OSI (Open Systems Interconnection) là một mô hình tham khảo để hiểu cách các hệ thống máy tính giao tiếp với nhau trong một mạng máy tính. Mô hình này được phát triển bởi Tổ chức Tiêu chuẩn Hóa Quốc tế (ISO) và được công bố vào năm 1984. Mục tiêu chính của mô hình OSI là xác định các lớp và giao thức để cho phép truyền thông hiệu quả giữa các hệ thống không tương thích về cả phần cứng lẫn phần mềm.

Mô hình OSI chia quá trình truyền thông thành 7 lớp, mỗi lớp thực hiện một số nhiệm vụ cụ thể. Các lớp này là:

1. Lớp Vật lý (Physical Layer): Đây là lớp chịu trách nhiệm về việc truyền dẫn tín hiệu qua các phương tiện vật lý như cáp, sóng vô tuyến. Nó đảm bảo việc truyền dẫn dữ liệu giữa các thiết bị.

2. Lớp Liên kết dữ liệu (Data Link Layer): Lớp này xử lý việc gói dữ liệu thành các khung và quản lý truy cập vào phương tiện truyền thông. Nó đảm bảo luồng dữ liệu không bị xung đột và kiểm soát lỗi truyền thông.

3. Lớp Mạng (Network Layer): Lớp này quản lý địa chỉ logic của các thiết bị trong mạng, điều hướng gói dữ liệu từ nguồn đến đích và thực hiện chức năng định tuyến.

4. Lớp Giao vận (Transport Layer): Lớp này cung cấp các dịch vụ truyền thông định tuyến và kiểm soát dòng. Nó chia dữ liệu thành các phần nhỏ hơn để gửi và đảm bảo rằng dữ liệu được gửi và nhận đúng thứ tự và không bị mất.

5. Lớp Phiên (Session Layer): Lớp này thiết lập, duy trì và đóng kết nối giữa các ứng dụng trên các máy tính khác nhau. Nó quản lý quá trình trao đổi dữ liệu giữa các ứng dụng.

6. Lớp Trình diễn (Presentation Layer): Lớp này chịu trách nhiệm về định dạng dữ liệu, mã hóa và giải mã dữ liệu để đảm bảo rằng các thiết bị có thể hiểu và xử lý dữ liệu nhau.

7. Lớp Ứng dụng (Application Layer): Đây là lớp gần gũi nhất với người dùng, cung cấp các dịch vụ mạng trực tiếp cho người dùng như trình duyệt web, email, truyền tệp, v.v.

Mô hình OSI giúp cho việc thiết kế, triển khai và quản lý mạng dễ dàng hơn bằng cách chia nhỏ quá trình truyền thông thành các lớp riêng biệt và xác định các giao thức tương ứng cho từng lớp.