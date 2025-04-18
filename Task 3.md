---
title: struct

---

# I. Lí thuyết
## 1. Cấu trúc
```
struct name 
{
    type a1;
    type a2;
    ...
    type an;
}
```
## 2. Tính chất
- Gồm các phần tử với nhiều kiểu dữ liệu khác nhau
- Có thể truyền vào hàm cả cấu trúc mà mình đã định nghĩa
- Có cấu trúc lồng nhau

## 3. Ý nghĩa
- Dùng để quản lí các danh sách gồm nhiều dữ liệu với nhiều kiểu dữ liệu khác nhau

## 4. Cách sử dụng
- Định nghĩa một cấu trúc, với các thành phần cần dùng
- Truy cập đến các thành phần bằng cách gọi tên hoặc con trỏ

## 5. Phân biệt

| array                         | union                                                          | struct                           |
| ----------------------------- | -------------------------------------------------------------- | -------------------------------- |
| các biến cùng kiểu dữ liệu    | khác kiểu dữ liệu, nhưng tồn tại trong một thời gian nhất định | khác kiểu dữ liệu                |
| mỗi phần tử có vùng nhớ riêng | dùng chung vùng nhớ                                            | mỗi thành phần có vùng nhớ riêng |
| truy cập mọi phần tử          | truy cập 1 thành phần tại 1 thời điểm                          | truy cập mọi thành phần          |
|truy cập bằng chỉ số|truy cập bằng tên thành phần|truy cập bằng tên thành phần|

# II. Bài tập
```
#include <stdio.h>
#include <string.h>
#include <conio.h>
#include <stdlib.h>

typedef struct
{
    char ho_ten[50];
    int tuoi;
    float diem_tb;
} sv;

void nhap(sv *x)
{
    printf("Nhap ten: "); fflush(stdin); gets(x->ho_ten);
    printf("Nhap tuoi:"); fflush(stdin); scanf("%d", &x->tuoi);
    printf("Nhap diem:"); scanf("%f", &x->diem_tb);
}
void nhapds(sv a[], int *n)
{
    printf("Nhap so sinh vien:"); scanf("%d", n);
    for(int i=0; i<*n; i++) {
        printf("Nhap thong tin sinh vien thu %d:\n", i+1);
        nhap(&a[i]);
    }
}
void xuatds(sv a[], int n)
{
    printf("\n\tDANH SACH SINH VIEN\n");
    printf("%-5s%-20s%-10s%-10s\n","STT","Ho Ten","Tuoi","Diem trung binh");
    for(int i=0; i<n; i++) {
        printf("%-5d%-20s%-10d%-10.2f\n", i+1, a[i].ho_ten, a[i].tuoi, a[i].diem_tb);
    }
}
int tim(sv a[], int n, char tct[])
{
    for(int i=0; i<n; i++) {
        if(strcmp(a[i].ho_ten, tct)==0) {
            return i;
        }
    }
    return -1;
}
int chen(sv a[], int n)
{
    char svchen[50];
    printf("Nhap ten sinh vien muon chen vao sau: ");
    fflush(stdin);
    gets(svchen);
    int check=tim(a, n, svchen);
    if(check<0) {
        printf("Khong co sinh vien");
        return 0;
    }
    else {
        n++;
        check++;
        for(int i=n; i>check; i--) {
            a[i]=a[i-1];
        }
        printf("Nhap sinh vien can chen:\n");
        nhap(&a[check]);
    }
    return n;
}
int xoa(sv a[], int n)
{
    char svxoa[50];
    printf("Nhap ten sinh vien muon xoa:");
    fflush(stdin);
    gets(svxoa);
    int check = tim(a, n, svxoa);
    if (check<0) printf("Khong co sinh vien");
    else {
        for(int i=check; i<n; i++) {
            a[i]=a[i+1];
        }
        n--;
    }
    return n;
}
void sua(sv a[], int n)
{
    char svsua[50];
    printf("Nhap ten sinh vien muon sua:");
    fflush(stdin);
    gets(svsua);
    int check=tim(a, n, svsua);
    if(check<0) printf("Khong co sinh vien");
    else nhap(&a[check]);
    xuatds(a, n);
}
void menu()
{
    system("cls");
    printf("Chuong trinh quan li sinh vien:\n");
    printf("1. Tao danh sach\n");
    printf("2. In danh sach\n");
    printf("3. Chen them mot sinh vien\n");
    printf("4. Xoa thong tin mot sinh vien\n");
    printf("5. Sua thong tin mot sinh vien\n");
    printf("6. Thoat\n");
}
int main()
{
    sv a[100];
    int n;
    char c;
    do
    {
        menu();
        printf("Moi ban nhap lua chon:"); scanf("%c", &c);
        switch(c)
        {
            case '1': nhapds(a, &n); break;
            case '2': xuatds(a, n); break;
            case '3':   n=chen(a, n);
                        printf("Danh sach sau khi sua:\n");
                        xuatds(a, n); break;
            case '4':   n=xoa(a, n);
                        printf("Danh sach sau khi sua");
                        xuatds(a, n);
                        break;
            case '5': sua(a, n); break;
            case '6': return 0;
            default: printf("Moi lua chon lai\n");
        }
        fflush(stdin);
        getch();
    } while(1);
    return 0;
}
```
