---
title: task 4 btt

---

# I. Lí thuyết
## Danh sách liên kết
- Là một dãy cấu trúc dữ liệu, gồm các nút(node) tạo thành một chuỗi, kết nối với nhau thông qua các liên kết(link)
- Mỗi node gồm 2 phần, dữ liệu(data) của node đó, và tham chiếu đến node kế tiếp.
- Con trỏ Head trỏ vào địa chỉ của node đầu tiên, node cuối cùng trỏ NULL.

# II. Bài tập
## 1. Danh sách quản lí sinh viên
```
#include <stdio.h>
#include <stdlib.h>
#include<string.h>

typedef struct
{
    char name[30];
    int age;
    float gpa;
} sv;
typedef struct node
{
    sv infor;
    struct node *next;
} Node;
Node *head;
Node *GetNode(sv x)
{
    Node *p;
    p=(Node*)malloc(sizeof(Node));
    if(p==NULL) {
        printf("Out of memory");
        exit(1);
    }
    p->infor=x;
    p->next=NULL;
    return p;
}
void InsertEnd(Node *newn)
{
    if(head==NULL) head=newn;
    else {
        Node *tmp=head;
        while(tmp->next!=NULL) {
            tmp=tmp->next;
        }
        tmp->next=newn;
    }
}
void CreateList()
{
    Node *p;
    int n;
    sv a;
    head=NULL;
    printf("Nhap so sinh vien: ");
    scanf("%d", &n);
    for(int i=0; i<n; i++) {
        printf("Nhap thong tin sinh vien thu %d:\n", i+1);
        printf("Ho va ten: "); fflush(stdin); gets(a.name);
        printf("Nhap tuoi: "); fflush(stdin); scanf("%d", &a.age);
        printf("Nhap diem trung binh: "); scanf("%f", &a.gpa);
        p=GetNode(a);
        InsertEnd(p);
    }
}
void PrintfList()
{
    Node *p;
    p=head;
    int i=1;
    printf("\tDanh sach sinh vien\n");
    printf("%-5s%-20s%-10s%-10s\n", "STT", "Ho va ten", "Tuoi", "Diem");
    while(p!=NULL) {
        printf("%-5d%-20s%-10d%-10.2f\n", i, p->infor.name, p->infor.age, p->infor.gpa);
        p=p->next;
        i++;
    }
}
void Insert()
{
    char ten[30];
    printf("Nhap ten sinh vien muon chen sau:");
    fflush(stdin);
    gets(ten);
    Node *p=head;
    while(p!=NULL&&strcmp(ten, p->infor.name)!=0)
        p=p->next;
    if(p==NULL) {
        printf("Khong tim thay sinh vien\n");
        return;
    }
    sv a;
    printf("Nhap thong tin sinh vien can chen: \n");
    printf("Ho va ten: "); fflush(stdin); gets(a.name);
    printf("Nhap tuoi: "); fflush(stdin); scanf("%d", &a.age);
    printf("Nhap diem: "); scanf("%f", &a.gpa);
    Node *newn=GetNode(a);
    newn->next=p->next;
    p->next=newn;
}
void Delete()
{
    char ten[30];
    printf("Nhap ten sinh vien muon xoa:");
    fflush(stdin); gets(ten);
    Node *p=head, *pre=NULL;
    while(p!=NULL&&strcmp(ten, p->infor.name)!=0) {
        pre=p;
        p=p->next;
    }
    if(p==NULL) {
        printf("Khong tim thay sinh vien\n");
        return;
    }
    if(pre==NULL) head=p->next;
    else pre->next=p->next;
    free(p);
}
void Edit()
{
    char ten[30];
    int check=0;
    printf("Nhap ten sinh vien muon sua: ");
    fflush(stdin);
    gets(ten);
    Node *p=head;
    while(p!=NULL) {
        if(strcmp(ten, p->infor.name)==0) {
            printf("Nhap thong tin sinh vien:\n");
            printf("Ho va ten: "); fflush(stdin); gets(p->infor.name);
            printf("Nhap tuoi: "); fflush(stdin); scanf("%d", &p->infor.age);
            printf("Nhap diem: "); scanf("%.2f", &p->infor.gpa);
            check=1;
            break;
        }
        p=p->next;
    }
    if(!check) printf("Khong tim thay sinh vien\n");
}
void Sort()
{
    if(head==NULL||head->next==NULL) return;
    Node *i, *j;
    sv tmp;
    for(i=head; i->next!=NULL; i=i->next) {
        for(j=i->next; j!=NULL; j=j->next) {
            if(i->infor.gpa>j->infor.gpa) {
                tmp=i->infor;
                i->infor=j->infor;
                j->infor=tmp;
            }
        }
    }
}
void menu()
{
    system("cls");
    printf("Chuong trinh quan li sinh vien\n");
    printf("1. Tao danh sach\n");
    printf("2. In danh sach\n");
    printf("3. Chen them sinh vien\n");
    printf("4. Xoa sinh vien\n");
    printf("5. Sua sinh vien\n");
    printf("6. Sap xep theo diem tang dan\n");
    printf("7. Thoat\n");
}
int main()
{
    char c;
    Node *p;
    int n;
    do
    {
        menu();
        printf("Moi nhap lua chon: ");
        scanf("%c", &c);
        switch(c)
        {
            case '1': CreateList(); break;
            case '2': PrintfList();
                        break;
            case '3': Insert();
                        PrintfList();
                        break;
            case '4': Delete();
                        PrintfList();
                        break;
            case '5': Edit();
                        PrintfList();
                        break;
            case '6': Sort();
                        PrintfList();
                        break;
            case '7': return 0;
            default: printf("Moi nhap lai");
        }
        fflush(stdin);
        getch();
    } while(1);
    return 0;
}

```
## 2. Chuyển đổi cơ số
```
#include<stdio.h>
#include<stdbool.h>
#include<stdlib.h>

typedef struct 
{
    int top;
    int data[100];
} stack;

bool isempty(stack p)
{
    if(p.top==-1)
        return true;
    else return false;
}
stack create()
{
    stack *p=(stack*)malloc(sizeof(stack));
    p->top=-1;
    return *p;
}
bool isfull(stack p)
    {
        if(p.top==99)
            return true;
        else return false;
}
bool push(stack *p, int value)
{
    if(isfull(*p))
    {
        printf("FULL");
        return false;
    }
    p->top+=1;
    p->data[p->top]=value;
}
int pop(stack *p)
{
    if(isempty(*p)) {
        return -1;
    }
    int res=p->data[p->top];
    p->top-=1;
    return res;
}
void printstack(stack *p)
{
    while(!isempty(*p))
    {
        printf("%x", pop(p));
    }
}
void doics(int n, int a, stack *p)
{
    while(n!=0) 
    {
        push(p, n%a);
        n/=a;
    }
}
int main()
{
    int n, a;
    printf("Nhap so can chuyen: ");
    scanf("%d", &n);
    printf("Nhap co so can chuyen: ");
    scanf("%d", &a);
    printf("Ket qua: ");
    stack p=create();
    doics(n, a, &p);
    printstack(&p);
    return 0;
}
```
