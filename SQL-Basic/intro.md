# Tạo database , table , sửa , xóa , chèn , update ,..

_Để tạo một database ta sử dụng câu lệnh **CREATE DATABASE** name_database_

```
CREATE DATABASE PTIT;
-- Lưu trữ cơ sở dữ liệu của PTIT
```

_Để tạo một bảng trong database ta sử dụng từ khóa **USE** name_database_

```
USE SQLDBQuery;
CREATE TABLE SinhVien(
	ID int,
	fullName varchar(255),
	msv varchar(255),
	Address varchar(255)
);
```

_Xóa database : **DROP DATABASE** name_database , tương tự nếu muốn xóa bảng_

```
DROP DATABASE SQLDBQuery;
DROP TABLE SinhVien;
```

_Xem các database hiện có_

- Đối với SQL Server : SELECT name FROM master.sys.databases;
- Đối với MySql : SHOW DATABASE;

  Kết quả trả về bao gồm một số database mặc định có sẵn trong SQL Server và các database do chính chúng ta tạo ra
  -master: Chứa các thông tin về cấu hình của SQL Server và các đối tượng trong hệ thống.
  -tempdb: Được sử dụng để lưu trữ dữ liệu tạm thời cho các thao tác trên cơ sở dữ liệu.
  -model: Được sử dụng để tạo ra các cơ sở dữ liệu mới.
  -msdb: Chứa các đối tượng hỗ trợ cho SQL Server Agent, như các lịch trình và các công việc được lập lịch.
  -SQLDBQuery : Cơ sở dữ liệu ta vừa tạo ra ở trên

_Thêm dữ liệu vào bảng với câu lệnh **INSERT INTO**_

```
INSERT INTO SinhVien (ID , fullName , msv , Address)
VALUES (1 , 'Giang' , 'B21DCAT077' , 'Vĩnh Phúc');
```

> Như vậy 1 bản ghi mới đã được thêm vào bảng SinhVien

![image1](https://live.staticflickr.com/65535/52854298065_4dc1af1826_w.jpg)

_Sau khi ta thêm vào một bản ghi nếu ta muốn xem dữ liệu bản ghi có trong bảng ta có thể sử dụng câu lệnh **SELECT th FROM table_name;**_

```
SELECT * FROM SinhVien;
```

![image2](https://live.staticflickr.com/65535/52853904181_1640bc496a.jpg)

_Bây giờ muốn xóa tất cả các bản ghi trong 1 table ta sẻ sử dụng **TRUNCATE TABLE table_name**_

```
TRUNCATE TABLE SinhVien;
SELECT * FROM SinhVien;
```

> Lúc này thì các bản ghi trong bảng sẽ trống rỗng

_Chẳng hạn bây giờ ta muốn thêm cột trong bảng thì ta sẽ sử dụng câu lệnh **ALTER TABLE name_table ADD column_name datatype**_

```
ALTER TABLE SinhVien ADD Gpa int;
SELECT * FROM SinhVien;
```

> Lúc này một cột mới có tên Gpa có kiểu dữ liệu **int** đã được thêm vào

![image3](https://live.staticflickr.com/65535/52854329650_89f4b99c1d_c.jpg)

_Tương tự với xóa một cột ta sử dụng **DROP COLUMN**_

```
ALTER TABLE SinhVien DROP COLUMN Gpa;
SELECT * FROM SinhVien;
```

> Lúc này cột **Gpa** vừa thêm vào phía trên sẽ bị xóa

_Để thay đổi kiểu dữ liệu của một cột , ta sử dụng cấu trúc sau:_

```
ALTER TABLE name_table
ALTER COLUMN column_name datatype;
```
