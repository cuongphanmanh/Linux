__1. Thao tác trên Files__
| No. | Function   | Commands     |
| :------------- | :---------- | :--------------------- |
| 01 | Liệt kê thư mục | __`li`__ |
| 02 | Liệt kê thư mục, cả file ẩn | __`li -al`__ |
| 03 | Chuyển đến thư mục| __`cd /abc/a1`__ |
| 04 | chuyển đến thư mục gốc | __`cd`__ |
| 05 | hiện thị thư mục hiện tại | __`pwd`__ |
| 06 | tạo thư mục | __`mkdir folderabc`__ |
| 07 | xóa file| __`rm filename`__ |
| 08 | xóa file không cần hỏi | __`rm -f filename`__ |
| 09 | xóa thư mục | __`rm -r thư-mục`__ |
| 10 | xóa thư mục, không hỏi | __`rm -rf thư-mục `__ |
| 11 | copy file1 vào file2| __`cp file1 file2`__ |
| 12 | chuyển đến thư mục gốc | __`mv file1 file2`__ |
| 13 | tạo symbolic link ('link' trỏ đến file) | __`ln -s fileabc link`__ |
| 14 | tạo file hoặc cập nhật file | __`touch fileabc`__ |
| 15 | đè nội dung soạn thảo vào file (__CTRL+D__ để ghi lại)| __`cat > fileabc`__ |
| 16 | hiện thị nội dung file | __`cat fileabc`__ |
| 13 | hiện thị nội dung file | __`more fileabc`__ |
| 14 | hiện thị nội dung file | __`less fileabc`__ |
| 15 | hiện thị 10 dòng đầu của file | __`head fileabc`__ |
| 16 | hiện thị 10 dòng cuối của file | __`tail fileabc`__ |
  
__2. Nén và giải nén__
| No. | Function   | Commands     |
| :------------- | :---------- | :--------------------- |
| 01 | nén thư mực vào .tar | __`tar -cvf /tenfilenen.tar /thu-muc-can-nen`__ |
| 02 | giải nén file .tar | __`tar -xvf file-nen.tar`__ |
| 03 | nén file thành file.gz | __`gzip file`__ |
| 04 | giải nén file.gz | __`gzip -d file.gz`__ |
  
__3. Permission__
| No. | Function   | Commands     |
| :------------- | :---------- | :--------------------- |
| 01 | thay đổi permission | __`chmod octal file`__  octal con số bát phân (1)(2)(3) thể hiện permision (rwx == read-write-execute) |
| 02 | rw cho owner, rx cho group/world | __`chmod 775 file`__ |
| 03 | file rwx cho tất các các user | __`chmod 777 file`__ |
| 04 | thiết lập cho toàn thư mục | __`chmod -R 755 directory-name/`__ |
| 05 | đổi owner\|group của file | __`chown -R owner:group file/directory`__ |
