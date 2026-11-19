# Chất lượng, Kiểm định & Phát hành — QLCH (`QUALITY_AND_RELEASE.md`)

- **Mã dự án:** `QLCH` — Hệ thống Quản lý Chuỗi Cửa hàng, Kho bãi & Thương mại Điện tử Hợp nhất (`04 Phân hệ Tách biệt: SYS-ADMIN | WMS | STORE & POS | ECOM & TMS`)
- **Mã công việc:** `QLCH-QA-01` (`#6`)
- **Căn cứ quyết định:** [`QLCH-D002`, `QLCH-D003`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/01-quan-ly/DECISIONS.md), [`02-nghiep-vu/TEST_TRANSACTIONS_AND_BA_AMBIGUITY_REVIEW.md`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/02-nghiep-vu/TEST_TRANSACTIONS_AND_BA_AMBIGUITY_REVIEW.md)
- **Chuẩn kiểm thử áp dụng:** `3.DOC_AI/skills/qa-test-case/SKILL.md` (Biểu mẫu `X02`)
- **Ngày cập nhật:** `2026-11-19`
- **Phụ trách:** `QA Lead (Test Lead)` phối hợp `BA Lead` & `Tech Lead`

---

## 1. Chiến lược Kiểm thử & Phân bổ Đội ngũ Tester theo 04 Phân hệ (`QLCH-D003`)

Toàn bộ **21 Use Cases** của hệ thống `QLCH` được tách nhỏ thành **60 Giao dịch nguyên tử (`Atomic Transactions`)** và **120 Kịch bản Kiểm thử (`Test Cases` chuẩn `X02`)** tại tài liệu [`02-nghiep-vu/TEST_TRANSACTIONS_AND_BA_AMBIGUITY_REVIEW.md`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/02-nghiep-vu/TEST_TRANSACTIONS_AND_BA_AMBIGUITY_REVIEW.md), phân công cho 04 tổ Tester chuyên trách:

| Tổ Kiểm thử | Phân hệ phụ trách (`QLCH-D003`) | Phạm vi Use Cases & Transactions | Trọng tâm Kiểm định Bắt buộc (`Zero-Defect Invariants`) |
| :---: | :--- | :--- | :--- |
| **`QA-T1`** | **1. Quản trị ứng dụng (`SYS-ADMIN`)**<br>`@qlch/admin-portal` (`P1 MVP`) | `UC-ADM-01`, `UC-WMS-02`, `UC-WMS-03`<br>(`TRX-ADM-01..11`) | • Cách ly quyền `RBAC` giữa 4 cổng Portal và theo điểm Kho/Cửa hàng (`Location-scoped`).<br>• Ẩn 100% `Giá vốn MAC` & `Lãi gộp` đối với nhân viên vận hành.<br>• Xác thực 2 lớp `PIN/TOTP` cục bộ (`$0 First`) & tính bất biến (`Append-only`) của `system_audit_logs`.<br>• Khóa tự động `Hard Compliance Lock` khi bất kỳ giấy phép nào trong 17 loại giấy phép hết hạn. |
| **`QA-T2`** | **2. Quản lý kho bãi (`WMS`)**<br>`@qlch/wms-portal` (**Trọng tâm `P1 MVP`**) | `UC-WMS-01`, `UC-WMS-04` .. `UC-WMS-09`<br>(`TRX-WMS-01..22`) | • Sơ đồ kho 2D (`Zone/Rack/Bin`) & Khóa chặn cứng trần `Max NEQ` (tính cả hàng `In-Transit` đang đi tới kho nhận).<br>• Chặn cứng xếp chung hàng kỵ nhau (`Kíp nổ` vs `Thuốc nổ`; `Amoni Nitrat` vs `Dầu mỡ/Axít`) theo `QCVN 01:2019/BCT`.<br>• Khớp 100% phương trình Thẻ kho bất biến, Báo cáo `NXT` và Giá vốn bình quân `MAC` (`BM-KHO-01..04`).<br>• Phản hồi quét mã vạch `< 1 giây` và bảo toàn 100% chốt chặn an toàn ngay cả khi `Offline` (`IndexedDB`). |
| **`QA-T3`** | **3. Quản lý cửa hàng (`STORE & POS`)**<br>`@qlch/store-pos-portal` (`P2`) | `UC-STR-01`, `UC-POS-01` .. `UC-POS-04`<br>(`TRX-STR-01..02`, `TRX-POS-01..07`) | • Giới hạn trưng bày `Max NEQ` trên sơ đồ 2D cửa hàng.<br>• Kết ca mù theo mệnh giá tiền (`BM-POS-03`).<br>• Tốc độ thanh toán `POS < 15s/đơn`, `VietQR` cục bộ (`$0`), bắt buộc `CCCD 12 số >= 18 tuổi` + khóa giá trần khi bán Pháo hoa `Z121`, đẩy 100% hàng trả nghi ngờ ẩm/rách vào `Kho Cách ly (Quarantine)`. |
| **`QA-T4`** | **4. Cổng TMĐT Online & Giao vận (`ECOM & TMS`)**<br>`@qlch/ecom-portal` (`P2`) | `UC-ECM-01` .. `UC-ECM-03`, `UC-TMS-01` .. `UC-TMS-03`<br>(`TRX-ECM-01..03`, `TRX-TMS-01..03`) | • Chống bán vượt tồn (`Zero Overselling`) giữa `ECOM` và `POS` qua cơ chế khóa `Reserved Stock`.<br>• Bộ lọc pháp lý ẩn tuyệt đối `VLNCN` trên `B2C Storefront`.<br>• Kiểm soát Xe Hàng Loại 1 (`Biển UN`), Giấy phép vận chuyển `C06/PC07 <= 7 ngày`, đối soát `COD 100%` & nhắc hạn `07 ngày` nộp trả giấy phép gốc. |

---

## 2. Tiêu chí Hoàn thành & Cổng Chất lượng (`Definition of Done — DoD`)

1. **Độ chính xác Số liệu Tồn kho & Tài chính (`100% Accuracy`):**
   - 100% giao dịch biến động tồn kho (`On-hand`, `Reserved`, `In-Transit`, `Available`) khớp tuyệt đối với sổ cái `stock_ledger_entries`.
   - Công thức Giá vốn bình quân gia quyền (`MAC`), làm tròn tiền hàng VNĐ (`0` chữ số thập phân) và phân bổ chi phí nhập kho không có sai số lệch dòng.
2. **Độ an toàn Pháp lý Hàng đặc thù (`Zero Compliance Bypass`):**
   - 100% kịch bản kiểm thử chặn cứng (`Negative / Hard-Lock` cho `Max NEQ`, cách ly `Kíp nổ` vs `Thuốc nổ`, giấy phép hết hạn, giá trần `Z121`, định danh `CCCD 12 số`) đạt `PASS` ở cả tầng Giao diện (`UI/IndexedDB`), tầng `API` và tầng `Database Trigger`.
3. **Hiệu năng & Ràng buộc Hạ tầng (`$0 First / Local Library-First`):**
   - Tốc độ quét mã vạch `< 1 giây/thao tác` (cả Online và Offline); tốc độ lên đơn `POS < 15 giây/đơn`.
   - Chi phí dịch vụ bên thứ 3 bằng **`$0`** (không phát sinh bất kỳ lời gọi API trả phí nào khi chưa có xác nhận của Chủ dự án).

---

## 3. Quy trình Rà soát Điểm mờ Nghiệp vụ (`QA Lead` $\leftrightarrow$ `BA Lead`) & Phát hành

1. **Cơ chế phản hồi sớm (`Shift-Left QA Review`):**
   - Trước mỗi cổng (`Brief`, `G1`, `G3`), `Test Lead` rà soát chéo `USE_CASES.md`, `REQUIREMENTS.md` và `DATABASE_SCHEMA.md` để trích xuất danh sách **Điểm mờ nghiệp vụ (`AMB-xx`)** gửi `BA Lead`.
   - `BA Lead` đánh giá, phân loại thành **Nhóm A (`Task cần điều chỉnh tài liệu/code`)** và **Nhóm B (`Issue cần làm rõ với Chủ dự án`)** trên GitHub repo `theGonlyK/QLCH`.
2. **Quy trình Kiểm thử & Phát hành / Rollback:**
   - Mọi PR vào nhánh `main` bắt buộc vượt qua bộ kiểm thử `Unit Test`, `Integration Test` (bao gồm các Database Triggers `INV-DB-01..05`) và bộ kịch bản `X02` của phân hệ tương ứng.
   - Sao lưu (`Backup`) cơ sở dữ liệu `PostgreSQL` tự động trước mỗi lần chạy `Migration`; hỗ trợ `Rollback` tức thời về bản snapshot gần nhất nếu phát hiện bất kỳ sai lệch nào trên Sổ cái Thẻ kho.
