**chương trình C** tìm **Ước số chung lớn nhất (UCLN)** và **Bội số chung nhỏ nhất (BCNN)** của hai số `a` và `b`.

---

## 📌 Ý tưởng

* **UCLN**: dùng **thuật toán Euclid**
* **BCNN**:
  [
  BCNN(a, b) = \frac{|a \times b|}{UCLN(a, b)}
  ]

---

## ✅ Chương trình C hoàn chỉnh

```c
#include <stdio.h>
#include <stdlib.h>  // abs()

int UCLN(int a, int b) {
    a = abs(a);
    b = abs(b);

    while (b != 0) {
        int r = a % b;
        a = b;
        b = r;
    }
    return a;
}

int BCNN(int a, int b) {
    if (a == 0 || b == 0)
        return 0;
    return abs(a * b) / UCLN(a, b);
}

int main() {
    int a, b;
    printf("Nhap a va b: ");
    scanf("%d %d", &a, &b);

    printf("UCLN(%d, %d) = %d\n", a, b, UCLN(a, b));
    printf("BCNN(%d, %d) = %d\n", a, b, BCNN(a, b));

    return 0;
}
```

---

## 🧪 Ví dụ chạy

```
Nhap a va b: 12 18
UCLN(12, 18) = 6
BCNN(12, 18) = 36
```

---
Dưới đây là **chương trình C kiểm tra số nguyên tố** (đúng chuẩn, dễ hiểu) 👇

---

## 📌 Số nguyên tố là gì?

* Là số **lớn hơn 1**
* Chỉ chia hết cho **1 và chính nó**

---

## ✅ Chương trình C kiểm tra số nguyên tố

```c
#include <stdio.h>

int laSoNguyenTo(int n) {
    if (n < 2) return 0;
    for (int i = 2; i * i <= n; i++)
        if (n % i == 0) return 0;
    return 1;
}

int main() {
    int n;
    printf("Nhap n: ");
    scanf("%d", &n);

    if (laSoNguyenTo(n))
        printf("%d la so nguyen to\n", n);
    else
        printf("%d khong phai la so nguyen to\n", n);

    return 0;
}
```

---

## 🧪 Ví dụ chạy

```
Nhap n: 17
17 la so nguyen to
```

---

OK 👍 mình **chuyển sang BÀI TẬP C (chuỗi)** và **rút gọn – dễ nhớ – đúng kiểu sinh viên học C**.
👉 Mỗi bài: **ý tưởng + code C ngắn gọn**.

---

# 📌 BÀI TẬP CHUỖI TRONG C (TỔNG HỢP)

---

## 1️⃣ In chuỗi

```c
#include <stdio.h>

int main() {
    char s[100];
    fgets(s, 100, stdin);
    printf("%s", s);
    return 0;
}
```

---

## 2️⃣ Tìm độ dài chuỗi

```c
#include <stdio.h>

int main() {
    char s[100];
    int dem = 0;
    fgets(s, 100, stdin);

    while (s[dem] != '\0' && s[dem] != '\n')
        dem++;

    printf("Do dai = %d", dem);
    return 0;
}
```

---

## 3️⃣ Đếm số lần xuất hiện của 1 ký tự

```c
#include <stdio.h>

int main() {
    char s[100], c;
    int dem = 0;
    fgets(s, 100, stdin);
    scanf("%c", &c);

    for (int i = 0; s[i] != '\0'; i++)
        if (s[i] == c) dem++;

    printf("%d", dem);
    return 0;
}
```

---

## 4️⃣ Sao chép chuỗi

```c
#include <stdio.h>

int main() {
    char s1[100], s2[100];
    int i = 0;
    fgets(s1, 100, stdin);

    while (s1[i] != '\0') {
        s2[i] = s1[i];
        i++;
    }
    s2[i] = '\0';

    printf("%s", s2);
    return 0;
}
```

---

## 5️⃣ Đảo ngược chuỗi

```c
#include <stdio.h>
#include <string.h>

int main() {
    char s[100];
    fgets(s, 100, stdin);
    int n = strlen(s) - 1;

    for (int i = 0; i < n / 2; i++) {
        char t = s[i];
        s[i] = s[n - i - 1];
        s[n - i - 1] = t;
    }
    printf("%s", s);
    return 0;
}
```

---

## 6️⃣ Tìm kiếm chuỗi con

```c
#include <stdio.h>
#include <string.h>

int main() {
    char s[100], sub[50];
    fgets(s, 100, stdin);
    fgets(sub, 50, stdin);

    if (strstr(s, sub))
        printf("Co");
    else
        printf("Khong");

    return 0;
}
```

---

## 7️⃣ Nối chuỗi

```c
#include <stdio.h>
#include <string.h>

int main() {
    char s1[100], s2[50];
    fgets(s1, 100, stdin);
    fgets(s2, 50, stdin);

    strcat(s1, s2);
    printf("%s", s1);
    return 0;
}
```

---

## 8️⃣ Đảo ngược từng từ trong chuỗi

**Ví dụ:** `lap trinh C` → `pal hnirt C`

```c
#include <stdio.h>
#include <string.h>

void dao(char s[], int l, int r) {
    while (l < r) {
        char t = s[l];
        s[l++] = s[r];
        s[r--] = t;
    }
}

int main() {
    char s[100];
    fgets(s, 100, stdin);
    int n = strlen(s), i = 0;

    for (int j = 0; j <= n; j++) {
        if (s[j] == ' ' || s[j] == '\0' || s[j] == '\n') {
            dao(s, i, j - 1);
            i = j + 1;
        }
    }
    printf("%s", s);
    return 0;
}
```

---

## 9️⃣ Chuyển chuỗi thành số nguyên

```c
#include <stdio.h>

int main() {
    char s[20];
    int n = 0;
    fgets(s, 20, stdin);

    for (int i = 0; s[i] >= '0' && s[i] <= '9'; i++)
        n = n * 10 + (s[i] - '0');

    printf("%d", n);
    return 0;
}
```

---

## 🔟 Chuyển chuỗi thành chữ HOA

```c
#include <stdio.h>
#include <ctype.h>

int main() {
    char s[100];
    fgets(s, 100, stdin);

    for (int i = 0; s[i]; i++)
        s[i] = toupper(s[i]);

    printf("%s", s);
    return 0;
}
```

---

## 1️⃣1️⃣ Chuyển chuỗi thành chữ thường

```c
#include <stdio.h>
#include <ctype.h>

int main() {
    char s[100];
    fgets(s, 100, stdin);

    for (int i = 0; s[i]; i++)
        s[i] = tolower(s[i]);

    printf("%s", s);
    return 0;
}
```

---

# 🧠 BẢNG GHI NHỚ NHANH (ĐI THI)

| Bài          | Hàm / Ý             |
| ------------ | ------------------- |
| Độ dài       | vòng `while`        |
| Sao chép     | gán từng ký tự      |
| Tìm          | `strstr()`          |
| Nối          | `strcat()`          |
| Hoa / thường | `toupper / tolower` |
| Đảo          | đổi `s[i] ↔ s[j]`   |

---
---

# 📌 CHƯƠNG TRÌNH QUẢN LÝ SINH VIÊN (C)

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

/* ===== CẤU TRÚC SINH VIÊN ===== */
typedef struct {
    int maSV;
    char ten[100];
    char gioiTinh[10];
    int tuoi;
    float diemToan;
    float diemLy;
    float diemHoa;
    float diemTrungBinh;
    char hocLuc[20];
} SinhVien;

/* ===== BIẾN TOÀN CỤC ===== */
int maTuDong = 1;

/* ===== HÀM HỖ TRỢ ===== */
void xoaXuongDong(char *s) {
    s[strcspn(s, "\n")] = '\0';
}

void tinhDiemVaHocLuc(SinhVien *sv) {
    sv->diemTrungBinh = (sv->diemToan + sv->diemLy + sv->diemHoa) / 3;

    if (sv->diemTrungBinh >= 8)
        strcpy(sv->hocLuc, "Gioi");
    else if (sv->diemTrungBinh >= 6.5)
        strcpy(sv->hocLuc, "Kha");
    else if (sv->diemTrungBinh >= 5)
        strcpy(sv->hocLuc, "Trung Binh");
    else
        strcpy(sv->hocLuc, "Yeu");
}

int timViTriTheoID(SinhVien *ds, int soLuong, int id) {
    for (int i = 0; i < soLuong; i++)
        if (ds[i].maSV == id)
            return i;
    return -1;
}

/* ===== CHỨC NĂNG 1: THÊM SINH VIÊN ===== */
void themSinhVien(SinhVien **ds, int *soLuong) {
    SinhVien sv;
    sv.maSV = maTuDong++;

    printf("Nhap ten: ");
    fgets(sv.ten, 100, stdin);
    xoaXuongDong(sv.ten);

    printf("Nhap gioi tinh: ");
    fgets(sv.gioiTinh, 10, stdin);
    xoaXuongDong(sv.gioiTinh);

    printf("Nhap tuoi: ");
    scanf("%d", &sv.tuoi);

    printf("Nhap diem Toan Ly Hoa: ");
    scanf("%f %f %f", &sv.diemToan, &sv.diemLy, &sv.diemHoa);
    getchar();

    tinhDiemVaHocLuc(&sv);

    *ds = realloc(*ds, (*soLuong + 1) * sizeof(SinhVien));
    (*ds)[*soLuong] = sv;
    (*soLuong)++;

    printf("Da them sinh vien!\n");
}

/* ===== CHỨC NĂNG 2: CẬP NHẬT ===== */
void capNhatSinhVien(SinhVien *ds, int soLuong) {
    int id;
    printf("Nhap ID can cap nhat: ");
    scanf("%d", &id);
    getchar();

    int vt = timViTriTheoID(ds, soLuong, id);
    if (vt == -1) {
        printf("Khong tim thay sinh vien!\n");
        return;
    }

    printf("Nhap ten moi: ");
    fgets(ds[vt].ten, 100, stdin);
    xoaXuongDong(ds[vt].ten);

    printf("Nhap gioi tinh moi: ");
    fgets(ds[vt].gioiTinh, 10, stdin);
    xoaXuongDong(ds[vt].gioiTinh);

    printf("Nhap tuoi moi: ");
    scanf("%d", &ds[vt].tuoi);

    printf("Nhap diem Toan Ly Hoa moi: ");
    scanf("%f %f %f",
          &ds[vt].diemToan,
          &ds[vt].diemLy,
          &ds[vt].diemHoa);
    getchar();

    tinhDiemVaHocLuc(&ds[vt]);
    printf("Cap nhat thanh cong!\n");
}

/* ===== CHỨC NĂNG 3: XÓA ===== */
void xoaSinhVien(SinhVien **ds, int *soLuong) {
    int id;
    printf("Nhap ID can xoa: ");
    scanf("%d", &id);
    getchar();

    int vt = timViTriTheoID(*ds, *soLuong, id);
    if (vt == -1) {
        printf("Khong tim thay sinh vien!\n");
        return;
    }

    for (int i = vt; i < *soLuong - 1; i++)
        (*ds)[i] = (*ds)[i + 1];

    (*soLuong)--;
    *ds = realloc(*ds, (*soLuong) * sizeof(SinhVien));

    printf("Da xoa sinh vien!\n");
}

/* ===== CHỨC NĂNG 4: TÌM THEO TÊN ===== */
void timTheoTen(SinhVien *ds, int soLuong) {
    char tenCanTim[100];
    printf("Nhap ten can tim: ");
    fgets(tenCanTim, 100, stdin);
    xoaXuongDong(tenCanTim);

    for (int i = 0; i < soLuong; i++) {
        if (strstr(ds[i].ten, tenCanTim)) {
            printf("%d - %s - %.2f - %s\n",
                   ds[i].maSV,
                   ds[i].ten,
                   ds[i].diemTrungBinh,
                   ds[i].hocLuc);
        }
    }
}

/* ===== CHỨC NĂNG 5: SẮP XẾP THEO GPA ===== */
void sapXepTheoDiem(SinhVien *ds, int soLuong) {
    for (int i = 0; i < soLuong - 1; i++)
        for (int j = i + 1; j < soLuong; j++)
            if (ds[i].diemTrungBinh < ds[j].diemTrungBinh) {
                SinhVien tmp = ds[i];
                ds[i] = ds[j];
                ds[j] = tmp;
            }
}

/* ===== CHỨC NĂNG 6: SẮP XẾP THEO TÊN ===== */
void sapXepTheoTen(SinhVien *ds, int soLuong) {
    for (int i = 0; i < soLuong - 1; i++)
        for (int j = i + 1; j < soLuong; j++)
            if (strcmp(ds[i].ten, ds[j].ten) > 0) {
                SinhVien tmp = ds[i];
                ds[i] = ds[j];
                ds[j] = tmp;
            }
}

/* ===== CHỨC NĂNG 7: HIỂN THỊ ===== */
void hienThiDanhSach(SinhVien *ds, int soLuong) {
    printf("\n%-5s %-20s %-6s %-5s %-6s %-6s %-6s %-6s %-10s\n",
           "ID","Ten","GT","Tuoi","Toan","Ly","Hoa","DTB","Hoc luc");

    for (int i = 0; i < soLuong; i++) {
        printf("%-5d %-20s %-6s %-5d %-6.2f %-6.2f %-6.2f %-6.2f %-10s\n",
               ds[i].maSV,
               ds[i].ten,
               ds[i].gioiTinh,
               ds[i].tuoi,
               ds[i].diemToan,
               ds[i].diemLy,
               ds[i].diemHoa,
               ds[i].diemTrungBinh,
               ds[i].hocLuc);
    }
}

/* ===== MENU ===== */
void menu() {
    printf("\n===== QUAN LY SINH VIEN =====\n");
    printf("1. Them sinh vien\n");
    printf("2. Cap nhat sinh vien\n");
    printf("3. Xoa sinh vien\n");
    printf("4. Tim sinh vien theo ten\n");
    printf("5. Sap xep theo diem trung binh\n");
    printf("6. Sap xep theo ten\n");
    printf("7. Hien thi danh sach\n");
    printf("0. Thoat\n");
    printf("Chon: ");
}

/* ===== MAIN ===== */
int main() {
    SinhVien *danhSach = NULL;
    int soLuong = 0;
    int luaChon;

    do {
        menu();
        scanf("%d", &luaChon);
        getchar();

        switch (luaChon) {
            case 1: themSinhVien(&danhSach, &soLuong); break;
            case 2: capNhatSinhVien(danhSach, soLuong); break;
            case 3: xoaSinhVien(&danhSach, &soLuong); break;
            case 4: timTheoTen(danhSach, soLuong); break;
            case 5: sapXepTheoDiem(danhSach, soLuong); break;
            case 6: sapXepTheoTen(danhSach, soLuong); break;
            case 7: hienThiDanhSach(danhSach, soLuong); break;
            case 0: printf("Thoat chuong trinh!\n"); break;
            default: printf("Lua chon khong hop le!\n");
        }
    } while (luaChon != 0);

    free(danhSach);
    return 0;
}
```

---
