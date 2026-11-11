# BÀI LÀM – HACKATHON 02

- **Mã đề:** 01
- **Họ tên:** VĂN HŨU LUÂN
- **Lớp:**CNTT1
- **Link repository:** https://github.com/IT101-CNTT1KS26/HCM-CNTT1_Nhapmon-CNTT-HACKATHON02.
- **Hệ điều hành (Windows/macOS):** WINDOWN

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
 ls -force
 mv .\ghi_chu_ban_giao.txt .\docs\
 mkdir backup
 cp .\data\ban_ve_thang_1.xlsx .\backup\
rm *.tmp
 cd..
  get-childitem -recurse -force
```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
Directory: C:\Users\lenovo\Downloads\starter-kit\starter-kit


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026   7:58 AM                ho-boi-website
------         11/3/2026   7:06 AM           2407 bai_lam.md


    Directory:
    C:\Users\lenovo\Downloads\starter-kit\starter-kit\ho-boi-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026   7:58 AM                backup
d-----        11/11/2026   7:53 AM                data
d-----        11/11/2026   7:57 AM                docs
d-----        11/11/2026   7:52 AM                evidence
d-----        11/11/2026   7:53 AM                logs
d-----        11/11/2026   7:50 AM                web
------         11/3/2026   7:06 AM             74 .env
-a----         11/3/2026   7:06 AM           2407 bai_lam.md


    Directory: C:\Users\lenovo\Downloads\starter-kit\starter-kit\ho-boi-
    website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:06 AM           6106 ban_ve_thang_1.xlsx


    Directory: C:\Users\lenovo\Downloads\starter-kit\starter-kit\ho-boi-
    website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:06 AM           6106 ban_ve_thang_1.xlsx


    Directory: C:\Users\lenovo\Downloads\starter-kit\starter-kit\ho-boi-
    website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:06 AM            158 ghi_chu_ban_giao.txt


    Directory: C:\Users\lenovo\Downloads\starter-kit\starter-kit\ho-boi-
    website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:06 AM            972 visit.log


    Directory:
    C:\Users\lenovo\Downloads\starter-kit\starter-kit\ho-boi-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026   7:50 AM                images
------         11/3/2026   7:06 AM            574 app.js
------         11/3/2026   7:06 AM            507 index.html
------         11/3/2026   7:06 AM            460 style.css


    Directory: C:\Users\lenovo\Downloads\starter-kit\starter-kit\ho-boi-
    website\web\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
------         11/3/2026   7:06 AM           3061 logo-aquazone.png

```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
 select-string "status=500" .\logs\visit.log > .\logs\loi_500.txt

```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
2026-01-28 08:24:34 POST /api/thanh-toan status=500
2026-01-28 08:28:45 POST /api/thanh-toan status=500

```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
 (get-content .\logs\visit.log | select-string "status=404").count

```

```text
4

```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
PS C:\Users\lenovo\Downloads\starter-kit\starter-kit\ho-boi-website> '@
>> # Script: tong_hop.ps1
>> #Tac gia: VANHUULUAN
>> # Ngay tao:11-11-2026
>> Write-Host "Dang tao bao cao..."
>> "=== BAO CAO SU CO WEBSITE ===" > logs\tong_hop.txt
>> Get-content logs\visit.log | Select-string "status=404" >> logs\tong_hop.txt
>> > Get-content logs\visit.log | Select-string "status=500" | measure-object >> logs\tong_hop.txt
>> Write-Host "Hoan thanh!"
>> '@ set-content tong_hop.ps1

```

### Nội dung file logs/tong_hop.txt

```text
2026-01-28 08:07:39 GET /tin-tuc status=404
2026-01-28 08:13:01 GET /ve-cu status=404
2026-01-28 08:34:07 GET /images/be-boi-2.jpg status=404
2026-01-28 08:57:24 GET /khuyen-mai-he status=404
2026-01-28 08:24:34 POST /api/thanh-toan status=500
2026-01-28 08:28:45 POST /api/thanh-toan status=500
2026-01-28 08:37:18 POST /api/thanh-toan status=500
2026-01-28 08:42:40 POST /api/mua-ve status=500
2026-01-28 08:45:51 POST /api/thanh-toan status=500


```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [ ] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [ ] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [ ] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 |  |  |  |
| 2 |  |  |  |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** 
- **Expected:** 
- **Actual:** 
- **Log:** 

### Câu tìm kiếm Google

```text
(Ghi câu tìm kiếm vào đây – xoá dòng này)

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/ban_ve_thang_1.xlsx`, không cần ghi vào đây.
