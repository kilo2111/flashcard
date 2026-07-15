HỌC TỪ VỰNG SONG NGỮ — Hướng dẫn quản lý file Excel
=======================================================

CẤU TRÚC THƯ MỤC
-----------------
hoc-tu-vung-web/
├── index.html                       ← Trang chủ (chọn Trung / Anh)
├── hoc-tu-vung-trung-viet.html      ← Trang học tiếng Trung
├── hoc-tu-vung-anh-viet.html        ← Trang học tiếng Anh
├── China/
│   ├── manifest.json                ← Danh mục file tiếng Trung (PHẢI cập nhật khi thêm file)
│   ├── HSK4.xlsx                    ← Đặt file Excel vào đây
│   └── (thêm file mới vào đây)
└── English/
    ├── manifest.json                ← Danh mục file tiếng Anh
    ├── IELTS_Academic.xlsx
    └── (thêm file mới vào đây)


CÁCH THÊM FILE EXCEL MỚI
--------------------------
Ví dụ: thêm bộ từ vựng "HSK5.xlsx" vào thư mục China/

BƯỚC 1: Copy file Excel vào thư mục China/
   → China/HSK5.xlsx

BƯỚC 2: Mở file China/manifest.json bằng Notepad, thêm 1 dòng:
   (trước dấu ngoặc vuông cuối cùng "]")

   Trước khi sửa:
   {
     "files": [
       { "name": "HSK4.xlsx", "label": "HSK 4 — Từ vựng cấp 4", "desc": "983 từ", "path": "China/HSK4.xlsx" }
     ]
   }

   Sau khi thêm:
   {
     "files": [
       { "name": "HSK4.xlsx", "label": "HSK 4 — Từ vựng cấp 4", "desc": "983 từ",  "path": "China/HSK4.xlsx" },
       { "name": "HSK5.xlsx", "label": "HSK 5 — Từ vựng cấp 5", "desc": "1500 từ", "path": "China/HSK5.xlsx" }
     ]
   }
   ↑ Chú ý: thêm dấu phẩy sau dòng trước đó!

BƯỚC 3: Upload lại TOÀN BỘ thư mục hoc-tu-vung-web/ lên Netlify
   → Vào https://app.netlify.com
   → Chọn site của bạn → Deploys → kéo thả thư mục lên


CẤU TRÚC FILE manifest.json (giải thích từng trường)
------------------------------------------------------
{
  "folder": "China",                 ← tên thư mục (chỉ để ghi chú)
  "description": "...",             ← mô tả (chỉ để ghi chú)
  "files": [
    {
      "name":  "HSK4.xlsx",          ← tên file thực tế trong thư mục
      "label": "HSK 4 — Cấp 4",     ← tên hiển thị trên web (đẹp)
      "desc":  "983 từ · ...",       ← mô tả ngắn hiển thị bên dưới label
      "path":  "China/HSK4.xlsx"     ← đường dẫn từ thư mục gốc (QUAN TRỌNG)
    }
  ]
}


HOST LÊN NETLIFY (lần đầu)
---------------------------
1. Mở trình duyệt → https://app.netlify.com/drop
2. Kéo thả TOÀN BỘ thư mục "hoc-tu-vung-web" vào trang
3. Chờ ~10 giây → nhận link dạng: https://xyz-abc-123.netlify.app
4. Chia sẻ link đó cho mọi người

LƯU Ý QUAN TRỌNG:
- Kéo thả THƯMỤC (hoc-tu-vung-web), KHÔNG phải từng file lẻ
- Đăng ký tài khoản Netlify miễn phí để giữ link vĩnh viễn
- Sau khi đăng ký: Site settings → Change site name → đặt tên đẹp hơn


CẤU TRÚC FILE EXCEL (cột bắt buộc)
------------------------------------
Tiếng Trung (6 cột):
  Tiếng trung | Tiếng trung (phiên âm) | Từ loại | Tiếng Việt | Ví Dụ | Nghĩa câu ví dụ

Tiếng Anh (6 cột):
  Tiếng Anh | Phiên âm (IPA) | Từ loại | Tiếng Việt | Ví Dụ | Nghĩa câu ví dụ

Dòng đầu tiên là tiêu đề cột, từ dòng 2 trở đi là dữ liệu.
