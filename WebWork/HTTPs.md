# Giới thiệu
 HTTP là viết tắt của HyperText Tranfer Protocol - được phát triển bởi Tim Berners-Lee cùng đội ngũ vào giữa nhưng năm 1989 - 1991. HTTP là tập các quy tắc để kết nối với máy chủ để truyền dữ liệu.

 HTTPs (HyperText Tranfer Protocol Secure) là phiên bản bảo mật của HTTP. Dữ liệu truyền đi được mã hóa và đảm bảo dữ liệu được truyền đến đúng đích chứ không phải địa chỉ mạo danh.

# Requests và Responses
 Khi chúng ta truy cập vào một trang web, trình duyệt sẽ tạo một yêu cầu tới máy chủ để truyền tải các tài nguyên, dữ liệu cần thiết. Nhưng trước đó, chúng ta cần xác định cho trình duyệt là truyền tải ở đâu và bằng cách nào. Đây là công việc cho URL.

## URL (Uniform Resource Locator)

 Hình ảnh bên dưới là các thành phần có trong URL (không phải lúc nào dùng tới tất cả các thành phần này).
![URL-structure][URL-structure-img]

 **Scheme:** Xác định giao thức kết nối, có thể là HTTP, HTTPs, FTP (File Transfer Protocol).

 **User:** Khi dịch vụ truy cập yêu cầu xác thực đăng nhập, ta có thể để username và password vào URL để đăng nhập.

 **Host:** Tên miền hoặc địa chỉ IP của máy chủ mà bạn muốn đăng nhập.

 **Port:** Cổng mà bạn muốn kết nối với máy chủ, thường là 80 với HTTP và 443 cho HTTPs nhưng nó có thể là bất cổng nào từ 1 - 65535.

 **Path:** đường dẫn tới tài nguyên bạn muốn truy cập.

 **Query String:** bits mở rộng để có thể gửi đế yêu cầu của đường dẫn. Như ảnh thì bản đang vào view-room có id là 1, có thể có id 2, 3, ... .

 **Fragment:** Ánh xạ tới một vị trí trên trang web. Điều này thường xuất hiện khi trang web khá dài và được tổ chức thành các phần nhỏ hơn.

## Making Resquest
 
 Có thể thực hiện request tới server với 1 dòng lệnh **"GET/HTTP/1.1"**.

 ![Request process][Request-process]

 Nhưng để có trải nghiệm tốt hơn thì cần phải gửi thêm các dữ liệu khác, tổ hợp lại được gọi là HEADER.

### Ví dụ về request

 ```
	GET / HTTP/1.1
	Host: tryhackme.com
	User-Agent: Mozilla/5.0 Firefox/87.0
	Referer: https://tryhackme.com/

 ```
 **Line 1:** Request theo phương thức GET tới trang chủ với '/' và thông báo với máy chủ là chúng ta sử dụng giao thức HTTP ver 1.1.

 **Line 2:** Thông báo với máy chủ là chúng ta muốn tới trang web tryhackme.com.

 **Line 3:** thông báo với máy chủ là chúng ta dùng trình duyệt Firefox ver 87.

 **Line 4:** Thông báo với máy chủ trang web hướng chúng ta tới host.

 **Line 5:** HTTP request luôn kết thúc với một dòng trống.

### Ví dụ về response

```HTML
	
	HTTP/1.1 200 OK
	Server: nginx/1.15.8
	Date: Fri, 09 Apr 2021 13:34:03 GMT
	Content-Type: text/html
	Content-Length: 98

	<html>
		<head>
		    <title>TryHackMe</title>
		</head>
		<body>
		    Welcome To TryHackMe.com
		</body>
	</html>
```
 **Line 1:** Phiên bản giao thức HTTP máy chủ sử dụng và Status Code.

 **Line 2:** Phần mềm máy chủ và phiên bản sử dụng.

 **Line 3:** Ngày, giờ và múi giờ hiện tại của máy chủ.

 **Line 4:** Thông báo loại thông tin nào sẽ được gửi đến, có thể như HTML, ảnh, videos, pdf, XML.

 **Line 5:** Thông báo kích thước thông tin trả về, đơn vị bytes. Bằng thông tin này, chúng ta có thể xác nhận không bị thiếu dữ liệu gửi về.

 **Line 6:** Dòng trống xác kết thúc HTTP response.

 **Lines 7-14** Thông tin trả về.

# Các phương thức HTTP
 
 Phương thức HTTP sẽ xác định việc người dùng muốn làm khi thức hiện request. Có rất nhiều phương thức nhưng chủ yếu hay thấy 4 loại và hai trong đó hay gặp nhất là GET và POST.

 **GET:** lấy dữ liệu từ máy chủ.

 **POST:** gửi dữ liệu lên máy chủ để thêm mới.

 **PUT:** gửi dữ liệu lên máy chủ để cập nhật.

 **DELETE:** xóa dữ liệu trên máy chủ (trong quyền hạn).

# HTTP Status Codes

 Status codes có thể chia thành 5 phạm vi khác nhau.

|Phạm vi|     Phân loại    |Ý nghĩa|
|-------|------------------|-------|
|100-199|Phản hồi thông tin|Xác nhận 1 phần của request đã được chấp nhận và người dùng cần gửi nốt phần còn lại. Hiện tại không còn phổ biến|
|200-299|Thành công|Xác nhận request đã thực hiện thành công|
|300-399|Chuyển hướng|Điều hướng người dùng tới trang, địa chỉ khác|
|400-499|Lỗi máy khách|Thông báo có lỗi với request gửi tới|
|500-599|Lỗi máy chủ|Các lỗi phía máy chủ khi xử lý yêu cầu|

 Một vài Status Code hay gặp.

|Code|Message|              |
|----|-------|--------------|
|200|Ok                     |Request thành công|
|201|Created                |Tài nguyên mới đã được tạo(tạo tài khoản hay đăng bài viết)|
|301|Permanent Redirect     |Chuyển hướng người dùng tới một trang khác|
|302|Temporary Redirect     |Giống 301 nhưng có thể quay lại|
|400|Bad Request            |Có sai hoặc thiếu sót trong request|
|401|Not Authorised         |Thông báo khi truy cập vào tài nguyên mà chưa có danh tính|
|403|Forbidden              |Không có quyền truy cập|
|404|Not Found              |Tài nguyên, trang web, .. không tồn tại
|405|Method Not Allowed     |Sai phương thức request|
|500|Internal Service Error | Máy chủ gặp sự cố với request và không có cách xử lý|
|503|Service Unavailable    |Không thể xử lý request do quá tải hoặc đang bảo trì|

# HEADER

 Là thông tin bổ sung khi gửi request. Không có yêu cầu nghiêm ngặt về header khi tạo request.

## Headers request phổ biến

 Các headers này được gửi từ máy khách hay là từ trình duyệt tới máy chủ.

 **Host:** Xác định trang web khi máy chủ host nhiều web, nếu không sẽ được gửi tới trang web mặc định.

 **User-Agent:** Cung cấp cho máy chủ biết về thông tin trình duyệt để dữ liệu web truyền về phù hợp với trình duyệt.

 **Content-Length:** Cung cấp kích thước dự kiến dữ liệu gửi tới máy chủ để có thêm kiểm tra dữ liệu có được nhận đủ.

 **Accerpt-Encoding:** Thông báo cho máy chủ biết trình duyệt hỗ trợ phương thức nén file nào, để file gửi đi có thể nhỏ hơn.

 **Cookie:** Là những dữ liệu máy chủ gửi về sau lần đầu truy cập trang web. Sau đó được lưu lại trên máy người dùng và trình duyệt gửi lại máy chủ theo các request.

## Headers response phổ biến

 **Set-Cookie:** Dữ liệu cần lưu lại để gửi cùng các request sau.

 **Cache-Control:** Xác định khoảng thời gian tồn tại nội dung của response trong bộ nhớ đệm trình duyệt trước khi được request lại.

 **Content-Type:** Thông báo với máy khách lại dữ liệu được trả về để trình duyệt có thể biết cách xử lý.

 **Content-Encoding:** Xác định phương thức nén dữ liệu được sử dụng.

# Cookies

 Là dữ liệu được lưu lại sau khi nhận header "Set-Cookie" từ máy chủ. Dữ liệu này sẽ được gửi lại theo các request. Cookie có giúp lưu định danh hay các cài đặt cá nhân khi truy cập lại trang web.

![Set Cookie example][Set-Cookie-example]

 Cookie có thể được sử dụng cho nhiều mục đích nhưng thường được sử dụng nhất để xác thực trang web. Cookie thường không phải là một văn bản rõ ràng dễ ràng để đọc mà là một token(bí mật, duy nhất và không dễ đoán được).




 [URL-structure-img]: https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/34ad66d8b90aaaa35f9536d3b152ea97.png "URL structure"

 [Request-process]: https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/09e70200e7af451077081a3ee3d3708c.png "Request process"

 [Set-Cookie-example]: https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/a2117dc267fbb169e38be77c7af44027.png "Set Cookie example"