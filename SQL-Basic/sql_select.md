# Select and From

Câu lệnh **SQL Select** được sử dụng để chọn dữ liệu(retrieve) từ một bảng cơ sở dữ liệu
_Examples:_

```
SELECT first_name
FROM Customers;
```

> ở đây có thể hiểu các câu lệnh trên đang chọn tất cả các _first_name_ từ bảng **Customers**

- **SQL SELECT Syntax**

```
SELECT column1 , column2 , ...
FROM table_name;
```

_Examples:_

```
SELECT first_name, last_name
FROM Customers;
```

![image1](https://live.staticflickr.com/65535/52857548313_1c7500f7fe_n.jpg)

- **SQL SELECT All**

Chọn ra tất cả các cột từ một bảng cơ sở dữ liệu , khi mà chúng ta sử dụng kí tự **\***
_Examples:_

```
SELECT *
FROM Customers;
```

![image2](https://live.staticflickr.com/65535/52856535072_ee1f59880d_m.jpg)

- **SQL SELECT WHERE Clause**

Một câu lệnh SELECT có thể có mệnh đề WHERE tùy chọn. Mệnh đề WHERE cho phép chúng ta tìm nạp các bản ghi từ một bảng cơ sở dữ liệu khớp với (các) điều kiện đã chỉ định.
_Examples:_

```
SELECT * FROM Customers
WHERE last_name = 'Doe';
```

> Ở đây câu lệnh SQL trên sẽ chọn tất cả các bản ghi có **last_name** là _Doe_ từ bảng Customers

![image3](https://live.staticflickr.com/65535/52857202021_003f416ce7.jpg)

```
SELECT age, country
FROM Customers
WHERE country = 'USA';
```

## SQL Operators

SQL cung cấp 1 số toán tử trong mệnh đề điều kiện WHERE như = , > , < , >= , <= , >, AND , OR , <>  
Có thể xem kĩ hơn ở [SQL Operators](https://www.w3schools.com/sql/sql_operators.asp)

## SQL SELECT DISTINCT Statement

Câu lệnh **DISTINCT** trong SQL để lấy các giá trị riêng biệt hay khác nhau từ một bảng trong database

```
-- select the unique ages from the Customers table
SELECT DISTINCT age
FROM Customers;
```

- Syntax:

```
SELECT DISTINCT column1, column2 ...
FROM table;
```

_Examples:_

```
SELECT DISTINCT country
FROM Customers;
```

![image4](https://live.staticflickr.com/65535/52857748843_2901af50e0.jpg)

## SQL DISTINCT With Multiple Columns

Không những ta chỉ có thể lấy dữ liệu từ 1 cột mà ta có thể lấy dữ liệu từ nhiều cột

_Examples:_

```
SELECT DISTINCT country, first_name
FROM Customers;
```

![image5](https://live.staticflickr.com/65535/52857487379_72c7e2937c_w.jpg)

## DISTINCT With COUNT

Nếu chúng ta cần đếm số hàng duy nhất, chúng ta có thể sử dụng hàm **COUNT()** với DISTINCT.
_Examples:_

```
SELECT COUNT(DISTINCT country)
FROM Customers;
```

![image6](https://live.staticflickr.com/65535/52857487374_720fe5c03d.jpg)

## SQL SELECT AS Alias

Từ khóa **AS** được sử dụng để cung cấp cho các cột hoặc bảng một tên tạm thời có thể được sử dụng để xác định cột hoặc bảng đó sau này.
_Examples:_

```
SELECT last_name AS name
FROM Customers;
```

> Ở đây, lệnh SQL chọn cột **last_name** từ bảng **Customers**. Tuy nhiên, tên cột được đổi thành **name** trong tập hợp kết quả.

- **SQL AS Alias Syntax**

```
SELECT column_1 AS alias_1,
    column_2 AS alias_2,
…... column_n AS alias_n
FROM table_name;
```

_Examples:_

```
SELECT first_name AS name
FROM Customers;
```

![image7](https://live.staticflickr.com/65535/52856745457_443c8aa94d_w.jpg)

- **SQL AS With Expression**
  Chúng ta có thể kết hợp dữ liệu từ nhiều cột và biểu diễn dữ liệu đó trong một cột duy nhất bằng cách sử dụng hàm _CONCAT()_.

```
SELECT CONTACT(first_name, ' ', last_name) AS full_name
FROM Customers;
```

Đối với SQLite , ta sẽ sử dụng toán tử **||** để nối chuỗi

```
SELECT first_name || ' ' || last_name AS full_name
FROM Customers;
```

![image8](https://live.staticflickr.com/65535/52857725700_6cd8edd0af_w.jpg)
