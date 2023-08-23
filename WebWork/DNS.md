# Giới thiệu
 DNS (Domain Name System)

 Mỗi máy chủ trên internet đều có một địa chỉ IP để thực hiện giao tiếp, kết nối. Địa chỉ IP này là một dãy số rất khó nhớ, DNS có thể khắc phục điều này. Ta có thể dùng `google.com` thay vì `142.250.199.78`

# Phân cấp Domain
![Domain Hierarchy](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/a168c8511887fff98a6944619c4b5259.png)

## Top-Level Domain
  
 Hay ở phía bên phải của domain name.

 Có 2 loại:
  
  * gTLDM (Generic Top Level Domain), trước đó dùng để thể hiện mục đích như .com (commercial), .org (organisation), .edu (education) và .gov (government). Do nhu cầu, nhiều loại gTLDs bắt đầu xuất hiện ([hơn 2000 TLDs](https://data.iana.org/TLD/tlds-alpha-by-domain.txt)).
  * ccTLD (Country Code Top Level Domain), thể hiện về mặt địa lý như .ca (Canada), .co.uk (United Kingdom)

## Second-Level Domain

 Lấy google.com làm ví dụ, .com là TLD và google là SLD. Khi đăng ký tên miền, SLD giới hạn độ dài trong 63 ký tự và chỉ được dùng a-z 0-9 và dấu - (không dùng - ở đầu hoặc cuối hay --).

## Subdomain
 Nằm ở phía bên trái của SLD và được ngăn cách bởi dấu chấm. Quy định đặt tên của subdomain giống với SLD. Ta có thể dùng nhiều subdomain liên tiếp để tăng độ dài nhưng tên miền có độ dài giới hạn là 253 ký tự. Không có giới số lượng subdomain có thể tạo.

# Các loại bản ghi trên DNS

 Có rất nhiều loại bản ghi DNS. Sau đây là một số loại hay gặp.

## A Record
 Phân giải thành IPv4.

## AAAA Record
 Phân giải thành IPv6.

## CNAME Record
 Ánh xạ tên miền này sang tên miền khác.

## MX Record
 Xác định máy chủ mail cho tên miền.

## TXT Record
 Là một dạng file văn bản. TXT records có thể xác định máy chủ có quyền gửi email thay cho miền (chống spam và spoofed email). Cũng có thể xác thực quyền sở hữu tên miền khi sử dụng dịch vụ của bên thứ 3.

# DNS request

![Domain request](https://tryhackme-images.s3.amazonaws.com/user-uploads/5c549500924ec576f953d9fc/room-content/307a490eef750cfe105d4a1e17e9098d.png)

Khá dài và khó hiểu cộng lười nên ...