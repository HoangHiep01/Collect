# Kill Chain

 Là một thuật ngữ từ quân đội, mô tả, giải thích các giai đoạn của quá trình của cuộc tấn công. Mục tiêu là để hiểu Kill Chain của kẻ tấn công, từ đó đưa ra các phương pháp bảo vệ, phòng thủ

# Threat Modelling

 Trong cybersecurity,**Threat Modelling** là một loạt các bước để cuối cùng cải thiện tính bảo mật của hệ thống. Threat modelling là việc xác định rủi do và tập trung vào:

 + Xác định hệ thống và ứng dụng nào cần tăng độ bảo mật và chúng có chức năng gì trong môi trường.

 + Xác định điểm yếu, lỗ hổng có thể có của hệ thống và ứng dụng và cách chúng bị khai thác.

 + Lên kế hoạch để bảo vệ các hệ thống và ứng dụng này khỏi các lỗ hổng được xác định.

 + Đưa ra các nguyên tắc phòng trách lỗ hỏng có thể bị khai thác.

 **Threat Modelling** một quy trình quan trọng để giảm rủi ro trong một hệ thống hoặc ứng dụng, vì nó tạo ra một cái nhìn tổng quan về tài sản(phần cứng và phần mền) của một tổ chức.

 STRIDE, DREAD và CVSS ... là những framework được dùng cho threat modelling

# Unified Kill Chain

 Unified Kill Chain được công bố vào năm 2017, nhằm mục đích bổ sung (không cạnh tranh) với các cybersecurity kill chain frameworks khác như ATT&CK của Lockheed Martin và MITRE.

 UKC xác định một cuộc tấn công gồm 18 giai đoạn: từ reconnaissance tới data exfiltration và tìm hiểu động cơ của kẻ tấn công. 

 Điểm nổi bật của UKC là nó bắt kịp những gì đang diễn ra (update2022) và cực kỳ chi tiết. Mô hình xác định các giai đoạn khác nhau có thể tái diễn.

![UCK][UCK]

# IN (Initial Foothold)

 Trọng tâm chính của giai đoạn này là kẻ tấn công giành được quyền truy cập vào hệ thống hay môi trường mạng (gôm cả việc tạo tiền đề để tái truy cập).

![IN][IN]

## Reconnaissance (MITRE Tactic TA0043)

 Giai đoạn này mô tả về các kỹ thuật mà kẻ tấn công dùng để thu thập thông tin liên quan đến mục tiêu. Các thông tin này có thể dùng trong suốt các giai đoạn khác.

 Thông tin thu thập được có thể bao gồm:

 + Thông tin về hệ thống và dịch vụ.

 + Danh sách mục tiêu có thể tấn công social engineering hay phishing attack.

 + Thông tin đăng nhập tiềm năng.

 + Thông tin về kiểu mạng, hệ thống mạng.

## Weaponization (MITRE Tactic TA0001)

 Giai đoạn này mô tả kẻ tấn công chuẩn những thứ cần thiết để thực hiện tấn công.

## Social Engineering (MITRE Tactic TA0001)

 Giai đoạn này mô tả kẻ tấn lợi dụng, thao túng tâm lý để lấy thông tin nhạy cảm, bí mật từ nạn nhân.

## Exploitation (MITRE Tactic TA0002)

 Giai đoạn mô tả cách kẻ tấn công lợi dụng điểm yếu hoặc lỗ hổng có trong hệ thống. UKC định nghĩa "Exploitation" là lạm dụng các lỗ hổng để thực hiện mã.

## Persistence (MITRE Tactic TA0003)

 Giai đoạn này mô tả các kỹ thuật mà kẻ tấn công sử dụng để duy trì quyền truy cập vào hệ thống mà chúng đã truy cập trước đó.

## Defence Evasion (MITRE Tactic TA0005)

 Giai đoạn này nói về các kỹ thuật mà kẻ tấn công tránh, vượt qua biện pháp phòng thủ được áp dụng.

 Giai đoạn này rất có giá trị khi phân tích một cuộc tấn công vì nó giúp hình thành cách phản ứng và cải thiện ứng phó - cung cấp cho đội phòng thủ thông tin về cách họ có thể cải thiện hệ thống phòng thủ của mình trong tương lai.

## Command & Control (MITRE Tactic TA0011)

 Ở giai đoạn này, kẻ tấn công cố gắng thực hiện kết nối tới mục tiêu và kiểm soát chúng.

## Pivoting (MITRE Tactic TA0008)

 Là kỹ thuật mà kẻ tấn công sử dụng để tiếp cận các hệ thống khác trong mạng mà không thể truy cập được - đó thường chứa dữ liệu có giá trị hoặc có bảo mật yếu hơn.

# Through (Network Propagation)

 Phần này bắt đầu sau khi kẻ tấn công xâm nhập được vào hệ thống. Kẻ tấn công sẽ tìm cách giành thêm quyền truy cập và đặc quyền đối với hệ thống và dữ liệu để thực hiện mục tiêu của chúng. 

![Through][THROUGH]

## Pivoting (MITRE Tactic TA0008)

 Sau khi thâm nhập được vào hệ thống, kẻ tấn công sẽ dựng nên một kết nối với mạng của nạn nhân để có thể tải lên malware hoặc backdoor.

## Discovery (MITRE Tactic TA0007)

 Kẻ tấn công tìm ra được thông tin về mạng và hệ thống.

## Privilege Escalation (MITRE Tactic TA0004)

 Sau khi thu thập thông tin, kẻ tấn công sẽ dùng mọi cách để nâng quyền trong hệ thống.

 Một số quyền cấp cao như:

 + SYSTEM/ROOT.

 + Local Administrator.

 + A user account with Admin-like access.

 + A user account with specific access or functions.

## Execution (MITRE Tactic TA0002)

 Đẩy thêm mã độc để duy trì. (???)

## Credential Access (MITRE Tactic TA0006)

 Kết hợp với quá trình Privilege Escalation, kẻ tấn công thực hiện việc đánh cắp thông tin đăng nhập.

## Lateral Movement (MITRE Tactic TA0008)

 Với thông tin đăng nhặp và đặc quyền đặt được, kẻ tấn công sẽ di chuyển tới mạng hay hệ thống khác nhằm đạt được mục tiêu cuối cùng. Kỹ thuật các lén lút thì càng tốt.

# Out (Action on Objectives)

 Đây là giai đoạn kết thúc quá trình tấn công.

## Collection MITRE Tactic (TA0009)

 Sau khi quá trình tấn công và đặt được quyền truy cập, kẻ tấn công sẽ thu thập toàn bộ thông tin có thể. Điều này gây tổn hại đến dữ liệu và dẫn tới quá trình tiếp theo.

## Exfiltration (MITRE Tactic TA0010)

 Các dữ liệu bị lấy cắp sẽ được nén và mã hóa để tránh phát hiện khi bị lấy đi. Các kết nối được thiết lập từ các bước trước sẽ có ích trong bước này.

## Impact (MITRE Tactic TA0040)

 Nếu kẻ tấn công muốn xâm phạm tính integrity và availability dữ liệu, chúng sẽ phá hủy hoặc làm gián đoạn hệ thống.

## Objectives

 Với quyền truy cập và khả năng của mình, kẻ tấn công có thể làm một số việc để đặt được mục tiêu của mình như: tống tiền dữ liệu, công bố dữ liệu bí mật, ... .

 

















[UCK]: https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/2b7d1d80745f42112e9572dcdcd30284.png "The Unified Kill Chain"

[IN]: https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/9f902ef203a9aacb47ee847d7b3051d6.png "IN"

[THROUGH]: https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/5adc12d43ac2b82857b4c5b78f0c2579.png "THROUGH"