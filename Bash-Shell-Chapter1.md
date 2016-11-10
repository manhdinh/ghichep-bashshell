#Biến trong Shell
Để thực hiện data/infomation, thì data phải được giữ ở trong RAM. RAM được chia thành các khu vực nhỏ, và từng khu vực có những số đánh dấu duy nhất gọi là memory location/address.
Lập trình viên có thể đặt tên cho memory location/address này, được gọi là memory variable hay variable (biến) (Có thể nhận các giá trị khác nhau, nhưng không cùng một thời điểm).

Trong Shell có 2 loại biến :
 - System variables : Được tạo và duy trì bởi Linux. Loại biến này được đánh dấu bằng các chứ cái in hoa
 - User defined variable (UDV): Được tạo và duy trì bởi user. Loại biến này được đánh dấu bằng các chữ cái thường.
 
Các **system variable** có dạng **$set**, một vài biến quan trọng như :

|System Variable|Ý nghĩa|
|---------------|-------|
|BASH=/bin/bash|shell name|
|BASH_VERSION=1.14.7(1)|shell version name|