---
title: I. Con trỏ

---

# I. Con trỏ 
## 1. Khái niệm
- Là một biến thông thường mà giá trị nó lưu là địa chỉ của một biến khác
- Cú pháp: Kieu_du_lieu *ten_bien;
- Để xem địa chỉ của biến mà con trỏ trỏ tới: 

```#include<stdio.h>

int main()
{
    int n=100;
    int *a;
    a=&n;
    printf("%d\n", a);
    return 0;
}
```
- Để xem giá trị tại vùng nhớ trỏ tới:

```
#include<stdio.h>

int main()
{
    int n=100;
    int *a;
    *a=n;
    printf("%d\n", *a);
    return 0;
}
```

## 2. Ứng dụng
- Truyền tham số cho biến
- Truy cập phần tử trong mảng

```#include<stdio.h>

int main()
{
    int a[3]={1, 3, 5};
    int *b=a;
    for (int i=0; i<3; i++) {
        printf("a[%d]=%d\n", i, *(b+i));
    }
    return 0;
}
```
# II. Mảng một chiều
- Khái niệm: Là một cấu trúc dữ liệu lưu trữ nhiều phần tử có cùng kiểu dữ liệu
- Ứng dụng con trỏ:
```
#include<stdio.h>

int main()
{
    int a[3]={1, 3, 5};
    int *b=a;
    printf("a[1]=%d", *(b+1));
    return 0;
}
```
với `*b` là phần tử đầu tiên của mảng
# III. Hàm
## 1. Khái niệm
- Là một chương trình con gồm các khối lệnh có nhiệm vụ thực hiện chức năng nào đó

## 2. Ý nghĩa 
- Có khả năng tái sử dụng lại một nhóm các khối lệnh
- Truyền tham chiếu vào trong hàm
- Code dễ đọc hơn
- Dễ tìm lỗi
## 3. Sửa lỗi chương trình
- Chương trình không thể thực hiện được vì khi ta khởi tạo biến a, b trong hàm main thì a và b đã nhận giá trị đó, ta cần sử dụng con trỏ để truyền tham chiếu đến biến a và b tại địa chỉ bộ nhớ của nó, chứ không chỉ sao chép giá trị của nó
- Sửa lỗi:
```
#include <stdio.h>

void swap(int *a, int *b)
{
    int tmp = *a;
    *a = *b;
    *b = tmp;
}
int main()
{
    int a = 100, b = 123456;
    swap(&a, &b);
    printf("a = %d\nb = %d", a, b);
}
```
