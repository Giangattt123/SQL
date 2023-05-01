# SQL SELECT LIMIT, TOP, FETCH FIRST

Từ khóa LIMIT trong SQL cho phép bạn chỉ định số lượng bản ghi sẽ trả về trong một truy vấn. Chúng ta có thể sử dụng từ khóa LIMIT với MySQL, PostgreSQL và SQLite.

```
SELECT first_name, age
FROM Customers
LIMIT 2;
```

> Ở đây, lệnh SQL chọn 2 hàng đầu tiên từ bảng **Customers**

## SQL LIMIT With OFFSET Clause

Từ khóa **OFFSET** được sử dụng với LIMIT để chỉ định xem hàng bắt đầu từ đâu để chọn dữ liệu.
_Example:_

```
-- LIMIT 2 selects two results
-- OFFSET 3 excludes the first three results
SELECT first_name, last_name
FROM Customers
LIMIT 2 OFFSET 3;
```

> Ở đây, lệnh SQL chọn 2 hàng bắt đầu từ hàng thứ tư. OFFSET 3 có nghĩa là 3 hàng đầu tiên bị loại trừ.

![image1](https://live.staticflickr.com/65535/52861184253_367c816e3f_w.jpg)

`NOTE`: Không phải tất các DBMS đều hỗ trờ tư khóa `LIMIT` , với mỗi một DBMS khác nhau từ khóa có thể là khác nhau

- **TOP**: SQL Server, MS Access
- **LIMIT**: MySQL, PostgreSQL, SQLite
- **FETCH FIRST**: Oracle

## SQL TOP Clause

```
SELECT TOP 2 first_name, last_name
FROM Customers;
```

Ở đây, lệnh SQL chọn first_name và last_name của 2 hàng đầu tiên. Cũng có thể sử dụng `*` với `TOP` để chọn tất cả các cột.

```
SELECT TOP 2 *
FROM Customers;
```

![image2](https://live.staticflickr.com/65535/52861162475_c807cf964e_n.jpg)

## SQL IN And NOT IN Operators

Toán tử `IN` được sử dụng với mệnh đề **WHERE** để so khớp các giá trị trong danh sách. Ví dụ:

```
SELECT first_name, country
FROM Customers
WHERE country IN ('USA');
```

> Ở đây, lệnh SQL chọn các hàng từ bảng **Customers** có giá trị quốc gia là 'USA'.

- **Syntax:**

```
SELECT column1, column2, ...
FROM table
WHERE column IN (value1, value2, ...);
```

    - Trong đó:
        #column1 , column2 : là tên của cột trong bảng
        #table : lấy dữ liệu từ bảng nào
        #column : là nơi các giá trị được so sánh
        #IN : chỉ định các giá trị mà giá trị cột sẽ được so sánh
        #value1, value2, ... : là các giá trị mà giá trị cột được so sánh

_Examples:_

```
SELECT first_name, country
FROM Customers
WHERE country IN ('USA', 'UK');
```

> Ở đây câu lệnh SQL trên sẽ chọn ra các hàng mà có **country** là USA or UK

![image3](https://live.staticflickr.com/65535/52861005806_440b6ba598_n.jpg)

## SQL IN Operator With Columns

Toán tử `IN` cũng có thể được sử dụng để chọn các hàng có một giá trị nhất định tồn tại trong trường đã cho. Hãy xem một ví dụ để làm rõ nó.

```
SELECT first_name, country
FROM Customers
WHERE 'USA' IN (country);
```

> Ở đây, lệnh SQL chọn các hàng nếu giá trị "USA" tồn tại trong trường **country**.

![image4](https://live.staticflickr.com/65535/52861183699_a66b4fb6f3_n.jpg)

> Tương tự ngược lại với **NOT IN**

## SQL IN Operator With Subquery

Giả sử chúng ta chỉ muốn thông tin chi tiết về những khách hàng đã đặt hàng. Đây là cách chúng ta có thể làm điều đó bằng _subquery_.

```
SELECT customer_id , first_name
FROM Customers
WHERE customer_id IN (
    SELECT customer_id
    FROM Orders
)
```

- **Trong đó:**

  - Chọn ra **customer_id** từ bảng **Orders** bằng _subquery_
  - Chọn ra các hàng từ bằng **Customers** với điều kiện các **customer_id** nằm trong tập hợp kết quả của truy vấn phụ trả về tức là nếu các **customer_id** cũng nằm trong bảng **Orders**
