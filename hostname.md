****Hostname****  
  
---  
  
- là tên gán cho máy khi nó gắn vào hệ thống mạng
- tên này phải là duy nhất trên mạng nó kết nối
- nhằm đảm bảo các máy có thể liên lạc với nhau thông qua tên này mà không cần địa chỉ IP  
  
__1. Xem hostname__
```sh
$ hostname
```  
__2. Đổi hostname__
```sh
$ hostname sv01.domain01.com
```
Sau đó mở và chỉnh sửa file __`/etc/sysconfig/network`__ (mở bằng __vi__ hoặc __nano__):
```ps
$ vi /etc/sysconfig/network
```
Chỉnh sửa thành:
```sh
NETWORKING=yes
HOSTNAME=sv01.domain01.com
```
_Trên CentOS 7 có thể cần thiết lập cả trong file_ __`/ect/hostname`__
```ps
$ vi /ect/hostname
```
#Nội dung
```ps
sv01.domain01.com
```
__3. Thiết lập local network__
```ps
$ nano /etc/hosts
```
```sh
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
X.X.X.X     sv01.domain01.com
```
```sh
$ service network restart
```
```sh
$ hostname

server1.mydomain.com

$ ping localhost
```
