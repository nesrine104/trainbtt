---
title: Task 1

---

# I. Kiểu dữ liệu
## 1. Khái niệm
- Là tập hợp các nhóm dữ liệu có cùng đặc tính, cách lưu trữ và thao tác xử lí trên trường dữ liệu đó
- Xác định loại giá trị mà một biến hoặc hằng số có thể chứa
## 2. Kiểu dữ liệu nguyên thủy
- Là kiểu dữ liệu cơ bản, được cung cấp sẵn trong ngôn ngữ lập trình, lưu trữ các giá trị đơn giản
- Các kiểu dữ liệu nguyên thủy

|          | Giá trị |Độ lớn|Đặc tả dữ liệu|
| ---------| -------- | -------- | ---   |
| Số nguyên(int)|-2,147,483,648 -> 2,147,483,647|  4 byte   |   %d  |
| Số thực (float)  |3.4E-38 -> 3.4E+38|  4 byte   |  %f   |
| Boolean  |True/False|  1 byte  |     |
| Kí tự    | -128-->127  |  1 byte  |   %c  |
| Chuỗi    |     | phụ thuộc số lượng kí tự |   %s  |
- Với số nguyên:

|        | | |
| ------ | -------- | -------- |
| Có dấu       | cả giá trị âm và dương |dùng 1 bit để lưu trữ dấu|
| Không có dấu | chỉ có giá trị dương |tất cả bit để lưu trữ giá trị |
- Xây dựng chương trình:
```
#include<stdio.h>

int main()
{
    int a=2;
    float b=4.3256;
    char c='M';
    printf("So nguyen a: %d\n", a);
    printf("So thuc b: %.2f\n", b);
    printf("Ki tu c: %c", c);
    return 0;
}
```
## 3. Ép kiểu
### a. Khái niệm
- Là quá trình chuyển đổi một giá trị từ kiểu dữ liệu này sang kiểu dữ liệu khác
### b. Phân loại
- Ép kiểu ngầm định: Là loại ép kiểu được trình biên dịch thực hiện tự động khi cần thiết

VD: 
```
#include<stdio.h>

int main()
{
    int a=10;
    float b;
    b = a;
    printf("%f", b);
    return 0;
}
```

- Ép kiểu tường minh: Là loại ép kiểu được lập trình viên thực hiện một cách rõ ràng bằng toán tử ép kiểu
VD: 
```
#include<stdio.h>

int main()
{
    int a=10;
    printf("%f", (float)a);
    return 0;
} 
```
# II. Biến
## 1. Địa chỉ
- Là vị trí bộ nhớ nơi giá trị của biến được lưu trữ
- Mỗi biến được gán một địa chỉ bộ nhớ duy nhất để chương trình có thể truy cập và thao tác với dữ liệu của biến
## 2. Giá trị
- Là dữ liệu thực tế được lưu trữ trong biến đó
- Có thể gán, thay đổi giá trị

VD:
```
#include<stdio.h>

int main()
{
    int a=-10;
    float b=2.5;
    char c='A';
    short d=29;
    long long e=40000;
    double f=23473;
    unsigned int g=324;
    unsigned char h='Y';
    printf("Gia tri: %d         Dia chi:%p\n", a, &a);
    printf("Gia tri: %f         Dia chi:%p\n", b, &b);
    printf("Gia tri: %c         Dia chi:%p\n", c, &c);
    printf("Gia tri: %hi        Dia chi:%p\n", d, &d);
    printf("Gia tri: %lld       Dia chi:%p\n", e, &e);
    printf("Gia tri: %lf        Dia chi:%p\n", f, &f);
    printf("Gia tri: %u         Dia chi:%p\n", g, &g);
    printf("Gia tri: %c         Dia chi:%p", h, &h);
    return 0;
}
```
- Em thêm một đoạn code để tính khoảng cách giữa các biến, sử dụng kiểu **(uintptr_t)** trong thư viện stdint.h
- Có sự chênh lệch giữa địa chỉ các biến, vì mỗi kiểu dữ kiểu có một vùng nhớ nhất định, ngoài ra còn phụ thuộc vào hệ điều hành và trình biên dịch
## 3. Biến toàn cục và biến cục bộ
|              | Biến toàn cục            | Biến cục bộ                     |
| ------------ | ------------------------ | ------------------------------- |
| Nơi khai báo | bên ngoài tất cả các hàm | trong một hàm/khối lệnh         |
| Phạm vi      | trong cả chương trình    | trong khối lệnh/hàm mà khai báo |
|Khởi tạo không có giá trị gán| bằng 0 |  giá trị rác              |





