# Tổng hợp Kết quả Khảo sát Thị trường POS / Chuỗi Cửa hàng & Bộ Biểu mẫu Tham khảo cho BA / UX (`QLCH-MKT-01`)

- **Mã công việc:** `QLCH-MKT-01` (GitHub Issue [`#3`](https://github.com/theGonlyK/QLCH/issues/3))
- **Vai trò thực hiện:** `Marketing Lead`
- **Ngày hoàn thành:** `2026-11-14`
- **Mục đích:** Điểm neo tra cứu nhanh trong thư mục `02-nghiep-vu/` của dự án `QLCH`, kết nối trực tiếp bộ câu hỏi Cổng Brief (`Q-QLCH-01` $\rightarrow$ `Q-QLCH-05` tại [`02-nghiep-vu/REQUIREMENTS.md`](REQUIREMENTS.md)) với 03 bộ tài liệu khảo sát thị trường và biểu mẫu nghiệp vụ đã hoàn thành.

---

## 1. Liên kết Nhanh tới Bộ Tài liệu Đầu ra (`QLCH-MKT-01`)

1. **`REF-MKT-003` — Báo cáo Khảo sát Đối thủ & Xu hướng Phần mềm POS / Chuỗi Cửa hàng tại Việt Nam:**
   - Đường dẫn: [`2.Tai_lieu_tham_khao/5.Tai_lieu_marketing/BAO_CAO_KHAO_SAT_PHAN_MEM_POS_VA_CHUOI_CUA_HANG_VN.md`](../2.Tai_lieu_tham_khao/5.Tai_lieu_marketing/BAO_CAO_KHAO_SAT_PHAN_MEM_POS_VA_CHUOI_CUA_HANG_VN.md)
   - Nội dung chính: Khảo sát 5 nền tảng (`KiotViet`, `Sapo POS`, `Haravan HaraRetail`, `PosApp`, `Odoo POS`), phân khúc giá (`170.000đ – 3.000.000đ+/tháng`), xu hướng HĐĐT khởi tạo từ máy tính tiền theo **Nghị định `70/2025/NĐ-CP`**, tách bạch *Dữ kiện – Diễn giải – Giả thuyết* và kế hoạch khảo sát thực địa đề xuất.
2. **`REF-BIZ-003` — Danh mục & Ma trận Đối sánh 12 Nhóm Nghiệp vụ Phần mềm POS / Chuỗi Bán lẻ:**
   - Đường dẫn: [`2.Tai_lieu_tham_khao/3.Tai_lieu_nghiep_vu/DANH_MUC_VA_MA_TRAN_PHAN_MEM_POS_CHUOI_BAN_LE_VN.md`](../2.Tai_lieu_tham_khao/3.Tai_lieu_nghiep_vu/DANH_MUC_VA_MA_TRAN_PHAN_MEM_POS_CHUOI_BAN_LE_VN.md)
   - Nội dung chính: Đối sánh chi tiết 12 nhóm chức năng (Cấu trúc SKU/Biến thể/Lô-HSD/IMEI, Đa kho & Điều chuyển 2 bước `In-Transit`, Bán hàng POS & Tạm lưu đơn, Offline POS `IndexedDB`, Kiểm kê kho, Nhập hàng & Công nợ NCC, Đổi trả hàng, Bảng giá chi nhánh & Loyalty, Bàn giao ca & RBAC chống gian lận, VietQR động & HĐĐT MTT, Thiết bị ngoại vi).
3. **`REF-MKT-004` — Bộ 07 Biểu mẫu Hóa đơn Bán hàng POS, Phiếu Nhập/Xuất/Điều chuyển Kho & Biên bản Kiểm kê Chuẩn Việt Nam:**
   - Đường dẫn: [`2.Tai_lieu_tham_khao/3.Tai_lieu_nghiep_vu/BO_BIEU_MAU_HOA_DON_POS_VA_XUAT_NHAP_KIEM_KHO_VN.md`](../2.Tai_lieu_tham_khao/3.Tai_lieu_nghiep_vu/BO_BIEU_MAU_HOA_DON_POS_VA_XUAT_NHAP_KIEM_KHO_VN.md)
   - Nội dung chính: Đặc tả trường dữ liệu, công thức tính toán và bản vẽ bố cục (ASCII Wireframe) cho:
     - `BM-POS-01`: Hóa đơn bán hàng POS khổ nhiệt `K80 (80mm)` & `K57 (58mm)` kèm VietQR động & chuẩn thông tin NĐ `70/2025/NĐ-CP`.
     - `BM-POS-02`: Phiếu Đổi / Trả hàng & Hoàn tiền tại quầy POS.
     - `BM-POS-03`: Biên bản Bàn giao ca & Đối soát két tiền thu ngân (`Shift Handover`).
     - `BM-KHO-01`: Phiếu Nhập kho (`Mẫu số 01-VT` — TT133 & TT200/TT-BTC).
     - `BM-KHO-02`: Phiếu Xuất kho & Xuất hủy (`Mẫu số 02-VT` — TT133 & TT200/TT-BTC).
     - `BM-KHO-03`: Phiếu Điều chuyển kho liên chi nhánh 2 bước (`In-Transit Stock Transfer`).
     - `BM-KHO-04`: Biên bản Kiểm kê hàng hóa & Cân bằng kho (`Mẫu số 05-VT` — TT133 & TT200/TT-BTC).
4. **Sổ đăng ký tri thức đề xuất đồng bộ:** [`SO_DANG_KY_TRI_THUC.md`](../SO_DANG_KY_TRI_THUC.md).

---

## 2. Bảng Ánh xạ Kết quả Khảo sát vào 05 Câu hỏi Cổng Brief (`02-nghiep-vu/REQUIREMENTS.md`)

> **Lưu ý quan trọng (`RULES_CORE.md`):** Bảng dưới đây cung cấp góc nhìn tham chiếu thị trường để hỗ trợ `BA Lead`, `UX Lead`, `Tech Lead` và Chủ dự án khi chốt Cổng Brief; mọi quyết định phạm vi vẫn ở trạng thái **`Cần xác nhận`** bởi Chủ dự án.

| Mã câu hỏi Cổng Brief | Câu hỏi tại `REQUIREMENTS.md` | Bằng chứng Thị trường & Điểm cần lưu ý từ `QLCH-MKT-01` |
| :---: | :--- | :--- |
| **`Q-QLCH-01`** | Ngành hàng & Mô hình chuỗi cửa hàng mục tiêu? | • Thị trường chia rõ 4 kiểu SKU theo ngành: (1) **Đa ĐVT quy đổi** (Tạp hóa/Siêu thị), (2) **Biến thể Màu/Size** (Thời trang), (3) **Lô/Hạn sử dụng** (Thuốc/Mỹ phẩm/Thực phẩm), (4) **Serial/IMEI** (Điện máy).<br>• Cần xác nhận sớm kiểu SKU nào đưa vào P1 MVP để tránh thiết kế thừa hoặc thiếu cấu trúc bảng `Product`. |
| **`Q-QLCH-02`** | Phạm vi các phân hệ cốt lõi trong P1 MVP? | • Bộ chứng từ lõi không thể thiếu của mọi cửa hàng: **Hóa đơn POS (`BM-POS-01`)**, **Đổi trả (`BM-POS-02`)**, **Bàn giao ca (`BM-POS-03`)**, **Nhập kho (`BM-KHO-01`)**, **Xuất/Hủy (`BM-KHO-02`)**, **Điều chuyển liên chi nhánh (`BM-KHO-03`)**, và **Kiểm kê kho (`BM-KHO-04`)**. |
| **`Q-QLCH-03`** | Định hướng trải nghiệm & Loại hình thiết bị (Client)? | • 100% phần mềm POS thực chiến dùng **giao diện 2D tốc độ cao (hỗ trợ phím tắt `F1–F12` + Touch Grid + Tạm lưu nhiều bill)** tại quầy thu ngân để không làm khách phải chờ.<br>• Nếu Chủ dự án muốn kết hợp yếu tố không gian trực quan 2D/3D, nên đặt ở **Bản đồ chuỗi chi nhánh / Sơ đồ kệ kho** cho Quản lý, tách biệt với màn hình tính tiền nhanh của Thu ngân. |
| **`Q-QLCH-04`** | Vận hành Offline tại quầy, Thiết bị ngoại vi & Nguyên tắc `$0 First`? | • Mô hình **Odoo POS** (`IndexedDB` Local Cache + `Sync Queue` trên trình duyệt Web/PWA) chứng minh có thể bán hàng Offline, in bill nhiệt `K80/K57`, quét mã vạch `Keyboard Wedge` và sinh mã **VietQR động cục bộ** với chi phí bên thứ ba bằng **`$0`**. |
| **`Q-QLCH-05`** | Thị trường mục tiêu đầu tiên & KPI thành công? | • Gợi ý thước đo vận hành thực tế trong ngành bán lẻ: Thời gian hoàn tất 1 đơn POS trung bình (`< 15 giây`), độ chính xác đối soát két tiền cuối ca (`100%`), và độ khớp tồn kho giữa các chi nhánh (`sai lệch = 0` trên các phiếu điều chuyển `In-Transit`). |
