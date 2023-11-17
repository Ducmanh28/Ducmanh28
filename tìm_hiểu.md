# Tìm hiểu tổng quan về mô hình `OSI` VÀ `TCP/IP`
## 1.Mô hình `TCP/IP` 
### 1.1 Mô hình `TCP/IP` là gì?
- `TCP` (Transmission Control Protocol) chia nhỏ dữ liệu ra thành những gói và đảm bảo việc truyền dữ liệu thành công
- `IP` (Internet Protocol) định tuyến (route) các gói dữ liệu khi chúng được truyền qua mạng, đảm bảo dữ liệu sẽ đến đúng nơi cần nhận
- `TCP/IP` hay (Transmission Control Protocol/Internet Protocol) là một giao thức điều khiển truyền nhận
- Là giao thức liên mạng được sử dụng để kết nối các thiết bị mạng với nhau trong môi trường internet
- Cũng được sử dụng như một giao thức truyền thông bên trong mạng máy tính riêng
- Hoạt động như một lớp trừu tượng giữa các ứng dụng Internet và hạ tầng thiết bị đầu cuối. Nghĩa là: `TCP/IP` che dấu tất cả các chi tiết về việc truyền tải dữ liệu qua mạng, bao gồm việc định tuyến dữ liệu, xử lý lỗi, kiểm soát tốc độ truyền và nhận dữ liệu,...  ⇒ nhằm mục đích giúp đơn giản hóa quá trình phát triển ứng dụng, tạo ra 1 giao diện chuẩn cho các ứng dụng để giao tiếp với nhau

### 1.2 Tổng quan về các tầng trong mô hình `TCP/IP`
TCP/IP gồm có 4 tầng xếp chồng lên nhau theo thứ tự: **Network Access** (Tầng vật lý) → **Network** (Tầng mạng) → **Transport** (Tầng giao vận) → **Application** (Tần ứng dụng), sau đây là một vài thông tin cơ bản về các tầng: 
#### 1.2.1. Tầng Vật Lý
- Là tầng thấp nhất trong mô hình `TCP/IP`
- Chịu trách nghiệm truyền dữ liệu giữa các thiết bị trong cùng 1 mạng. Tại đây, các gói dữ liệu được đóng vào khung (Frame) và được định tuyến đi đến đích được chỉ định ban đầu
- Đơn vị đo của tầng này là ‘**Frame**’ - dung lượng một khối dữ liệu nhỏ
#### 1.2.2. Tầng Mạng
- Là tầng xử lý quá trình truyền gói tin trên mạng
- Dữ liệu được phân thành các đoạn nhỏ để truyền đi. Mỗi đoạn có thể không bằng nhau về kích thước nhưng phải nhỏ hơn 64kb
    - Lý do: để đảm bảo hiệu suất và độ tin cậy của quá trình truyền tin
- Chức năng quan trọng nhất của tầng này là làm nhiệm vụ định tuyến và dẫn đường cho tệp tin đi đúng hướng
- Đơn vị đo của tầng này là ‘**Packets**’ - hay còn gọi là 1 gói tin. '**Packets**' chứa các thông tin gồm header chứa các thông tin đến việc định tuyến và xử lý giao tiếp còn payload chứa dữ liệu
#### 1.2.3. Tầng giao vận
- Hoạt động nhờ 2 giao thức chính là `TCP` và `UDP` (User Datagram Protocol). Hai giao thức này hỗ trợ nhau trong việc phân luồng dữ liệu
- `TCP` mất nhiều thời gian để đảm bảo độ an toàn nhưng không ổn về hiệu suất 
- `UDP` có  thời gian vận chuyển nhanh nhung lại không đảm bảo về độ an toàn
- Đơn vị đo lường của tầng này là ‘**Segment**’ - tương tự như ‘**Packets**’ nó cũng gồm 2 phần: Header chứa các thông tin như số thứ tự (**SQE**), cờ điều khiển, kích thước cửa sổ trượt và check lỗi. Còn lại Payload chứa dữ liệu cần truyền đi
#### 1.2.4. Tầng ứng dụng
- Cung cấp giao tiếp đến người dùng
- Cung cấp các ứng dụng cho phép người dùng trao đổi dữ liệu ứng dụng thông qua các dịch vụ mạng khác nhau (duyệt web, chat, gửi email, …)
- Dữ liệu khi tới tầng này sẽ được định dạng theo kiểu **byte nối byte**, cùng với đó là các thông tin định tuyến giúp xác định hướng đi đúng của 1 gói tin 
### 1.3 Cách mà mô hình `TCP/IP` hoạt động
- Dữ liệu được gửi từ tầng **Application** xuống các ngăn xếp
- Tại nơi gửi dữ liệu, mỗi tầng sẽ coi gói tin của tầng trên như là của nó và thực hiện thêm vào gói tin đó các thông tin điều khiển sau đó chuyển tiếp xuống tầng dưới
- Tại nơi nhận dữ liệu, quá trình này diễn ra ngược lại, mỗi tầng thực hiện tách thông tin điều khiển của mình ra rồi chuyển dữ liệu lên tầng trên
### 1.4 Ưu điểm của mô hình `TCP/IP`
- Là mô hình tự do, không chịu sự kiểm soát của bất kỳ tổ chức nào trên thế giới → giúp tạo điều kiện cho sự phát triển và đổi mới
- Có khả năng tương thích cao với tất cả các hệ điều hành, phần cứng máy tính và mạng→Có thể hoạt động trên hầu hết các loại hệ thống và thiết bị, từ máy tính cá nhân đến máy chủ
- Có khả năng mở rộng cao với cấu trúc ***server-client***→Hỗ trợ một lượng lớn thiết bị và người dùng cùng 1 lúc

⇒ Xuất phát từ thiết kế và cấu trúc của mô hình. Mô hình này được thiết kế để làm việc với 1 loạt các giao thức và dịch vụ mạng 
### 1.5 Nhược điểm của mô hình `TCP/IP`
- Cài đặt phức tạp, khó quản lý
- Tầng `Transport` không đảm bảo phân phối các gói tin
- Những giao thức ở trong mô hình rất khó thay thế 
- Không có sự tách biệt rõ ràng giữa những khái niệm về giao diện, dịch vụ và giao thức
Dễ bị tấn công **SYN** - một kiểu tấn công từ chối dịch vụ (*DDoS*)

⇒ Không hiệu quả để mô ta những công nghệ trong mạng mới
### 1.6 Những tìm hiểu thêm về mô hình TCP/IP
#### 1.6.1 Hai giao thức ở tầng `Transport`: TCP và UDP 
##### 1.6.1a. `TCP`(Tranmission Control Protocol) 
- TCP là giao thức nằm trong tầng `Transport` của mô hình `TCP/IP`
- Cung cấp cơ chế báo nhận: Khi A gửi dữ liệu cho B, B nhận được thì gói tin cho A thì xác nhận là đã nhận. Nếu B không nhận được thì A sẽ gửi lại đến khi B nhận được thì thôi
- Cung cấp cơ chế đánh số thứ tự gói tin cho các đơn vị dữ liệu, sử dụng để ráp các gói tin chính xác ở điểm nhận và lọc các gói tin bị trùng lặp
- Có các cơ chế điều khiển luồng thích hợp giúp tránh tắc nghẽn
- Hỗ trợ cơ chế truyền và nhận cùng một lúc
- Phục hồi dữ liệu truyền bị mất (A gửi mà B không nhận được thì sẽ tự động gửi lại cho đến khi B nhận được)
##### 1.6.1b. `UDP` (User Datagram Protocol)
- Ngược lại với TCP, thì UDP là giao thức connectionless (truyền tải hướng không kết nối) → Không thực hiện thiết lập kết nối trước mà thực hiện truyền ngay khi có dữ liệu⇒ truyền tải rất nhanh cho dữ liệu của lớp ứng dụng
- Nhưng nó không đảm bảo tính tin cậy khi truyền mà không có cơ chế phục hồi dữ liệu (không quan tâm gói tin có đến đích hay không, không quan tâm việc mất dữ liệu) ⇒ dễ bị lỗi
- Nhanh và hiệu quả đối với những dữ liệu nhỏ, khắt khe về thời gian chuyển 
- Bản chất không trạng thái nên UDP hữu dụng đối với các trả lời truy vấn nhỏ với số lượng người truy cập lớn
##### 1.6.1c. So sánh giống và khác nhau giữa 2 giao thức
- Giống nhau: Đều là các giao thức ở tầng `Transport` của mô hình `TCP/IP`, có chức năng kết nối các máy lại với nhau và truyền dữ liệu cho nhau
- Khác nhau:

|   `TCP/IP`  |        `UDP`        |
|-------------|-------------------|
|Hướng kết nối|Hướng không kết nối|
|Độ tin cậy cao|Độ tin cậy thấp|
|Gửi dữ liệu dạng luồng byte|Gửi dữ liệu dạng datagram|
|Không cho phép mất gói tin|Cho phép mất gói tin|
|Đảm bảo việc truyền dữ liệu|Không đảm bảo việc truyền dữ liệu|
|Có sắp xếp thứ tự các gói tin|Không sắp xếp thứ tự các gói tin|
|Tốc độ truyền thấp hơn UDP|Tốc độ truyền cao|

#### 1.6.2 Một số giao thức phổ biến khác
- `HTTP`(Hyper Text Transfer Protocol): Truyền tải dữ liệu không an toàn giữa **web-client** và **web-server**
- `HTTPS` (Hyper Text Transfer Protocol Secure): Truyền tải dữ liệu an toàn giữa **web-client** và **web-server**
- `FTP` (File Transfer Protocol): Giao thức cho phép người dùng lấy hoặc gửi tệp từ 1 thiết bị khác




