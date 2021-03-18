****Sử dụng Cron Crontab tự động chạy script trên Server Linux****
  
  ---  
    
- Cron, Crontab là một tiện ích tự động thi hành các tác vụ trong hệ thống Linux theo lịch biểu lập sẵn, tìm hiểu cách tạo các crontab
- Một chức năng giống như Microsoft Task Scheduler, nó cho phép bạn chạy các tác vụ theo một lịch biểu (có thể một lần, lặp lại nhiều lần) theo phút, giờ, ngày, tuần, tháng. 
- Thành phần đó trong Linux là crontab (viết tắt của chronograph table). 
- Nó dựa vào đồng hồ hệ thống xác định thời điểm phù hợp thi hành các tác vụ được cấu hình chạy. 
- Thường sử dụng crontab để chạy các lệnh, các script nhẹ với mục đích bảo trì hệ thống.
- ví dụ như định kỳ hàng tuần xóa các file log cũ sinh ra bởi httpd, định kỳ cập nhật phần mềm ...
  
__1. Kiểm tra trạng thái dịch vụ cron__  
- CentOS  
```sh
$ systemctl status crond
```
- Ubuntu
```sh
$ systemctl status cron
```
- Dừng, chạy, khởi động lại  
```sh
$ systemctl stop crond
$ systemctl start crond
$ systemctl restart crond
```
  
__2. Kiểm tra các crontab__  
- Các crontab (các tác vụ cần chạy theo lịch) được thiết lập chạy cho từng User, để liệt kê xem User hiện tại (đang login) có các crontab nào:
```sh
crontab -l
```
- Biên tập crontab  
\+ Mặc định thì lưu trữ tại __`/var/spool/cron/`__  
\+ Dùng các trình soạn thảo text như vim, nano vào biên tập - thêm bớt các tác vụ cần chạy theo lịch  
\+ Hoặc vào ngay soạn thảo các crontab cho user hiện tại  
```sh
$ crontab -e
```
- Định dạng các dòng Crontab
```sh
*[phút]  *[giờ]  *[ngày trong tháng]  *[tháng]  *[thứ]  [lệnh chạy (script hoặc lệnh linux)]
```
| phút | giờ | ngày | tháng | thứ | Script |
| :--- | :-- | :--- | :---- | :--- | :--- |
| `1 - 59` | `0 - 23` | `1 - 31` | `1 - 12` | `0 - 7` | _scipts_ |
|||||`0 = CN`||
|||||`7 = t7`||  
  
Các cột thời gian, loại thời gian nào luôn xảy ra để dấu __`*`__ (ví dụ mọi phút thì cột phút để dấu __`*`__, mọi giờ thì cột giờ để __`*`__, mọi ngày thì cột ngày để __`*`__ ....)  
Còn muốn xảy ra ở một thời điểm cụ thể thì điền thời điểm đó vào.  
__vd:__  
```sh 
      #A. Cứ đến phút 30 hàng giờ thì chạy script tên là /script/abc.sh 

30 * * * *  /script/abc.sh

      #B. Chạy vào lúc 3 giờ hàng ngày

0 3 * * *  /script/abc.sh

      #C. Chạy vào lúc 17h ngày chủ nhật hàng tuần

0 17 * * sun /scripts/abc.sh

      #D. Cứ 8 tiếng là chạy

0 */8 * * * /scripts/abc.sh

      #E. Cứ 30 phút chạy một lần

*/30 * * * * /script/abc.sh
```
___Một số dạng tắt:___  
```sh
      # Chạy hàng tháng
      
@monthly /scripts/abc.sh

      #Chạy hàng tuần

@weekly /bin/script.sh

      #Chạy hàng ngày

@daily /scripts/script.sh
```
  
__3. Bài tập tình huống___  
_ex1:_ Mysql nhiều khi bị crash database và cần repair, tạo một script làm việc này và chạy vào 3h sáng hàng ngày.  
```sh
$ mkdir ~/Desktop/Mybash
$ cd ~/Desktop/Mybash
$ touch repairdb.sh
$ nano repairdb.sh

# Nội dung:

#!/bin/bash
mysqlcheck -u{username_SQL}  -p{password_SQL} --auto-repair --check --all-databases

$ crontab -e

# Nội dung:

*    3    *    *    *    /rpairdb.sh
```
  
_ex2:_ Bạn có file PHP, lưu tại /home/user/run30.php, trong đó có các code php mà bạn muốn chạy cứ 30 phút một lần:
Làm tương tự như trên và thêm vào crontab
```sh
*/30    *    *    *    *    php /home/user/run30.php
```
