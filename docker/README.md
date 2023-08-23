# Docker là gì?

Docker là một nền tảng mã nguồn mở giúp bạn đóng gói, phân phối và chạy ứng dụng cùng với tất cả các phụ thuộc của chúng trong một môi trường cô lập gọi là container. Containers giúp đảm bảo rằng ứng dụng của bạn sẽ hoạt động như mong đợi trên mọi máy tính hoặc môi trường triển khai mà bạn chạy chúng, không phụ thuộc vào sự khác biệt của hệ thống. Docker đã đạt được sự phổ biến lớn trong việc phát triển ứng dụng và triển khai chúng trên nhiều môi trường khác nhau.

Dưới đây là một lộ trình học cơ bản về Docker:

1. **Hiểu cơ bản:**
   - Đọc về khái niệm container và sự cần thiết của chúng trong quá trình phát triển ứng dụng.

    Container là một hình thức ảo hóa mức hệ điều hành, cho phép bạn đóng gói ứng dụng và tất cả các thành phần cần thiết của nó - mã nguồn, thư viện, biến môi trường và cấu hình - trong một môi trường cô lập. Điều này giúp đảm bảo rằng ứng dụng sẽ hoạt động như mong đợi trên bất kỳ máy tính hoặc môi trường nào mà bạn chạy chúng, bất kể sự khác biệt về cài đặt hệ thống.

    Một số khái niệm quan trọng về container:

    -   Cô lập và Độc lập: Containers cung cấp môi trường cô lập cho ứng dụng. Điều này đảm bảo rằng các ứng dụng và tài nguyên của chúng không tác động lẫn nhau. Mỗi container chạy như một thể thức ảo hóa mức hệ điều hành, nhưng tốn ít tài nguyên hơn và khởi động nhanh hơn so với máy ảo truyền thống.
    -   Tích hợp và Đóng gói: Container cho phép đóng gói toàn bộ ứng dụng và các phụ thuộc của nó vào một đơn vị duy nhất. Điều này giúp giảm thiểu các vấn đề liên quan đến việc tương tác giữa các thành phần khác nhau của ứng dụng và đảm bảo tính nhất quán trong việc triển khai.
    -   Di động và Triển khai dễ dàng: Containers có thể di chuyển giữa các môi trường phát triển, thử nghiệm và triển khai mà không cần thay đổi mã nguồn. Điều này giúp giảm thiểu sự phụ thuộc vào cài đặt hệ thống cụ thể và giúp việc triển khai trở nên đơn giản hơn.
    -   Khả năng mở rộng và Quản lý dễ dàng: Containers có thể được sao chép và triển khai một cách dễ dàng để mở rộng ứng dụng khi cần thiết. Công cụ quản lý container như Docker cung cấp giao diện dễ sử dụng để tạo, quản lý và theo dõi các container.
    -   Hiệu suất tốt: Do containers chia sẻ hạt nhân của hệ điều hành, chúng tiết kiệm tài nguyên hệ thống và khởi động nhanh hơn so với máy ảo truyền thống.

    Tóm lại, sự cần thiết của container trong quá trình phát triển ứng dụng nằm ở khả năng cung cấp môi trường cô lập, đóng gói ứng dụng và phụ thuộc của nó, dễ dàng triển khai và di chuyển giữa các môi trường, cùng với khả năng quản lý và mở rộng hiệu quả.

    Các thành phần của Docker:
    1.  Docker Engine:
        -   Docker engine là thành phần trung tâm của Docker, cung cấp môi trường chạy các container và quản lý chúng.
        -   Bao gồm hai thành phần quan trọng:
            -   Docker Daemon:  Đây là tiến trình chạy phía máy chủ (server-side) quản lý các container. Nó lắng nghe các yêu cầu từ Docker CLI và quản lý các container, images và dịch vụ.
            -   Docker API: Cung cấp giao diện lập trình ứng dụng (API) để tương tác với Docker Daemon thông qua các yêu cầu HTTP.
    2.  Docker CLI (Command Line Interface):
        -   Docker CLI là công cụ dòng lệnh cho phép bạn tương tác với Docker Engine thông qua các lệnh dòng lệnh.
    3.  Images:
        -   Images là tập hợp các tệp và hướng dẫn cần thiết để tạo ra một container cụ thể. Chúng chứa mã nguồn, thư viện, tài nguyên và cấu hình cần thiết để chạy một ứng dụng.
    4.  Container:
        -   Container là một thực thể chạy từ một image cụ thể. Chúng cung cấp môi trường cô lập để chạy ứng dụng mà không ảnh hưởng đến môi trường bên ngoài.
    5.  Docker Registry:
        -   Docker Registry là nơi lưu trữ các images. Docker Hub là một ví dụ phổ biến về public registry. Bạn cũng có thể tự tạo private registry.
    6.  Docker compose:
        -   Docker Compose là một công cụ giúp định nghĩa và quản lý nhiều dịch vụ liên quan đến ứng dụng trong một tệp cấu hình duy nhất. Nó giúp bạn triển khai và quản lý toàn bộ môi trường phát triển của mình.
    7.  Docker Swarm và Kubernetes:
        -   Đây là các công cụ cho phép quản lý một tập hợp lớn các container và cân bằng tải chúng trên nhiều máy chủ. Kubernetes cũng là một hệ thống quản lý container phổ biến khác ngoài Docker Swarm.
    8.  Dockerfile:
        -   Dockerfile là một tệp văn bản chứa các chỉ thị và hướng dẫn để xây dựng một image. Nó mô tả cách mà một image nên được cấu hình.
    9.  Volumes và Networks:
        -   Volumes cho phép bạn lưu trữ và quản lý dữ liệu liên quan đến container.
        -   Networks cho phép bạn tạo mạng riêng cho các container để chúng có thể giao tiếp với nhau.
    10. Docker Hub và Registries khác: Ngoài Docker Hub, còn nhiều Docker Registry khác như Amazon ECR, Google Container Registry, quản lý images và cho phép bạn chia sẻ images qua các môi trường khác nhau.
    11. Docker Machine: Một công cụ giúp bạn quản lý và cài đặt Docker trên nhiều máy chủ ảo hoặc vật lý.
    12. Docker Plugin: Cho phép bạn mở rộng Docker Engine bằng cách thêm các tính năng, khả năng lưu trữ và mạng từ bên ngoài.
    13. Docker Events: Cho phép theo dõi sự kiện liên quan đến các hoạt động trong Docker Engine như chạy container, xóa container, và nhiều hơn nữa.
    14. Docker Secrets: Cho phép bạn quản lý và sử dụng các thông tin nhạy cảm như mật khẩu, khóa truy cập một cách an toàn.
    15. Docker Healthchecks: Cho phép bạn kiểm tra tình trạng của container và ứng dụng bên trong để tự động phát hiện và khắc phục sự cố.
    16. Docker Config: Cho phép bạn quản lý các cấu hình của ứng dụng, giúp bạn tách biệt cấu hình với mã nguồn.
    17. Docker Buildx: Mở rộng khả năng xây dựng image của Docker Engine, cho phép tạo nhiều kiến trúc và các image đa nền tảng.
    18. Docker Desktop: Một ứng dụng giúp bạn sử dụng Docker trên Windows và macOS một cách dễ dàng.
    19. Docker Security: Bao gồm các tính năng và cách để bảo mật các container và images, bao gồm kiểm tra vulnerabilities, quản lý quyền truy cập, mạng riêng và nhiều khía cạnh khác.

2. **Cài đặt và cấu hình:**
   - Cài đặt Docker trên máy tính của bạn (Docker có phiên bản cho Windows, macOS và Linux).
   - Tìm hiểu về Docker Engine, Docker CLI (Command Line Interface).

3. **Các lệnh cơ bản:**
   - Hiểu các lệnh cơ bản như `docker run`, `docker pull`, `docker build`, `docker images`, `docker ps`, `docker stop`, `docker rm`,...

   Dưới đây là một số lệnh cơ bản trong Docker mà bạn nên biết:
    1.  docker run
        -   Dùng để chạy một container từ một image.
        -   Ví dụ: `docker run -d --name mycontainer ngnix` (chạy một container từ image "ngnix" và đặt tên là "mycontainer")
    2.  docker pull
        -   Dùng để tải về một image từ một kho lưu trữ (responsitory) như Docker Hub.
        -   Ví dụ: `docker pull ngnix` (tải về image ngnix từ kho lưu trữ mặc định).
    3.  docker build:
        -   Dùng để xây dựng một image mới từ một Dockerfile.
        -   Ví dụ: docker build -t myapp . (xây dựng một image từ Dockerfile trong thư mục hiện tại và đặt tên là "myapp").
    4.  docker images:
        -   Liệt kê tất cả các image đã tải về hoặc đã xây dựng trên máy bạn.
        -   Ví dụ: `docker images` (liệt kê danh sách các image trên máy).
    5.  docker ps:
        -   Liệt kê tất cả các container đang chạy.
        -   Ví dụ: `docker ps` (liệt kê danh sách các container đang chạy).
    6.  docker stop:
        -   Dừng một container đang chạy.
        -   Ví dụ: `docker stop mycontainer` (dừng container có tên là "mycontainer").
    7.  docker rm:
        -   Xóa một container đã dừng.
        -   Ví dụ: `docker rm mycontainer` (xóa container có tên là "mycontainer").
    8.  docker rmi:
        -   Xóa một image đã tải về hoặc xây dựng trên máy bạn.
        -   Ví dụ: `docker rmi myapp` (xóa image có tên là "myapp").
    9.  docker exec:
        -   Chạy một lệnh trong một container đang chạy.
        -   Ví dụ: `docker exec -it mycontainer sh` (chạy một phiên làm việc tương tác trong container có tên "mycontainer").
    10. docker logs:
        -   Hiển thị logs của một container đang chạy.
        -   Ví dụ: `docker logs mycontainer` (hiển thị logs của container có tên "mycontainer").
    11. docker network:
        -   Quản lý mạng cho các container.
        -   Ví dụ: docker network create mynetwork (tạo một mạng có tên "mynetwork").
    12. docker volume:
        -   Quản lý lưu trữ dữ liệu cho các container.
        -   Ví dụ: docker volume create myvolume (tạo một volume có tên "myvolume").
    13. docker-compose:
        -   Quản lý nhiều dịch vụ và container trong một tệp cấu hình duy nhất.
        -   Ví dụ: docker-compose up -d (khởi động các dịch vụ từ tệp docker-compose.yml).
    14. docker inspect:
        -   Hiển thị thông tin chi tiết về một container hoặc image
        -   Ví dụ: docker inspect mycontainer (hiển thị thông tin chi tiết về container "mycontainer").
    15. docker attach:
        -   Gắn kết vào một container đang chạy để thực hiện các lệnh tương tác.
        -   Ví dụ: docker attach mycontainer (gắn kết vào container "mycontainer").
    16. docker cp:
        -   Sao chép tệp và thư mục giữa máy chủ và container.
        -   Ví dụ: docker cp mycontainer:/app/file.txt . (sao chép tệp từ container vào thư mục hiện tại trên máy chủ).
    17. docker top
        -   Hiển thị các quá trình đang chạy trong container.
        -   Ví dụ: docker top mycontainer (hiển thị các quá trình trong container "mycontainer").
    18. docker stats:
        -   Hiển thị thông tin về tài nguyên sử dụng của các container đang chạy.
        -   Ví dụ: docker stats (hiển thị thông tin về tài nguyên sử dụng của các container).
    19. docker commit:
        -   Tạo một image mới từ trạng thái hiện tại của một container.
        -   Ví dụ: docker commit mycontainer myimage (tạo image mới từ container "mycontainer").

4. **Dockerfile và Build Image:**
    - Tìm hiểu về Dockerfile - một tập tin văn bản chứa chỉ thị để xây dựng một image.
        -   Dockerfile là một tập tin văn bản đơn giản chứa các chỉ thị và hướng dẫn cần thiết để xây dựng một image Docker. Dockerfile mô tả cách mà image nên được xây dựng, bao gồm mã nguồn, thư viện, biến môi trường, và cấu hình. Khi bạn chạy lệnh docker build và cung cấp Dockerfile, Docker sẽ thực hiện các bước trong Dockerfile để tạo ra một image cuối cùng.
    - Học cách viết Dockerfile để xây dựng một image cho ứng dụng của bạn.
    ```
        # Sử dụng image cơ sở
        FROM ubuntu:lastest

        # Đặt thông tin tác giả
        LABEL maintainer="your-email@example.com"

        # Cài đặt các gói phần mềm
        RUN apt-get update && apt-get install -y nginx

        # Sao chép tệp cấu hình vào container
        COPY nginx.conf /etc/nginx/nginx.conf

        # Mở cổng
        EXPOSE 80

        # Chạy lệnh khi container khởi động.
        CMD ["ngnix", "-g", "daemon off;"]
    ```
    -   `FROM`: Chọn image cơ sở để xây dựng trên. Ở đây, chúng ta chọn `ubuntu:latest`.
    -   `LABEL`: Thêm các nhãn metadata như thông tin tác giả hoặc liên hệ.
    -   `RUN`: Thực hiện các lệnh trong quá trình xây dựng image. Ở đây, chúng ta cài đặt nginx.
    -   `COPY`: Sao chép tệp cấu hình từ máy chủ vào container.
    -   `EXPOSE`: Mở cổng trên container để có thể truy cập từ bên ngoài.
    -   `CMD`: Xác định lệnh mà container nên thực thi khi khởi động.

    Các thành phần trong dockerfile:
    1.  FROM:
        -   Chọn image cơ sở để xây dựng trên.
        -   Ví dụ: FROM ubuntu:latest (sử dụng image Ubuntu làm cơ sở).
    2.  LABEL:
        -   Thêm các nhãn metadata vào image để cung cấp thông tin bổ sung.
        -   Ví dụ: LABEL maintainer="your-email@example.com".
    3.  RUN:
        -   Thực hiện các lệnh trong quá trình xây dựng image.
        -   Ví dụ: RUN apt-get update && apt-get install -y nginx (cài đặt Nginx).
    4.  COPY và ADD:
        -   COPY: Sao chép tệp từ máy tính của bạn vào container.
        -   ADD: Tương tự như COPY, nhưng hỗ trợ nhiều tính năng hơn.
        -   Ví dụ: COPY app.py /app/ (sao chép tệp app.py từ thư mục máy tính vào thư mục /app/ trong container).
    5.  WORKDIR:
        -   Xác định thư mục làm việc cho các lệnh sau đó.
        -   Ví dụ: WORKDIR /app (đặt thư mục làm việc thành /app/).
    6.  ENV:
        -   Định nghĩa biến môi trường.
        -   Ví dụ: ENV MY_VARIABLE=value (định nghĩa biến môi trường MY_VARIABLE).
    7.  EXPOSE:
        -   Mở cổng trên container để có thể truy cập từ bên ngoài.
        -   Ví dụ: EXPOSE 80 (mở cổng 80 trên container).
    8.  CMD và ENTRYPOINT:
        -   CMD: Xác định lệnh mà container nên thực thi khi khởi động. Thường được ghi đè bởi lệnh khi chạy container.
        -   ENTRYPOINT: Tương tự như CMD, nhưng không thể bị ghi đè bởi lệnh khi chạy container.
        -   Ví dụ: CMD ["nginx", "-g", "daemon off;"].
    9.  VOLUME:
        -   Định nghĩa một hoặc nhiều thư mục trong container có thể lưu trữ dữ liệu liên quan đến container.
        -   Ví dụ: VOLUME /data (định nghĩa thư mục /data có thể được dùng để lưu trữ dữ liệu).
    10. USER:
        -   Xác định người dùng mặc định cho các lệnh RUN, CMD và ENTRYPOINT trong Dockerfile.
        -   Ví dụ: USER myuser (sử dụng người dùng myuser cho các lệnh tiếp theo).

5. **Docker Compose:**
   - Tìm hiểu về Docker Compose để định nghĩa và chạy các dịch vụ ứng dụng cùng lúc (ví dụ: cơ sở dữ liệu, máy chủ web, cache, ...).

6. **Lưu trữ Images:**
   - Tìm hiểu về các kho lưu trữ như Docker Hub, Amazon ECR, Google Container Registry để lưu trữ và chia sẻ images.

7. **Kết hợp Docker với ứng dụng thực tế:**
   - Áp dụng kiến thức Docker vào việc đóng gói và triển khai ứng dụng cụ thể mà bạn đang phát triển.

8. **Mạng và Lưu trữ dữ liệu:**
   - Tìm hiểu về cách Docker quản lý mạng và lưu trữ dữ liệu cho các container.

9. **Bảo mật và Tối ưu hóa:**
   - Học cách đảm bảo bảo mật cho các container và image.
   - Tìm hiểu về các cách để tối ưu hóa việc sử dụng Docker, tối thiểu hóa kích thước của images, ...

10. **Thực hành và Dự án:**
    - Xây dựng một dự án thực tế sử dụng Docker để làm quen với việc triển khai, quản lý và phát triển ứng dụng.

Docker là một kỹ năng quan trọng trong việc phát triển và triển khai ứng dụng hiện nay. Hi vọng lộ trình trên sẽ giúp bạn bắt đầu học về Docker một cách có hệ thống và hiệu quả.