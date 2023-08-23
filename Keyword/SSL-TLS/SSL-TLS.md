# TLS là gì? Chức năng và cách hoạt động của giao thức TLS

## Giao thức TLS là gì?

TLS (Transport Layer Security) - Bảo mật tầng vận chuyển. Đây là một giao thức mật mã cung cấp bảo mật đầu cuối cho dữ liệu được gửi giữa các ứng dụng qua internet.
TLS được biết đến chủ yếu thông qua việc sử dụng trong duyệt web an toàn với chuẩn HTTPS và đặc biệt là biểu tượng ổ khóa xuất hiện trong trình duyệt web khi một phiên truy cập bảo mật được thiết lập. Tuy nhiên, nó cũng có thể và được khuyến khích sử dụng cho các ứng dụng khác như e-mail, truyền tệp, hội nghị truyền hình / âm thanh, nhắn tin tức thì và VoIP, cũng như các dịch vụ Internet như DNS và NTP.
TLS phát triển từ Lớp cổng bảo mật (SSL -  Secure Sockets Layer) bởi Netscape Communications Corporation vào năm 1994 để bảo mật các phiên duyệt web. TLS lần đầu tiên được định nghĩa trong RFC 2246 vào năm 1999 như một giao thức độc lập với ứng dụng. Cần lưu ý rằng TLS không bảo mật dữ liệu trên các hệ thống đầu cuối. Nó chỉ đảm bảo dữ liệu an toàn trên đường truyền qua Internet, tránh khả năng bị nghe trộm hoặc thay đổi nội dung.
TLS thường được triển khai trên TCP để mã hóa các giao thức Lớp ứng dụng như HTTP, FTP, SMTP và IMAP, mặc dù nó cũng có thể được triển khai trên UDP, DCCP và SCTP (ví dụ: đối với ứng dụng dựa trên VPN và SIP).

## Tại sao mã hóa TLS lại quan trọng?

Trong thời kỳ mà tội phạm mạng đang ngày càng gia tăng cùng với sự phát triển nhanh chóng của Internet, đảm bảo an toàn cho các dịch vụ và website là yêu cầu quan trọng mà trong đó TLS là một giao thức cần thiết. TLS sẽ giúp cả khách hàng và nhà cung cấp dịch vụ qua Internet an tâm hơn với các hoạt động online, giảm thiểu các mối đe dọa tấn công mạng như nghe lén, giả mạo, đánh cắp dữ liệu,...
Nhìn chung chuyển dịch sang các giao thức bảo mật cao như TLS là xu hướng tất yếu của lĩnh vực công nghệ. Không đảm bảo được các yếu tố bảo mật thì những tiến bộ công nghệ mới nhất cũng chưa hẳn đem đến nhiều lợi ích hơn so với các vấn đề phát sinh.

## TLS hoạt động như thế nào?

TLS bảo mật thông tin liên lạc bằng cách sử dụng asymmetric public key infrastructure (cơ sở hạ tầng khóa công khai bất đối xứng) để khởi tạo kết nối giữa client – server và sau đó sử dụng khóa đối xứng (symetric) để mã hóa trong phần còn lại của phiên truyền dữ liệu. Trước hết ta cùng xem các phương thức mã hóa này hoạt động thế nào.

Giao thức mã hóa bất đối xứng sử dụng hai khóa khác nhau để mã hóa thông tin liên lạc giữa hai bên:
-   Khóa riêng tư - private key: Khóa này do chủ sở hữu trang web kiểm soát và nó được lưu giữ một cách riêng tư. Khóa này nằm trên máy chủ web và được sử dụng để giải mã thông tin được mã hóa bởi khóa công khai.
-   Khóa công khai - public key: khóa này khả dụng cho tất cả những ai muốn tương tác với máy chủ theo cách an toàn. Thông tin được mã hóa bằng khóa công khai chỉ có thể được giải mã bằng khóa riêng tư.

Cặp public key và private key có mối quan hệ được xác định bằng hàm toán học, nhưng được thiết kế để việc tính toán private key từ public key gần như là bất khả thi với độ dài khóa đủ lớn. Thuật toán cũng đảm bảo tin nhắn được mã hóa bằng public key không thể giải mã bằng chính public key mà phải có private key (được lưu trữ ở server). Do đó Client có thể khởi tạo một khóa chung và trao đổi với server mà không sợ hacker nghe lén public key và giải mã nó. Khóa chung này sau đó được dùng cho giao thức mã hóa đối xứng.

Với giao thức mã hóa đối xứng (symmetric), dữ liệu được mã hóa và giải mã bằng khóa bí mật (secret key) mà cả người gửi và người nhận đều biết; thường là 128 nhưng tốt nhất là có độ dài 256 bit (bất kỳ thứ gì nhỏ hơn 80 bit hiện được coi là không an toàn). Mã hóa đối xứng hiệu quả hơn về mặt tính toán so với mã hóa bất đối xứng, nhưng có một khóa bí mật chung có nghĩa là nó cần được chia sẻ một cách an toàn. Đó là lý do ban đầu ta cần sử dụng mã hóa bất đối xứng để trao đổi secet key nhưng sau đó lại dùng mã hóa đối xứng để trao đổi các dữ liệu lớn.

Quá trình bắt tay TLS được diễn ra như sau:
-   Client gửi một message “client hello" tới Server. Message này bao gồm version của SSL trên client, cipher setting (các thiết lập về mật mã), session data và các thông tin cần thiết khác mà server cần để client có thể giao tiếp thông qua giao thức SSL.
-   Server phản hồi với một message “server hello”. Message này cũng bao gồm version của SSL trên server, thiết lập mật mã, session data, public key và các thông tin cần thiết khác mà client cần để giao tiếp thông qua SSL.
-   Client tiến hành xác nhận SSL certificate (public key và các info khác mà Server vừa gửi) với Certificate Authority - CA (là các đơn vị thứ 3 cung cấp dịch vụ chứng thực số, ví dụ: GeoTrust, Digicert...). Nếu xác nhận thất bại thì client sẽ từ chối giao tiếp, quá trình bắt tay SSL sẽ bị dừng lại. Nếu xác nhận thành công thì tiếp tục bước sau
-   Client sinh một session key (hay chính là symetric secret key đã đề cập ở trên), mã hóa nó với public key và gửi nó đến server.
-   Server dùng private key để giải mã session key sau đó gửi kết quả thành công về cho client. Kết quả này cũng sẽ được mã hóa đối xứng với session key mà vừa được giải mã.

Sau khi việc khởi tạo trên hoàn tất, quá trình giao tiếp còn lại (trên các giao thức HTTPS/FTM/STMP,…) được mã hóa 2 chiều bằng symetric secret key nói trên.

Bên cạnh khả năng mã hóa dữ liệu đầu cuối, TLS còn cho phép ứng dụng khách xác thực quyền sở hữu khóa công khai của máy chủ, để đảm bảo website/máy chủ đang được truy cập tới là chính xác. Điều này thường được thực hiện bằng cách sử dụng chứng chỉ số X.509 được cấp do bên thứ ba đáng tin cậy (được gọi là Tổ chức phát hành chứng chỉ - CA) để xác nhận tính xác thực của khóa công khai. Trong một số trường hợp, máy chủ có thể sử dụng chứng chỉ tự ký và nó cần được máy khách chấp nhận một cách rõ ràng (trình duyệt sẽ hiển thị cảnh báo người dùng khi gặp chứng chỉ không đáng tin cậy). Các chứng chỉ riêng như vậy có thể được sử dụng trong các mạng riêng hoặc nơi có thể đảm bảo phân phối chứng chỉ an toàn. Tuy nhiên, chứng chỉ do các CA công khai cấp vẫn thường đáng tin cậy hơn.

## Chức năng của giao thức TLS

### Mã hóa (encryption)
Như đã đề cập, TLS sử dụng kết hợp các thuật toán mã hóa đối xứng và mã hóa bất đối xứng để đảm bảo dữ liệu được an toàn trong quá trình truyền qua Internet. Khả năng mã hóa của TLS có thể được sử dụng kết hợp với các giao thức khác như TCP để tăng cường bảo mật cho kết nối dữ liệu.

### Xác thực (authentication)
Bên cạnh mã hóa, xác thực là một chức năng quan trọng khác của TLS. Hãy tưởng tượng bạn kết nối với máy chủ giả mạo của một hacker mà không nhận ra, khởi tạo cả một đường hầm an toàn cho dữ liệu với đủ các phương thức bảo mật chỉ để đảm bảo rằng dữ liệu của mình sẽ đến tay hacker một cách “an toàn và nguyên vẹn”, thật mỉa mai! Do đó khả năng xác thực máy chủ, đặc biệt là qua các chứng chỉ cấp bởi bên thứ ba, là rất cần thiết để đảm bảo kết nối Internet an toàn.

### Bảo đảm tính toàn vẹn dữ liệu (data intergrity)
Kết hợp chức năng mã hóa và xác thực, TLS giúp đảm bảo tính toàn vẹn dữ liệu. Mã hóa giúp thông tin truyền giữa client và server không thể bị nghe lén hay thay đổi trong khi xác thực bảo vệ dữ liệu khỏi những địa chỉ giả mạo do hacker tạo ra. TLS đảm bảo tính bảo mật trong khi vẫn cung cấp hiệu suất ổn, nhất là khi cấu hình máy tính hiện đại đang ngày càng trở nên mạnh mẽ.

### Ngăn chặn phát lại:
Một chức năng cuối cùng của giao thức TLS chính là ngăn chặn phát lại. Với chức năng này, người dùng sẽ được bảo vệ khỏi các cuộc tấn công trung gian hoặc các cuộc tấn công vũ phu.

### Lợi ích của TLS là gì?
TLS cung cấp cơ chế xác thực an toàn, mã hoá dữ liệu và giúp kiểm tra tính toàn vẹn của dữ liệu. Tuy nhiên, khi so sánh TLS với Internet Protocol Security, TLS cung cấp cho người dùng những lợi ích bổ sung như sau:

- Tính năng bảo mật được tích hợp trực tiếp vào mỗi ứng dụng. Khác với phần mềm hoặc phần cứng bên ngoài để xây dựng đường hầm IPsec.

- Mã hoá end-to-end giữa các thiết bị giao tiếp.

- TLS có sự kiểm soát chi tiết với những gì được truyền hoặc nhận diện trên một phiên được mã hoá.

- TLS hoạt động trong các lớp trên của mô hình OSI nên khi sử dụng giao thức TLS sẽ không xảy ra những rắc rối trong việc dịch địa chỉ mạng NAT so với IPsec.

- Cuối cùng, TLS cung cấp chức năng ghi nhận nhật ký và giúp người dùng kiểm tra được tích hợp trực tiếp vào giao thức.

### Thực tế sử dụng

TLS (Transport Layer Security) được sử dụng rộng rãi trong nhiều khía cạnh của việc bảo mật truyền thông qua mạng. Dưới đây là một số cách thực tế mà TLS được áp dụng:

1. **Bảo mật trang web (HTTPS)**:
   TLS thường được sử dụng để bảo mật trang web thông qua giao thức HTTPS. Khi bạn truy cập một trang web bằng HTTPS, dữ liệu giữa trình duyệt của bạn và máy chủ web được mã hóa bằng TLS, ngăn chặn bất kỳ ai khác không có quyền truy cập vào thông tin cá nhân, mật khẩu và dữ liệu khác trên trang web.

2. **Máy chủ thư điện tử (Email)**:
   TLS cũng được sử dụng trong việc bảo mật truyền thông email. Khi hai máy chủ email giao tiếp với nhau thông qua TLS, dữ liệu email được mã hóa, ngăn chặn việc nghe trộm dữ liệu trong quá trình truyền tải.

3. **Kết nối VPN (Virtual Private Network)**:
   TLS cũng có thể được sử dụng trong việc thiết lập kết nối VPN để tạo một kênh truyền thông an toàn giữa người dùng và mạng nội bộ của tổ chức. Điều này giúp bảo vệ dữ liệu khi bạn kết nối từ xa đến mạng nội bộ.

4. **Ứng dụng truyền thông thời gian thực (Real-time Communication Apps)**:
   Các ứng dụng truyền thông thời gian thực như cuộc gọi video, trò chuyện và truyền phát trực tiếp cũng có thể sử dụng TLS để đảm bảo tính riêng tư và an toàn trong việc truyền dữ liệu.

5. **Websocket và ứng dụng thời gian thực trên Web**:
   TLS cũng được sử dụng để bảo mật kết nối Websocket và các ứng dụng thời gian thực trên Web, đảm bảo rằng dữ liệu truyền tải giữa máy khách và máy chủ được mã hóa và bảo mật.

6. **Ứng dụng di động và IoT (Internet of Things)**:
   TLS cũng có thể được sử dụng trong các ứng dụng di động và IoT để bảo mật việc truyền dữ liệu qua mạng từ các thiết bị di động và IoT đến máy chủ.

Tóm lại, TLS là một công nghệ quan trọng trong việc đảm bảo tính riêng tư và bảo mật trong truyền thông qua mạng, và nó được áp dụng rộng rãi trong nhiều tình huống và ứng dụng khác nhau.