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

##2. Tạo User define variables (UDV)
###2.1 Cú pháp
Để tạo các UDV, cú pháp như sau :
variable name=value
```sh
$ n=10
$ vech=Bus
```
Ở đây định ra 2 biến **n** có giá trị bằng 10, biến **vech** có giá trị bằng **Bus**

###2.2 Một số quy định khi đặt tên biến 
####Rule 1 
Tên biến bắt buộc phải bắt đầu bằng chữ cái hoặc đặt sau dấu `_`. Ví dụ :
```sh
HOME
SYSTEM_VERSION
vech
no
```
####Rule 2
Không dùng ký tự khoảng trống. Cách các đặt biến sau sẽ không được chấp nhận : 
```sh
$ no =10
$ no= 10
$ no = 10
```
####Rule 3 
Các ký tự chữ thường và chữ hoa sẽ tạo các biến khác nhau.Ví dụ :
```sh
$ no=10
$ No=11
$ NO=20
$ nO=2
```
Các biến trên là hoàn toàn khác nhau.
####Rule 4 
Có thể định ra các biến **NULL**. Biến này sẽ không có giá trị thời điểm đặt biến.Ví dụ : 
```sh
$ vech=
$ vech=""
```
Khi in biến ra với câu lệnh `echo $vech`, sẽ không có gì hiện ra vì biến không có giá trị nào.
####Rule 5
Không sử dụng các ký tự `?,*...` trong tên biến

##3. Câu lệnh echo
Cú pháp câu lệnh :

```
echo [options] [string, variables...]
```
Các `option` trong câu lệnh :

|Option|Ý nghĩa|
|------|-------|
|-n|Không xuống dòng|
|-e|Cho phép thực hiện các option với dấu \|
|\a|Chuông cảnh báo|
|\b|Xóa đi ký tự bên tay trái|
|\c|Không xuống dòng đồng thời chặn toàn bộ các ký tự bên phải|
|\n|Tạo 1 dòng mới|
|\t|Tạo 1 khoảng cách|
####4. Thực hiện phép tính trong Shell 
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

####4. Dấu trích dẫn

|Dấu trích dẫn|Ý nghĩa|
|-------------|------|
|"|Giữ nguyên các giá trị trong dấu, ngoài trừ `\` và `$`|
|'|Giữ nguyên các giá trị trong dấu|
|`	|Thực hiện command|

####5. Exit Status

Trong Linux, mỗi khi một command/shell được thực hiện, nó sẽ trả về 2 loại giá trị cho biết là câu lệnh có được thực hiện thành công hay không :
 - Loại 1: Giá trị trả về là 0, command được thực hiện thành công.
 - Loại 2 : Giá trị trả về # số 0, command chưa được thực hiện thành công, hoặc có lỗi trong quá trình thực hiện command/shell script.

Hiển thị `Exit Status` với biến : `$?`

####5. `read` Statement
Được dùng để nhận giá trị đầu vào ( data từ user) từ keyboard và lưu data lại để làm biến.
**Cú pháp** :
```sh
read variable1
```
User nhập giá trị cho biến, và ấn [ENTER] để tiếp tục.

Ví dụ : 

```sh
$ vi sayH
#
#Script to read your name from key-board
#
echo "Your first name please:"
read fname
echo "Hello $fname, Lets be friend!"
```
Sau khi nhập giá trị biến là : `manhdinh`, chmod script, chạy thử script, kết quả hiện ra sẽ là :
$ chmod +x sayH
$ ./sayH

Giá trị hiển thị sẽ là : `manhdinh`

####6. Dấu wildcard

| Dấu wild card| Ý nghĩa | 
|--------------|---------|
|		*	   |Ứng với bất kỳ chuỗi hoặc nhóm các ký tự|
Ví dụ : 
 - `$ ls *` : hiện ra tất cả các file
 - `$ ls a*` : hiện ra tất cả các file tên bắt đầu với chữ **a**
 - `$ ls *.c` : hiện ra tất cả các file có ký tự **c**
 - `$ ls ut*.c` : hiện ra tất cả các file có ký tự **c** nhưng phải bắt đầu bằng **ut**
 
| Dấu wild card| Ý nghĩa |
|--------------|---------|
|		?	   | Ứng với bất kỳ giá trị đơn nào|
Ví dụ :
 - **$ ls ?** : hiện ra tất cả các file với tên có độ dài 1 ký tự
 - **$ ls fo?** : hiện ra tất cả các file với độ dài 3 ký tự và bắt đầu với **fo**

| Dấu wild card| Ý nghĩa |
|--------------|---------|
|	  [...]    | Ứng với bất kỳ ký tự nào trong ngoặc |

Ví dụ : **ls [abc]*** : hiện ra tất cả các file bắt đầu với ký tự a,b,c

**Chú ý**  [..-..] Dấu **-** bao hàm các giá trị từ ký tự này đến ký tự kia
Ví dụ : **$ ls /bin/[a-c]* ** : hiện ra tất cả các file bắt đầu với a,b,c

Nhưng với : **$ ls /bin/[!a-o]** hoặc **$ ls /bin/[^a-o]** sẽ hiện ra các file bắt đầu với các ký tự không phải từ a đến o.

####7. Thực hiện nhiều command trên một command line

Cú pháp :
`command1;command2`

Ví dụ : `$ date;who`

####8. Tiến trình thực hiện command

Trong một câu lệnh, ví dụ `$ mv y.bak y.ok` thì chỉ có phần `mv` là câu lệnh thực sự, các thành phần còn lại được gọi là các argument của câu lệnh.
Trong câu lệnh này có 2 argument là `y.bak` và `y.ok`.

 - **$#** : chỉ số argument có trong 1 command line
 - **$*** và **$@** : đề cập tới tất cả các argument trong script

####9. Biểu tượng chuyển hướng

| Dấu | Ý nghĩa | 
|-----|---------|
|  >  |Thực hiện ghi đè giá trị vào file output|
| >>  |Thực hiện ghi tiếp giá trị vào file output|
|  <  |Thực hiện lấy giá trị từ file input|

Ví dụ :
 - **ls /root/ > file** : Thực hiện ghi giá trị vào file, nếu file đã có sẵn thì giá trị cũ sẽ bị ghi đè.
 - **ls /root/ >> file** : Thực hiện ghi tiếp giá trị vào cuối file, các dữ liệu cũ trong file vẫn đc giữ nguyên.
 - **cat < file** : Thực hiện nhận giá trị có trong file

####10. Dấu |
![shell](/images/pipe.gif)

**Cú pháp** : command1|command2 

Command 2 sẽ nhận output của command 1 làm input.

####11. Filter

Filter thực hiện nhận input và tạo ra output.

Ví dụ : Bạn có 1 file gọ là `hotel.txt` với 100 dòng dữ liệu .Và từ `hotel.txt` bạn muốn in các dòng từ 20 -> 30, 
và lưu nó trong một file gọi là `hlist`. Câu lệnh như sau :
```sh
$ tail +20 < hotel.txt | head -n30 >hlist
```

Lúc này, **head** command được gọi là filter, sẽ nhận input từ **tail** command ( tail command sẽ bắt đầu lấy các dòng từ dòng 20) 
và nhận các dòng như này là input cho head, output sẽ được ghi cho `hlist`.
