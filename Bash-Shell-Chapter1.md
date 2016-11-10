##1. Biến trong Shell

Để thực hiện data/infomation, thì data phải được giữ ở trong RAM. RAM được chia thành các khu vực nhỏ, và từng khu vực có những số đánh dấu duy nhất gọi là memory location/address.
Lập trình viên có thể đặt tên cho memory location/address này, được gọi là memory variable hay variable (biến) (Có thể nhận các giá trị khác nhau, nhưng không cùng một thời điểm).

Trong Shell có 2 loại biến :
 - System variables : Được tạo và duy trì bởi Linux. Loại biến này được đánh dấu bằng các chứ cái in hoa
 - User defined variable (UDV): Được tạo và duy trì bởi user. Loại biến này được đánh dấu bằng các chữ cái thường.
 
Các **system variable** có dạng **$set**, một vài biến quan trọng như :

|System Variable|Ý nghĩa|
|---------------|-------|
|BASH=/bin/bash|Shell name|
|BASH_VERSION=1.14.7(1)|Shell version name|
|COLUMNS=80|Số hàng dọc trên màn hình|
|HOME=/home/vivek|Thư mục home|
|LINES=25|Số dòng trên màn hình|
|LOGNAME=students|Tên logging|
|OSTYPE=Linux|Loại OS|
|PATH=/usr/bin:/sbin:/bin:/usr/sbin|Các cài đặt đường dẫn|
|PS1=[\u@\h \W]\$|Các cài đặt dấu nhắc|
|PWD=/home/students/Common|Thư mục hiện thời|
|SHELL=/bin/bash|Shell name|
|USERNAME=vivek|User mới logging vào PC|

##2. Thực hiện phép tính trong Shell 
Trong Shell, các phép tính sau :

|Phép tính|Cú pháp|
|---------|-------|
|Cộng|+|
|Trừ|-|
|Chia|/|
|Chia module|%|
|Nhân|\*|

Cú pháp thực hiện phép tính. Ví dụ định nghĩa 2 giá trị x=20, y=5 và thực hiện phép chia x / y.
```sh
$ x=20
$ y=5
$ expr $x / $y
```