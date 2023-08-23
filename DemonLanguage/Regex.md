# Regex
  
 Là các mẫu (pattern) để làm việc với chuối ký tự ví dụ như tìm chuỗi con, kiểm tra tính hợp lệ của chuỗi.

![Regular Expression shorthand][Regex-ShortHand]

# Cú pháp

## Lặp

|Ký tự  |Ý nghĩa                                      |Ví dụ    |Giải thích									   |
|-------|---------------------------------------------|---------|----------------------------------------------|
|`.`	|Bất kỳ ký tự nào ngoại trừ xuống dòng		  |`.uck`	|Có thể là duck, luck, cuck, ...			   |
|`*`	|Ký tự trước đó xuất hiện 0 hoặc nhiều lần	  |`Yo*h`	|Có thể là Yh, Yoh, Yooh, Yoooh, ...		   |
|`+`	|Ký tự trước đó xuất hiện 1 hoặc nhiều lần	  |`Yo+h`	|Có thể là Yoh, Yooh, Yoooh, ... . Ngoại trừ Yh|
|`?`	|Ký tự trước đó xuất hiện 0 hoặc 1 lần		  |`Yo?h`	|Chỉ có Yh và Yoh 							   |
|`{n}`	|Ký tự trước đó xuất hiện n lần				  |`Yo{3}h`	|Chỉ có Yoooh 								   |
|`{n,m}`|Ký tự trước đó xuất hiện n-m lần			  |`Yo{3,5}`|Chỉ có Yoooh, Yooooh và Yoooooh 			   |
|`{n,}` |Ký tự trước đó xuất hiện n tới không giới hạn|`Yo{3,5}`|Chỉ có Yoooh, Yooooh và Yoooooh 			   |

 Lưu ý: Sử dụng `\` để yêu cầu có dấu chấm. Ví dụ `.com` sẽ nhận ?com, @com, ... nhưng `\.com` sẽ chỉ nhận .com (Dùng khi kiểm tra hợp lệ đường dẫn).

 Tương đương:
 - `*` là gắn gọn của `{0,}`
 - `+` là gắn gọn của `{1,}`
 - `?` là gắn gọn của `{0,1}`

## Khớp nhóm

|Ký tự	|Ý nghĩa																   |Ví dụ |Giải thích			  |
|-------|--------------------------------------------------------------------------|------|-----------------------|
|`^`	|Ứng với vị trí bắt đầu của chuỗi										   |	  |Đúng khi bắt đầu chuỗi |
|`$`	|Ứng với vị trí kết thúc của chuỗi hoặc trước dấu xuống dòng tại cuối chuỗi|	  |Đúng khi kết thúc chuỗi|
|&vert;|Giống phép OR															   |A&vert;B|Hoặc là A hoặc là B 	  |
|`(...)`|Khớp với 1 nhóm ký tự đồng thời nhớ kết quả khớp						   |(e&vert;m)mail|Khớp với email hoặc gmail|
|`(?:.)`|Khớp với 1 nhóm ký tự và không nhớ kết quả khớp (non-capturing version)   |	   |					  |
|`(?=)` |Khớp theo điều kiện													   |x(?=y) |x khớp khi sau x là y |
|`(?!)` |Khớp theo điều kiện													   |x(?!y) |x khớp khi sau x không phải là y|


```python
import re
# python
def test_pattern(pattern, string):

    try:
        matchs = re.search(pattern, string)
        if matchs:
            name = f"{matchs.group(3)} {matchs.group(2)} {matchs.group(1)}"
            print(name)
            # print(f"If you wonder what is group[0]: {matchs.group(0)}")
    except IndexError:
        # Because (?:) is non capturning, we don't have group(3)
        print("(?:) is non-capturing")


name = input("What's your fullname? ").strip()

pat1 = r"^(.+) (.+) (.+)$"
print(f"Test with pattern is {pat1}")
test_pattern(pat1, name)

pat2 = r"^(.+) (?:.+) (.+)$"
print(f"Test with pattern is {pat2}")
test_pattern(pat2, name)
```

## Tập

|Ký tự|Ý nghĩa						|Ví dụ					       						|Giải thích	|
|-----|-----------------------------|---------------------------------------------------|-----------|
|`[]` |Xác định tập ký tự khớp		|`[a-z]` Khớp với 1 ký tự từ a tới z thường			|			|
|     |								|`[A-Z]` Khớp với 1 ký tự A tới Z hoa				|			|
|     |								|`[0-9]` Khớp với 1 ký tự 0 tới 9					|			|
|     |								|`[!@3a ]` Khớp với 1 ký tự !, @, 3, a và dấu cách	|			|
|`[^]`|Xác định tập ký tự không khớp|Ngược lại với `[]`									|			|

 Lưu ý: Kết hợp `[]` với `{}` để tạo ra khớp đa ký tự.

 ## Ký tự thường

|Ký tự|Ý nghĩa									  |Ví dụ|Giải thích					|
|-----|-------------------------------------------|-----|---------------------------|
|`\d` |Các chữ số từ 0-9						  |		|Tương đương `[0-9]`		|
|`\D` |Không phải là chữ số 0-9					  |		|Tương đương `[^0-9]`		|
|`\s` |Ký tự khoảng trống (dấu cách)			  |		|Tương đương `[ ]`			|
|`\S` |Không phải là ký tự khoảng trống (dấu cách)|		|Tương đương `[^ ]`			|
|`\w` |Ký tự chữ cái, số và _					  |		|Tương đương `[a-zA-Z0-9_]`	|
|`\W` |Không phải là ký tự chữ cái, số và _		  |		|Tương đương `[^a-zA-Z0-9_]`|

# Tham khảo và thực hành

[Bài viết](https://topdev.vn/blog/regex-la-gi/)

[Video](https://www.youtube.com/watch?v=nLRL_NcnK-4&t=30771s)

[Thực hành](https://regex101.com/)

[Regex-ShortHand]: img/RegexMeme.jpg "Regular Expression shorthand"