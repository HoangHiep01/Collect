# Reconnaissance (Trinh sát)
 
 Tìm và thu thập thông tin trong hệ thống và nạn nhân. Đây là gian đoạn lên kế hoạch.

 OSINT (Open-Source Intelligence) có thể thực hiện trong giai đoạn này. Kẻ tấn công sẽ thực hiện thu thập tất cả thông tin có thể về nạn nhân từ các nguồn miễn phí, công khai. Có thể khai thác thông tin trên các trang mạng xã hội, ... hay là từ các cụng chuyên biệt.

# Weaponization (Vũ khí hóa ???)
 
 Sau khi thu thập tất cả thông tin có thể, tiêp theo là tạo ra công cụng tấn công nạn nhân. Phối kết hợp **malware** và **exploit** để tạo ra **payload**. Đa số kẻ tấn công sẽ sử dụng tool để tạo malware hoặc mua trên [DarkWeb](https://www.kaspersky.com/resource-center/threats/deep-web). Còn có các đối tượng tấn công phức tạp có thể tự tạo malware tùy chỉnh với nạn nhân (độc nhất và khó phát hiện).

 Một vài định nghĩa:

 + **Malware** là chương trình hoặc phần mềm được thiết để tấn công, phá hủy hoặc truy cập trái phép vào máy tính.

 + **Exploit** là chương trình hoặc đoạn code dùng để khai thác, sử dụng các lỗ hổng trong ứng dụng, hệ thống.

 + **Payload** mã độc chạy trên hệ thống.

 Trong giai đoạn này, kẻ tấn công có thể lựa chọn:

 + Tạo tài liệu Microsoft Office có chứa Macro độc hại hoặc VBA(Visual Basic for Applications) scripts. Tìm hiểu thêm về [Marco và VBA](trustedsec.com/blog/intro-to-macros-and-vba-for-script-kiddies/).

 + Tạo payload hay worm rồi đem vào một thiết bị như USB và đưa ra bên ngoài.

 + Thực hiện kỹ thuật tấn công Command and Control (C2) để có thể thực hiện các lệnh hoặc tải lên các payload khác. [C2 technique](https://attack.mitre.org/tactics/TA0011/).

 + Tạo backdoor.

# Delivery (Truyền)

 Lựa chọn phương thức truyền đi payload.

 + Phishing email: Giả danh mail.

 + Phân phát USB chứa mã độc.

 + Watering hole attack (???).

# Exploitation (Khai thác lỗ hổng)

 Để có quyền truy cập vào hệ thống, những kẻ tấn công thường lợi dụng các lỗ hổng, điểm yếu. Sau khi vào được hệ thống, kẻ tấn công có thể khai thác lỗi hổng phần mềm, hệ thống hay leo thang đặc quyền hoặc vào sâu trong mạng để lấy dữ liệu nhạy cảm.

 Zero-day Exploit: những lỗ hổng phần mềm hoặc phần cứng chưa được biết đến và khó có cơ hội phát hiện từ ban đầu, có thể gây ra những vấn đề phức tạp trước khi người sở hữu hay người cung cấp sản phẩm nhận ra.

 Ví dụ về cách kẻ tấn công khai thác lỗ hổng:

 + Nạn nhân tạo nên lỗ hổng khi mở đính kèm mail hoặc đường dẫn độc hại.

 + Sử dụng zero-day exploit (chợ đen).

 + Khai thác lỗ hổng từ phần mềm, phần cứng, thậm chí là cả con người.

 + Khai thác lỗ hổng trên máy chủ.

# Installation (Cài đặt)

 Ở phần Weaponization, backdoor đã được nhắc tới - đây như là một điểm truy cập giúp kẻ tấn công có thể vượt qua được các biến pháp bảo mật và ẩn việc truy cập.

 Sau khi kẻ tấn công có quyền truy cập vào hệ thống, họ sẽ muốn truy cập lại nhưng nếu mất kết nối với hệ thống hoặc bị phát hiện và bị xóa quyền truy cập ban đầu hoặc nếu hệ thống được vá lỗi sau đó. Kẻ tấn công sẽ không còn có quyền truy cập nữa. Khi đó, kẻ tấn công cần cài đặt **persistent backdoor**.

 Có vài cách để cài được persistent backdoor:

 + Cài đặt webshell lên máy chủ.

 + Cài đặt backdoor lên máy nạn nhân, có thể dùng [meterpreter](https://www.offsec.com/metasploit-unleashed/meterpreter-backdoor/).

 + Tạo hoặc sửa đổi các dịch vụ Windows. Kỹ thuật này được gọi là [T1543.003](https://attack.mitre.org/techniques/T1543/003/) trên MITRE ATT&CK.

 + Thêm các cổng vào "run keys" cho payload tại Registry hoặc Startup Folder. [Đọc thêm](https://attack.mitre.org/techniques/T1547/001/).

 Kẻ tấn công có thẻ sử dụng kỹ thuật [timestomping](https://attack.mitre.org/techniques/T1070/006/) để tránh khỏi **forensic investigator** và cũng làm cho malware trông như một chương trình hợp lệ. Kỹ thuật này giúp kẻ tấn công chỉnh sửa **file's timestamps** bao gồm: modify, access, create and change times.

# Command and Control (Kiểm soát truy cập từ xa)

 Sau khi cài được **persistence** và thực thi malware trên máy của nạn nhân, kẻ tấn công có thể khởi tạo kết nối từ malware với máy chủ kiểm soát từ xa. Từ đó, kẻ tấn công nắm toàn quyền kiểm soát máy của nạn nhân. Cho đến hiện nay, IRC (Internet Relay Chat) là kênh C2 được sử dụng bởi những kẻ tấn công. Điều này không còn nữa, vì các giải pháp bảo mật hiện đại có thể dễ dàng phát hiện lưu lượng truy cập IRC độc hại.

 Các kênh C2 phổ biến:

 + Giao thức HTTP trên cổng 80 và HTTPS trên cổng 443 - trộn lưu lượng độc hại với lưu lượng hợp pháp và có thể giúp kẻ tấn công trốn tránh tường lửa.

 + DNS: máy của nạn nhận tạo DNS request đến DNS của kẻ tấn, phương pháp kết nối này còn được gọi là DNS Tunneling.

# Actions on Objectives (Exfiltration)

 Sau các quá trình trên, kẻ tấn công giờ có thể:

 + Thu thập thông tin người dùng.

 + Leo thang đặc quyền (lấy quyền quản trị viên từ những cấu hình sai).

 + Theo dõi các thông tin nội bộ.

 + Đi sâu hơn vào mạng nội bộ.

 + Thu thập thông tin nhạy cảm.

 + Xóa hoặc chỉnh sửa dữ liệu.

# Conclusion (Tổng kết)

 Traditional Cyber Kill Chain được thiết kế để bảo vệ tăng bảo vệ mạng và phòng chống các phần mềm độc hại. Lần sửa đổi cuối của mô hình này cách đây khá lâu và những kẻ tấn công hiện tại lại áp dụng kết hợp nhiều loại TTP (tactics, techniques, and procedures). Ngoài ra, mô hình không có khả năng phát hiện **Insider Threats**.

 Tìm hiểu thêm từ [ATT&CK](https://attack.mitre.org/) cũng như [**THE UNIFIED KILL CHAIN**](https://unifiedkillchain.com/).