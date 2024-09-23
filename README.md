# Các lệnh hay dùng


| **Mục** | **Mô tả** | **Cờ/Tùy chọn Quan trọng** | **Ví dụ Sử dụng** |
|---|---|---|---|
| [**chmod**](#chmod) | Thay đổi quyền truy cập cho file/thư mục | `+x` (thêm quyền thực thi), `-r` (gỡ quyền đọc), `+w` (thêm quyền ghi) | `chmod +x file.sh` (Thêm quyền thực thi cho file.sh) |
| [**find**](#find) | Tìm kiếm file trong hệ thống | `-name` (tìm theo tên), `-type` (loại tệp), `-size` (kích thước tệp) | `find / -name "*.txt"` (Tìm tất cả các file .txt trong hệ thống) |
| [**grep**](#grep) | Tìm kiếm mẫu cụ thể trong file hoặc đầu ra lệnh | `-i` (không phân biệt hoa/thường), `-r` (tìm kiếm đệ quy), `-v` (lọc mẫu không khớp) | `grep -i "error" log.txt` (Tìm từ "error" trong file log.txt, không phân biệt hoa/thường) |
| [**nano**](#nano) | Tạo và chỉnh sửa file văn bản | `Ctrl+O` (lưu file), `Ctrl+X` (thoát nano) | `nano myfile.txt` (Mở file myfile.txt để chỉnh sửa) |
| [**wget**](#wget) | Tải file từ internet | `-O` (đặt tên file), `-c` (tiếp tục tải nếu bị gián đoạn) | `wget -O myfile.zip http://example.com/file.zip` (Tải file và lưu tên là myfile.zip) |
| [**scp**](#scp) | Sao chép file an toàn giữa hai máy tính | `-r` (sao chép thư mục đệ quy), `-P` (chỉ định cổng SSH) | `scp file.txt user@remote:/path/to/destination` (Sao chép file.txt từ máy cục bộ đến máy từ xa) |
| [**HTTPServer**](#httpserver) | Tạo máy chủ web đơn giản | `-p` (chỉ định cổng) | `python3 -m http.server 8080` (Tạo máy chủ HTTP trên cổng 8080) |
| [**Crontab**](#crontab) | Lập lịch tác vụ định kỳ | `-e` (chỉnh sửa lịch cron), `-l` (liệt kê lịch cron) | `crontab -e` (Mở crontab để chỉnh sửa lịch trình) |
| [**sqlite3**](#sqlite3) | Tương tác với cơ sở dữ liệu SQLite | `.tables` (hiển thị các bảng), `.schema` (xem cấu trúc bảng) | `sqlite3 mydb.db` (Mở cơ sở dữ liệu SQLite có tên mydb.db) |
| [**LinEnum**](#linenum) | Công cụ kiểm tra quyền và cấu hình bảo mật trên hệ thống Linux | Không có cờ đặc biệt, chạy với quyền root để có kết quả đầy đủ | `./LinEnum.sh` (Chạy script LinEnum để thu thập thông tin hệ thống) |


## chmod
    Mục đích: Đặt quyền truy cập cho file/thư mục (ai được đọc/ghi/thực thi).
    Đọc (r), ghi (w), thực thi (x)

* **chmod +x script.sh**: Cấp quyền thực thi cho tập lệnh.

* **chmod -x script.sh**: Loại bỏ quyền thực thi (không chạy được trực tiếp)

## find
    Tìm kiếm file trong hệ thống.
> find . -name "*.txt": Tìm tất cả file .txt trong thư mục hiện tại

    tryhackme@linux1:~$ find -name passwords.txt
    ./folder1/passwords.txt
    tryhackme@linux1:~$
---
    tryhackme@linux1:~$ find -name *.txt
    ./folder1/passwords.txt
    ./Documents/todo.txt
    tryhackme@linux1:~$

## grep
    Tìm kiếm và hiển thị các dòng chứa mẫu cụ thể trong file hoặc đầu ra của lệnh khác.
> grep "từ_khóa" file.txt: Tìm "từ_khóa" trong file.txt
 
> ps aux | grep "process_name": Tìm tiến trình có tên        "process_name"

    tryhackme@linux1:~$ grep "81.143.211.90" access.log
    81.143.211.90 - - [25/Mar/2021:11:17 + 0000] "GET / HTTP/1.1" 200 417 "-" "Mozilla/5.0 (Linux; Android 7.0; Moto G(4))"
    tryhackme@linux1:~$

## nano
    Để tạo hoặc sửa file

> Điều hướng: Mũi tên lên/xuống, Enter để xuống dòng mới

* Tính năng:

    > Tìm kiếm văn bản (Ctrl + W)

    > Sao chép/Dán (Ctrl + 6, Ctrl + U)

    > Nhảy đến dòng (Ctrl + _)

    > Xem số dòng (Ctrl + C)

    > Thoát: Ctrl + X


## wget
    Tải tệp tin là một tính năng cơ bản trong máy tính, cho phép bạn lấy chương trình, script, hoặc ảnh từ internet.

> wget https://assets.tryhackme.com/additionallinux-fundamentalspart3/myfile.txt   

## scp
    scp là một lệnh để sao chép tệp an toàn giữa hai máy tính
    Nó sử dụng giao thức SSH để xác thực và mã hóa

Đoạn văn giải thích về cách sử dụng lệnh `scp` để truyền tệp an toàn giữa hai máy tính, sử dụng giao thức SSH để xác thực và mã hóa dữ liệu. 

**Tóm tắt các điểm chính:**

* `scp` là một lệnh để sao chép tệp an toàn giữa hai máy tính
* Nó sử dụng giao thức SSH để xác thực và mã hóa
* `scp` hoạt động theo mô hình SOURCE (nguồn) và DESTINATION (đích), cho phép bạn:
    * Sao chép tệp & thư mục từ máy tính hiện tại đến máy tính từ xa
    * Sao chép tệp & thư mục từ máy tính từ xa về máy tính hiện tại
* Bạn cần biết tên người dùng và mật khẩu của cả hai máy tính để sử dụng

**Ví dụ 1: Sao chép từ máy tính hiện tại đến máy tính từ xa**

* Giả sử bạn có các thông tin sau:
    * Địa chỉ IP máy tính từ xa: `192.168.1.30`
    * Tên người dùng trên máy từ xa: `ubuntu`
    * Tên tệp trên máy tính hiện tại: `important.txt`
    * Tên bạn muốn đặt cho tệp trên máy tính từ xa: `transferred.txt`

* Lệnh `scp` sẽ như sau:
   ```bash
   scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt
   ```

**Ví dụ 2: Sao chép từ máy tính từ xa về máy tính hiện tại**

* Giả sử bạn có các thông tin sau:
    * Địa chỉ IP máy tính từ xa: `192.168.1.30`
    * Tên người dùng trên máy từ xa: `ubuntu`
    * Tên tệp trên máy tính từ xa: `documents.txt`
    * Tên bạn muốn đặt cho tệp trên máy tính hiện tại: `notes.txt`

* Lệnh `scp` sẽ như sau:
   ```bash
   scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt
   ```

**Giải thích cú pháp lệnh `scp`**

* `scp`: Tên lệnh
* `SOURCE`: Đường dẫn đến tệp/thư mục nguồn
* `DESTINATION`: Đường dẫn đến nơi lưu tệp/thư mục đích
* `username@remote_IP_address` : Thông tin đăng nhập vào máy tính từ xa
* `:/path/to/file`: Đường dẫn đến tệp/thư mục trên máy tính từ xa

## HTTPServer
`HTTPServer` giúp dễ dàng tạo một máy chủ web đơn giản

**Khởi động** 

    python3 -m http.server -b IP_Address Port

**Dừng http.server**
    
    ps aux | grep http.server
    root       18085  0.0  0.3  30424 18304 pts/1    T    05:16   0:00 python3 -m http.server

    ┌──(root㉿kali)-[~]
    └─# ps aux | grep http.server
        root       18085  0.0  0.3  30424 18304 pts/1    T    05:16 0:00 python3 -m http.server

    ┌──(root㉿kali)-[~]
    └─# kill -9 18085
    [1]  + killed     python3 -m http.server

## Crontab
    Một tệp đặc biệt chứa danh sách các tác vụ định kỳ (cron jobs) mà cron sẽ thực hiện.

* `MIN`: Phút thực hiện (0-59)
* `HOUR`: Giờ thực hiện (0-23)
* `DOM`: Ngày trong tháng thực hiện (1-31)
* `MON`: Tháng trong năm thực hiện (1-12)
* `DOW`: Ngày trong tuần thực hiện (0-7, 0 và 7 đều là Chủ nhật)
* `CMD`: Lệnh sẽ được thực thi

Sao lưu thư mục "Documents" của người dùng "cmnatic" vào thư mục "/var/backups/" cứ sau 12 giờ.

    0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/

* Dấu "/" thêm vào dùng để thực thi vào cứ mỗi thời gian được đặt, nếu không có thì chỉ thực hiện 1 lần.

## sqlite3 
    Là một công cụ dòng lệnh (command-line tool) mạnh mẽ để tương tác với cơ sở dữ liệu SQLite. 


**Ví dụ cụ thể:**

1. **Tạo cơ sở dữ liệu và bảng:**

```bash
sqlite3 sinh_vien.db
CREATE TABLE sinhvien (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    ho_ten TEXT NOT NULL,
    tuoi INTEGER,
    diem_trung_binh REAL
);
.quit
```

2. **Chèn dữ liệu:**

```bash
sqlite3 sinh_vien.db
INSERT INTO sinhvien (ho_ten, tuoi, diem_trung_binh) VALUES ('Nguyễn Văn A', 20, 8.5);
INSERT INTO sinhvien (ho_ten, tuoi, diem_trung_binh) VALUES ('Trần Thị B', 21, 7.0);
.quit
```

3. **Truy vấn dữ liệu:**

```bash
sqlite3 sinh_vien.db
SELECT * FROM sinhvien;
.quit
```

Kết quả sẽ hiển thị danh sách sinh viên trong cơ sở dữ liệu.

### Giả sử chúng ta đã tải xuống thành công một cơ sở dữ liệu:

```jsx
user@linux$ ls -l 
-rw-r--r-- 1 user user 8192 Feb  2 20:33 example.db

user@linux$ file example.db 
example.db: SQLite 3.x database, last written using SQLite version 3039002, file counter 1, database pages 2, cookie 0x1, schema 4, UTF-8, version-valid-for 1
```

Chúng ta có thể thấy rằng có một cơ sở dữ liệu SQLite trong thư mục hiện tại.

Để truy cập nó, chúng ta sử dụng `sqlite3 <database-name>`:

```jsx
user@linux$ sqlite3 example.db                     
SQLite version 3.39.2 2022-07-21 15:24:47
Enter ".help" for usage hints.
sqlite>
```

Từ đây, chúng ta có thể xem các bảng trong cơ sở dữ liệu bằng cách sử dụng lệnh `.tables`:


```jsx
user@linux$ sqlite3 example.db                     
SQLite version 3.39.2 2022-07-21 15:24:47
Enter ".help" for usage hints.
sqlite> .tables
customers
```

Tại thời điểm này, chúng ta có thể kết xuất tất cả dữ liệu từ bảng, nhưng chúng ta sẽ không nhất thiết biết ý nghĩa của từng cột trừ khi chúng ta xem thông tin bảng. Đầu tiên, hãy sử dụng `PRAGMA table_info(customers);` để xem thông tin bảng. Sau đó, chúng tôi sẽ sử dụng `SELECT * FROM customers;` để kết xuất thông tin từ bảng:


```jsx
sqlite> PRAGMA table_info(customers);
0|cudtID|INT|1||1
1|custName|TEXT|1||0
2|creditCard|TEXT|0||0
3|password|TEXT|1||0

sqlite> SELECT * FROM customers;
0|Joy Paulson|4916 9012 2231 7905|5f4dcc3b5aa765d61d8327deb882cf99
1|John Walters|4671 5376 3366 8125|fef08f333cc53594c8097eba1f35726a
2|Lena Abdul|4353 4722 6349 6685|b55ab2470f160c331a99b8d8a1946b19
3|Andrew Miller|4059 8824 0198 5596|bc7b657bd56e4386e3397ca86e378f70
4|Keith Wayman|4972 1604 3381 8885|12e7a36c0710571b3d827992f4cfe679
5|Annett Scholz|5400 1617 6508 1166|e2795fc96af3f4d6288906a90a52a47f
```

Chúng ta có thể thấy từ thông tin bảng rằng có bốn cột: `custID`, `custName`, `creditCard` và `password`. Bạn có thể nhận thấy rằng điều này khớp với kết quả. Lấy hàng đầu tiên:

`0|Joy Paulson|4916 9012 2231 7905|5f4dcc3b5aa765d61d8327deb882cf99`

Chúng ta có `custID` (0), `custName` (Joy Paulson), `creditCard` (4916 9012 2231 7905) và băm mật khẩu (5f4dcc3b5aa765d61d8327deb882cf99).



## LinEnum
LinEnum là một công cụ tự động hóa quá trình thu thập thông tin và kiểm tra hệ thống **Linux** để tìm kiếm các điểm yếu hoặc cơ hội leo thang đặc quyền. Đây là một công cụ mạnh mẽ giúp kiểm tra nhiều khía cạnh bảo mật của hệ thống như quyền truy cập tệp, dịch vụ đang chạy, và cấu hình hệ thống.

### **Chức năng của LinEnum**

LinEnum sẽ thu thập và liệt kê các thông tin bảo mật quan trọng của hệ thống như:
- **Kiểm tra quyền truy cập SUID/SGID**: Xác định các tệp có quyền SUID/SGID có thể sử dụng để leo thang đặc quyền.
- **Kiểm tra dịch vụ đang chạy**: Xác định các dịch vụ nào đang chạy với quyền root hoặc người dùng khác có đặc quyền.
- **Kiểm tra cấu hình SSH**: Tìm các cấu hình SSH yếu như việc cho phép đăng nhập bằng root.
- **Kiểm tra các tác vụ cron**: Xác định các tác vụ định kỳ có thể bị khai thác.
- **Kiểm tra quyền trên các tệp nhạy cảm**: Ví dụ như `/etc/passwd`, `/etc/shadow`.

### **Cách sử dụng LinEnum**

1. **Tải xuống LinEnum**: 
   Nếu bạn chưa có công cụ này, bạn có thể tải xuống từ GitHub:
   ```bash
   wget https://github.com/rebootuser/LinEnum/blob/master/LinEnum.sh
   ```

2. **Cấp quyền thực thi cho LinEnum**:
   Trước khi chạy, bạn cần cấp quyền thực thi cho tệp script:
   ```bash
   chmod +x LinEnum.sh
   ```

3. **Chạy LinEnum**:
   Chạy công cụ LinEnum với quyền root để có thể thu thập đầy đủ thông tin hệ thống:
   ```bash
   ./LinEnum.sh
   ```

   Bạn cũng có thể lưu kết quả kiểm tra vào một tệp:
   ```bash
   ./LinEnum.sh > output.txt
   ```

### **Các tùy chọn quan trọng của LinEnum**
Mặc dù LinEnum có thể chạy mà không cần thêm tùy chọn nào, dưới đây là một số cờ bạn có thể sử dụng để điều chỉnh quá trình kiểm tra:
- **-r**: Chạy kiểm tra toàn diện và ghi kết quả.
   ```bash
   ./LinEnum.sh -r
   ```
- **-e**: Kiểm tra đầy đủ về các thông tin bảo mật như quyền truy cập tệp và dịch vụ.
   ```bash
   ./LinEnum.sh -e
   ```

### **Ví dụ kết quả của LinEnum**
Dưới đây là một ví dụ về đầu ra của LinEnum khi chạy kiểm tra các tệp SUID/SGID trên hệ thống:
```bash
#######################
# SUID/SGID Files #
#######################

[-] SUID files:
-rwsr-xr-x 1 root root 28760 Oct 24 18:21 /usr/bin/passwd
-rwsr-xr-x 1 root root 164200 May 10 21:21 /usr/bin/sudo
-rwsr-xr-x 1 root root 47256 Jun 11  2014 /usr/bin/chsh
```

Ngoài ra, LinEnum có thể cung cấp các thông tin về các tác vụ cron, quyền truy cập tệp nhạy cảm, và nhiều thông tin hữu ích khác giúp bạn xác định được các lỗ hổng bảo mật trong hệ thống.

