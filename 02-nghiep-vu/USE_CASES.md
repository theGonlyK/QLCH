# Đặc tả Kịch bản Ca sử dụng (Use Cases) — QLCH

- **Mã dự án:** `QLCH` — Hệ thống Quản lý Chuỗi Bán lẻ (`POS`), Kho bãi (`WMS`) & Vận chuyển (`TMS`) Hợp nhất (Hỗ trợ Hàng tiêu dùng/bán lẻ & **Hàng đặc thù: Chất gây cháy nổ, Vật liệu nổ, Pháo**)
- **Phiên bản:** `1.1` (Tích hợp đầy đủ Quyết định Cổng Brief [`QLCH-D002`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/01-quan-ly/DECISIONS.md) và trọn bộ 02 gói khảo sát từ `Marketing Lead` [`QLCH-MKT-01` & `MKT-TO-BA-02`])
- **Ngày cập nhật:** `2026-11-14`
- **Người thực hiện:** `BA Lead` (Kỹ năng `business-analysis/SKILL.md`)
- **Căn cứ truy vết chuẩn:**
  1. **Quyết định phạm vi & lộ trình [`01-quan-ly/DECISIONS.md`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/01-quan-ly/DECISIONS.md) (`QLCH-D002`):**
     - **Giai đoạn 1 (`P1 MVP`):** Tập trung làm trước **Hệ thống Quản lý Kho bãi (`WMS`)** kết hợp **Sơ đồ trực quan 2D (`Zone/Rack/Bin`)**, thiết bị quét mã vạch/in nhiệt, vận hành **Offline-first** và nguyên tắc **`$0 First / Local Library-First`**.
     - **Giai đoạn 2 (`P2`):** Mở rộng **Hệ thống Bán lẻ (`POS`)** và **Hệ thống Vận chuyển (`TMS`)** kết nối trực tiếp vào `WMS`.
  2. **Danh mục yêu cầu nghiệp vụ [`02-nghiep-vu/REQUIREMENTS.md`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/02-nghiep-vu/REQUIREMENTS.md)** (`BR-QLCH-01..02`, `FR-WMS-01..09`, `NFR-QLCH-01..03`, `FR-POS-01..02`, `FR-TMS-01..02`).
  3. **Trọn bộ tài liệu khảo sát & bàn giao từ `Marketing Lead` (`#3 QLCH-MKT-01` & `MKT-TO-BA-02`):**
     - [`REF-BIZ-003`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/2.Tai_lieu_tham_khao/3.Tai_lieu_nghiep_vu/DANH_MUC_VA_MA_TRAN_PHAN_MEM_POS_CHUOI_BAN_LE_VN.md): Ma trận 12 nhóm nghiệp vụ 5 phần mềm (`KiotViet`, `Sapo POS`, `Haravan`, `PosApp`, `Odoo POS`).
     - [`REF-MKT-004`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/2.Tai_lieu_tham_khao/3.Tai_lieu_nghiep_vu/BO_BIEU_MAU_HOA_DON_POS_VA_XUAT_NHAP_KIEM_KHO_VN.md): Bộ 07 biểu mẫu chuẩn Việt Nam (`BM-KHO-01..04` theo Thông tư `133/2016/TT-BTC` & `200/2014/TT-BTC`; `BM-POS-01..03` theo Nghị định `70/2025/NĐ-CP`).
     - [`REF-MKT-005`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/2.Tai_lieu_tham_khao/5.Tai_lieu_marketing/KHAO_SAT_KHO_BAI_VAN_CHUYEN_HANG_DAC_THU_CHAY_NO_PHAO.md) & [`02-nghiep-vu/KHAO_SAT_NGHIEP_VU_KHO_VAN_CHUYEN_HANG_DAC_THU_CHAY_NO.md`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/02-nghiep-vu/KHAO_SAT_NGHIEP_VU_KHO_VAN_CHUYEN_HANG_DAC_THU_CHAY_NO.md): Khảo sát chuyên sâu Kho bãi, Kinh doanh & Vận chuyển **Hàng đặc thù (Chất gây cháy nổ, Vật liệu nổ công nghiệp `VLNCN`, Pháo hoa `Z121`)** cùng ma trận **17 loại Giấy phép/GCN/Chứng chỉ** theo Luật `42/2024/QH15`, Nghị định `137/2020/NĐ-CP`, Nghị định `34/2024/NĐ-CP`, Nghị định `96/2016/NĐ-CP` và `QCVN 01:2019/BCT`.

---

## 1. Danh mục Tác nhân (Actors) & Sơ đồ Tổng quan Hệ thống Use Cases (`P1` & `P2`)

### 1.1. Danh mục Tác nhân (Actors)

| Mã Actor | Tên vai trò (Actor) | Giai đoạn chính | Trách nhiệm cốt lõi trên hệ thống `QLCH` |
| :---: | :--- | :---: | :--- |
| **`ACT-OWN`** | **Chủ hệ thống / Chủ chuỗi (`System Owner`)** | `P1` & `P2` | Cấu hình chuỗi kho/chi nhánh, quản lý hồ sơ 17 loại Giấy phép pháp lý (`ANTT/PCCC/VLNCN/Pháo`), phê duyệt điều chỉnh kiểm kê/xuất hủy bằng xác thực 2 lớp (PIN/OTP), xem báo cáo toàn chuỗi. |
| **`ACT-WM`** | **Quản lý kho / Thủ kho (`Warehouse Manager`)** | **`P1 (WMS)`** | Thiết lập sơ đồ kho 2D (`Zone/Rack/Bin`), cấu hình định mức tồn chứa thuốc nổ tối đa (`NEQ/NEW`) & quy tắc phân khu cách ly (`QCVN 01:2019/BCT`), duyệt phiếu nhập/xuất/điều chuyển/kiểm kê. |
| **`ACT-WS`** | **Nhân viên kho (`Warehouse Staff`)** | **`P1 (WMS)`** | Tác nghiệp trực tiếp bằng máy quét mã vạch/Mobile Web tại kệ kho: Nhận hàng, Cất hàng (`Putaway`), Soạn hàng (`Picking`), Quét đếm kiểm kê theo Lô/Serial/HSD (kể cả khi `Offline`). |
| **`ACT-ACC`** | **Kế toán & Pháp chế (`Accountant & Compliance`)** | `P1` & `P2` | Kiểm soát giá vốn bình quân (`MAC`), đối soát Nhập - Xuất - Tồn (`NXT`), Thẻ kho, công nợ NCC, đối soát ca/COD và trích xuất báo cáo định kỳ nộp Cục `C06/PC06`, `C07/PC07`, Sở Công Thương. |
| **`ACT-POS`** | **Thu ngân / Cửa hàng trưởng (`POS Cashier / Store Mgr`)** | `P2 (POS)` | Mở/kết ca (`BM-POS-03`), bán hàng quầy POS `< 15s/đơn` (`BM-POS-01`), thu thập định danh `CCCD 12 số` khi bán lẻ Pháo hoa `Z121` / kiểm tra Giấy phép sử dụng `VLNCN` (`B2B`), xử lý đổi trả (`BM-POS-02`). |
| **`ACT-TMS`** | **Điều phối vận chuyển, Lái xe & Người áp tải (`Dispatcher, Driver & Escort`)** | `P2 (TMS)` | Điều phối xe chuyên dụng Hàng nguy hiểm Loại 1, gắn Giấy phép vận chuyển Công an cấp (`hạn <= 7 ngày`), niêm phong kẹp chì, theo dõi lộ trình 2D, xác nhận giao hàng (`POD`), đối soát `COD` & nộp trả giấy phép. |

### 1.2. Sơ đồ Kiến trúc 16 Use Cases theo Lộ trình `P1 (WMS)` $\rightarrow$ `P2 (POS + TMS)`

```mermaid
flowchart TD
    subgraph P1_WMS["GIAI ĐOẠN 1 (P1 MVP): HỆ THỐNG QUẢN LÝ KHO BÃI (WMS) & AN TOÀN HÀNG ĐẶC THÙ"]
        UC01["UC-WMS-01: Thiết lập Đa kho, Sơ đồ 2D (Zone/Rack/Bin), Định mức NEQ & Phân khu Cách ly"]
        UC02["UC-WMS-02: Quản lý Danh mục SKU, Đa ĐVT, Lô/Serial/HSD & Thuộc tính Hàng Cháy nổ (Mã UN, NEQ)"]
        UC03["UC-WMS-03: Quản lý Hồ sơ 17 loại Giấy phép/GCN/CC (ANTT, PCCC, VLNCN, Pháo) & Cảnh báo Hạn"]
        UC04["UC-WMS-04: Nhập kho (BM-KHO-01), Cất hàng (Putaway), Khóa chặn Trần NEQ & Cách ly Kíp nổ/Thuốc nổ"]
        UC05["UC-WMS-05: Xuất kho (BM-KHO-02), Soạn hàng FEFO/FIFO, Đối chiếu Giấy phép & Xuất hủy An toàn"]
        UC06["UC-WMS-06: Điều chuyển Liên kho 2 bước (BM-KHO-03 In-Transit), Gắn Giấy phép VC & Niêm chì"]
        UC07["UC-WMS-07: Kiểm kê Kho bằng Mã vạch (BM-KHO-04 Blind Count), 3 Cột Phẩm chất & Cân bằng kho"]
        UC08["UC-WMS-08: Cảnh báo Tồn tối thiểu/Cận date/Trần NEQ 80% & Báo cáo Thẻ kho/NXT/Báo cáo C06-SCT"]
        UC09["UC-WMS-09: Tác nghiệp Kho Ngoại tuyến (Offline-first IndexedDB) & Đồng bộ Hàng đợi Sự kiện"]
    end

    subgraph P2_EXT["GIAI ĐOẠN 2 (P2): MỞ RỘNG BÁN LẺ (POS) & VẬN CHUYỂN HÀNG ĐẶC THÙ (TMS)"]
        UC10["UC-POS-01: Mở ca, Thu/Chi tại quầy, Kết ca Mù (Blind Close) & Bàn giao Két tiền (BM-POS-03)"]
        UC11["UC-POS-02: Bán hàng POS Tốc độ cao (<15s), Tạm lưu bill, VietQR cục bộ & In bill K80/K57 (BM-POS-01)"]
        UC12["UC-POS-03: Bán hàng Đặc thù: Thu thập CCCD 12 số (Pháo hoa Z121), Khóa giá trần & Kiểm định mức VLNCN"]
        UC13["UC-POS-04: Đổi / Trả hàng tại quầy theo Hóa đơn gốc & Phân loại Kho Hàng Trả/Cách ly (BM-POS-02)"]
        UC14["UC-TMS-01: Quản lý Đội xe Chuyên dụng Hàng Loại 1 (Biển UN, Kiểm định) & Hồ sơ Lái xe/Người áp tải"]
        UC15["UC-TMS-02: Lập Vận đơn, Gắn Giấy phép Vận chuyển C06/PC07 (<=7 ngày) & Điều phối Lộ trình 2D"]
        UC16["UC-TMS-03: Xác nhận Giao hàng (POD), Đối soát Kẹp chì, Đối soát COD 100% & Thu hồi Giấy phép VC"]
    end

    UC03 --> UC01
    UC01 --> UC04
    UC02 --> UC04
    UC04 --> UC05
    UC04 --> UC06
    UC06 -.->|"Liên thông In-Transit & Giấy phép VC"| UC15
    UC03 -.->|"Kiểm soát Chứng chỉ Lái xe/Áp tải"| UC14
    UC05 -.->|"Liên thông Tồn kho & Giá niêm yết"| UC11
    UC11 --> UC12
    UC14 --> UC15
    UC15 --> UC16
```

---

## 2. Bảng Ma trận Tổng hợp Danh sách 16 Use Cases (`P1` & `P2`)

| Mã UC | Tên Use Case | Phân hệ | Giai đoạn | Ưu tiên | Truy vết Yêu cầu (`REQUIREMENTS.md`) | Truy vết Tài liệu & Biểu mẫu Marketing (`QLCH-MKT-01` & `MKT-TO-BA-02`) |
| :---: | :--- | :---: | :---: | :---: | :--- | :--- |
| **`UC-WMS-01`** | Thiết lập Đa kho (`Hub/Chi nhánh`), Sơ đồ kho 2D (`Zone/Rack/Bin`), Định mức `NEQ` & Quy tắc Phân khu Cách ly | `WMS` | **`P1 MVP`** | `P0 - Bắt buộc` | `BR-QLCH-01`, `FR-WMS-01`, `FR-WMS-02`, `FR-WMS-08` | `REF-BIZ-003` (Mục 2) & `REF-MKT-005` (`QCVN 01:2019/BCT` — Khoảng cách an toàn, Định mức `NEQ`, Phân khu cách ly) |
| **`UC-WMS-02`** | Quản lý Danh mục Hàng hóa (`SKU`), Đa ĐVT (`Multi-UoM`), Lô/Serial/HSD & Thuộc tính Hàng Cháy nổ (`Mã UN`, `NEQ`) | `WMS` | **`P1 MVP`** | `P0 - Bắt buộc` | `FR-WMS-03`, `FR-WMS-08`, `NFR-QLCH-01` | `REF-BIZ-003` (Mục 1) & `REF-MKT-005` (Mục 2 & 7.1 — Phân loại `VLNCN`, `Pháo hoa Z121`, `Hóa chất`, `Mã UN`, `NEQ`) |
| **`UC-WMS-03`** | Quản lý Hồ sơ 17 loại Giấy phép / GCN / Chứng chỉ (`ANTT`, `PCCC`, `VLNCN`, `Pháo`) & Cảnh báo Hết hạn (`30-60 ngày`) | `WMS / Compliance` | **`P1 MVP`** | `P0 - Bắt buộc` | `FR-WMS-09` | `REF-MKT-005` (Mục 3 — Ma trận 17 loại Giấy phép theo NĐ `96/2016`, NĐ `136/2020`, NĐ `137/2020`, Luật `42/2024`) |
| **`UC-WMS-04`** | Nhập kho (`Inbound`), Cất hàng (`Putaway`), Khóa chặn Trần `NEQ` (`Hard Lock`) & Chặn Xếp chung Hàng Kỵ nhau | `WMS` | **`P1 MVP`** | `P0 - Bắt buộc` | `FR-WMS-04`, `FR-WMS-08` | **`BM-KHO-01`** (`Mẫu số 01-VT` — TT133/TT200) & `REF-MKT-005` (Mục 5.2 & 7.2 — Kiểm soát `NEQ` & Cách ly Kíp nổ/Thuốc nổ) |
| **`UC-WMS-05`** | Xuất kho (`Outbound`), Soạn hàng `FEFO/FIFO` (`Picking`), Kiểm tra Giấy phép & Xuất hủy Hàng hỏng/Hết hạn | `WMS` | **`P1 MVP`** | `P0 - Bắt buộc` | `FR-WMS-03`, `FR-WMS-04`, `FR-WMS-08` | **`BM-KHO-02`** (`Mẫu số 02-VT` — TT133/TT200) & `REF-MKT-005` (Đối soát Lệnh xuất/Giấy phép & PIN 2 lớp) |
| **`UC-WMS-06`** | Điều chuyển Liên kho 2 bước (`In-Transit Stock Transfer`), Gắn Giấy phép Vận chuyển & Niêm phong Kẹp chì | `WMS` | **`P1 MVP`** | `P0 - Bắt buộc` | `FR-WMS-05`, `FR-WMS-08` | **`BM-KHO-03`** (Phiếu Điều chuyển Liên chi nhánh 2 bước) & `REF-MKT-005` (Mục 6.2 — Giấy phép VC C06/PC07) |
| **`UC-WMS-07`** | Kiểm kê Kho bằng Quét mã vạch (`Blind Count / Tally`), 3 Cột Phẩm chất & Phê duyệt Cân bằng kho 2 lớp | `WMS` | **`P1 MVP`** | `P0 - Bắt buộc` | `FR-WMS-06`, `NFR-QLCH-01` | **`BM-KHO-04`** (`Mẫu số 05-VT` — Biên bản Kiểm kê TT133/TT200) & `REF-MKT-005` (Mục 7.6 — Xác thực PIN/OTP) |
| **`UC-WMS-08`** | Cảnh báo Tồn tối thiểu / Cận hạn / Trần `NEQ 80%` & Báo cáo Thẻ kho, `NXT`, Sổ Báo cáo Công an (`C06`) / Sở Công Thương | `WMS` | **`P1 MVP`** | `Cao` | `FR-WMS-06`, `FR-WMS-07`, `FR-WMS-09` | `REF-BIZ-003` (Tồn kho đa trạng thái) & `REF-MKT-005` (Mục 5.2 & 7.6 — Sổ theo dõi bất biến nộp `C06` & Sở CT) |
| **`UC-WMS-09`** | Tác nghiệp Kho Ngoại tuyến (`Offline-first WMS`) tại Kho Cách ly / Chống nổ & Đồng bộ Hàng đợi Sự kiện | `WMS` | **`P1 MVP`** | `Cao` | `NFR-QLCH-02`, `NFR-QLCH-03` | `REF-BIZ-003` (Mục 5 — `IndexedDB` + `Sync Queue`) & `REF-MKT-005` (Kho cách ly xa khu dân cư, tường chắn sóng) |
| **`UC-POS-01`** | Mở ca, Thu/Chi tại quầy, Kết ca Mù (`Blind Close`) & Bàn giao Két tiền Thu ngân | `POS` | `P2` | `Cao (P2)` | `BR-QLCH-02`, `FR-POS-01` | **`BM-POS-03`** (Biên bản Bàn giao Ca & Đối soát Két tiền) |
| **`UC-POS-02`** | Bán hàng POS Tốc độ cao (`< 15s`), Tạm lưu đa đơn (`Hold Bill`), VietQR cục bộ & In bill `K80/K57` | `POS` | `P2` | `Cao (P2)` | `FR-POS-01`, `NFR-QLCH-01..03` | **`BM-POS-01`** (Hóa đơn POS `K80/K57`, VietQR động, chuẩn NĐ `70/2025/NĐ-CP`) |
| **`UC-POS-03`** | Bán hàng Đặc thù: Bắt buộc Định danh `CCCD 12 số` & Khóa giá trần (Pháo hoa `Z121`) / Kiểm định mức Nổ mìn (`VLNCN`) | `POS` | `P2` | `Cao (P2)` | `FR-POS-02` | `REF-MKT-005` (Mục 4.1, 4.2 & 7.5 — Quy định bán lẻ Pháo hoa Z121 theo NĐ `137/2020` & B2B `VLNCN` theo Luật `42/2024`) |
| **`UC-POS-04`** | Đổi / Trả hàng tại quầy POS theo Hóa đơn gốc & Phân loại Kho Hàng Trả / Kho Cách ly An toàn | `POS` | `P2` | `Cao (P2)` | `FR-POS-01`, `FR-POS-02` | **`BM-POS-02`** (Phiếu Đổi / Trả Hàng) & Quy tắc cách ly hàng lỗi/ẩm ướt (`QCVN 01:2019/BCT`) |
| **`UC-TMS-01`** | Quản lý Đội xe Chuyên dụng Hàng Nguy hiểm Loại 1 (`Biển UN`, Kiểm định, PCCC) & Chứng chỉ Lái xe / Người áp tải | `TMS` | `P2` | `Cao (P2)` | `FR-TMS-01`, `FR-TMS-02` | `REF-MKT-005` (Mục 3 Nhóm IV-V & Mục 6.1 — Nghị định `34/2024/NĐ-CP` về phương tiện & nhân sự chở hàng nguy hiểm) |
| **`UC-TMS-02`** | Lập Vận đơn, Gắn Giấy phép Vận chuyển (`C06/PC07`, hạn `<= 7 ngày`), Kiểm tra Ghép hàng & Điều phối Lộ trình 2D | `TMS` | `P2` | `Cao (P2)` | `FR-TMS-01`, `FR-TMS-02` | `REF-MKT-005` (Mục 6.2 & 7.4 — Giấy phép vận chuyển từng chuyến, tuyến đường/khung giờ chỉ định, cấm ghép Kíp nổ + Thuốc nổ) |
| **`UC-TMS-03`** | Xác nhận Giao hàng (`POD`), Kiểm tra Niêm phong Kẹp chì, Đối soát `COD` 100% & Theo dõi Nộp trả Giấy phép Vận chuyển | `TMS` | `P2` | `Cao (P2)` | `FR-TMS-01`, `FR-TMS-02` | `REF-MKT-005` (Mục 6.2 — Hoàn trả Giấy phép vận chuyển cho Công an trong vòng `07 ngày` sau chuyến hàng) |

---

## 3. Đặc tả Chi tiết 09 Use Cases Trọng tâm Giai đoạn 1 (`P1 MVP — Hệ thống Kho bãi WMS & Tuân thủ Hàng Đặc thù`)

### `UC-WMS-01`: Thiết lập Đa kho (`Hub/Chi nhánh`), Sơ đồ kho 2D (`Zone/Rack/Bin`), Định mức `NEQ` & Quy tắc Phân khu Cách ly
- **Tác nhân chính:** `Chủ chuỗi (ACT-OWN)`, `Quản lý kho (ACT-WM)`.
- **Truy vết:** `BR-QLCH-01`, `FR-WMS-01`, `FR-WMS-02`, `FR-WMS-08`; `REF-BIZ-003` (Mục 2) & `REF-MKT-005` (Mục 5.1 — `QCVN 01:2019/BCT`).
- **Luồng chính (Happy Path):**
  1. Người dùng khởi tạo hoặc cấu hình Kho trong hệ thống (`Kho tổng Hub/DC`, `Kho chi nhánh / Cửa hàng Z121`, `Kho chuyên dụng VLNCN/Hóa chất`), kèm các kho con logic (`Kho Hàng Tốt - Sellable` và `Kho Hàng Lỗi / Cách ly chờ hủy - Quarantine`).
  2. Thiết lập cấu trúc phân cấp vị trí lưu trữ: `Khu vực / Buồng kho (Zone)` $\rightarrow$ `Dãy/Kệ/Pallet (Rack)` $\rightarrow$ `Tầng/Ô chứa (Bin)` và gắn thuộc tính an toàn đặc thù cho từng Kho / `Zone`:
     - **Định mức tồn chứa thuốc nổ/thuốc pháo quy đổi tối đa (`Max NEQ / NEW Limit`**, tính bằng `kg` hoặc `tấn` theo Giấy chứng nhận ANTT/PCCC được cấp).
     - **Nhóm tương thích lưu trữ (`Compatibility Group` theo `QCVN 01:2019/BCT`):** Ví dụ `Zone A: Chỉ chứa Thuốc nổ`, `Zone B (Buồng cách ly chống nổ): Chỉ chứa Kíp nổ / Phụ kiện nổ`, `Zone C: Tiền chất Amoni Nitrat ($NH_4NO_3$ — cách ly hoàn toàn dầu mỡ/axít/kim loại kiềm)`, `Zone D: Pháo hoa tiêu dùng Z121`, `Zone E: Hàng tiêu dùng thông thường`.
     - **Chỉ số kỹ thuật an toàn kho:** Điện trở nối đất chống sét ($R \le 10\ \Omega$), chuẩn thiết bị điện phòng nổ (`Ex-proof IP54`), ngưỡng nhiệt độ & độ ẩm bảo quản tối đa.
  3. Trên màn hình **Thiết kế Sơ đồ kho 2D (`2D Warehouse Layout Builder`)**, người dùng bố trí trực quan các khối `Zone/Rack/Bin`, vành đai an toàn ngoại vi, tường chắn nổ, vị trí bình chữa cháy và tủ điện ngoài kho.
  4. Hệ thống sinh mã định danh vị trí (`Bin Barcode/QR`) và in hàng loạt tem vị trí qua máy in nhiệt.
  5. Khi vận hành, **Sơ đồ kho 2D** hiển thị trực quan thanh phần trăm tải trọng **`% NEQ hiện tại / Max NEQ`** của từng buồng kho cùng màu sắc cảnh báo (Xanh: $< 80\%$ `NEQ`, Vàng: $80\% - 95\%$ `NEQ` hoặc có lô cận date, Đỏ: chạm trần `NEQ` hoặc vi phạm nhiệt độ/độ ẩm).
- **Luồng ngoại lệ (Exceptions):**
  - *`E1 - Kho hàng đặc thù chưa có Giấy phép ANTT & Nghiệm thu PCCC còn hiệu lực`:* Hệ thống khóa trạng thái kích hoạt nhận hàng (`Locked for Inbound` đối với nhóm hàng cháy nổ/pháo) cho đến khi gắn hồ sơ giấy phép hợp lệ tại `UC-WMS-03`.

---

### `UC-WMS-02`: Quản lý Danh mục Hàng hóa (`SKU`), Đa ĐVT (`Multi-UoM`), Lô/Serial/HSD & Thuộc tính Hàng Cháy nổ (`Mã UN`, `NEQ`)
- **Tác nhân chính:** `Quản lý kho (ACT-WM)`.
- **Truy vết:** `FR-WMS-03`, `FR-WMS-08`, `NFR-QLCH-01`; `REF-BIZ-003` (Mục 1) & `REF-MKT-005` (Mục 2 & 7.1).
- **Luồng chính (Happy Path):**
  1. Quản lý kho tạo hoặc cập nhật `SKU` với thông tin cơ bản: Mã `SKU`, Mã vạch (`Barcode/QR`), Tên hàng, Thương hiệu/Nhà máy sản xuất (ví dụ: `Nhà máy Z121`, `MICCO`...), Đơn vị tính cơ sở (`Base UoM` — ví dụ: `Giàn`, `Hộp`, `Kg`, `Kíp`) và bảng **Quy đổi Đa đơn vị tính (`Multi-UoM`**, ví dụ: `1 Thùng = 20 Giàn`).
  2. Chọn **Phân loại Quản lý Hàng hóa (`Product Regulatory Type`)**:
     - `Loại 0 — Hàng tiêu dùng / Bán lẻ thông thường`
     - `Loại 1A — Vật liệu nổ công nghiệp (Thuốc nổ / Phụ kiện kíp nổ, dây nổ)`
     - `Loại 1B — Tiền chất thuốc nổ (Amoni Nitrat >= 98.5%, Natri Nitrat...)`
     - `Loại 2 — Pháo hoa tiêu dùng (Z121 — Không gây tiếng nổ, được phép bán lẻ dân sự)`
     - `Loại 3 — Chất dễ cháy nổ / Hóa chất nguy hiểm (LPG, Khí công nghiệp, Dung môi Loại 2, 3, 4)`
  3. Nếu thuộc nhóm Hàng đặc thù (`Loại 1A, 1B, 2, 3`), hệ thống bắt buộc nhập bộ **Thuộc tính An toàn & Pháp lý (`Hazardous Metadata`)**:
     - **Mã số Liên Hợp Quốc (`UN Number`**, ví dụ: `UN 0336` cho Pháo hoa 1.4G, `UN 1942` cho Amoni Nitrat) và **Nhóm nguy hiểm (`Hazard Division`: `1.1`, `1.3`, `1.4G`...)**.
     - **Định lượng thuốc nổ/thuốc pháo quy đổi trên 1 đơn vị cơ sở (`Unit NEQ / NEW` tính bằng `kg`)** để hệ thống tự động nhân với số lượng tồn kho khi kiểm soát trần kho.
     - **Nhóm kỵ lưu trữ (`Incompatibility Group`)**: Đánh dấu rõ `Thuốc nổ` vs `Kíp nổ` vs `Dầu mỡ/Axít`.
     - **Bắt buộc quản lý theo `Số Lô (Batch/Lot)`, `Số Sê-ri thùng/hộp (Serial)`, `Ngày sản xuất` & `Hạn sử dụng (`FIFO/FEFO`)`**.
     - **Giá bán lẻ niêm yết trần (`Regulated Ceiling Price`**, áp dụng cho Pháo hoa `Z121`).
  4. In tem nhãn mã vạch/QR chứa đủ tổ hợp: `Mã SKU + Số Lô + Số Thùng/Serial + Ngày SX/HSD + Cảnh báo Nhóm Nguy hiểm`.
- **Luồng ngoại lệ (Exceptions):**
  - *`E1 - Khai báo sản phẩm thuộc danh mục Nghiêm cấm dân sự (Pháo nổ / Pháo hoa nổ trái phép)`:* Hệ thống hiển thị cảnh báo pháp lý theo Nghị định `137/2020/NĐ-CP` và chặn lưu nếu không có giấy phép đặc biệt của Thủ tướng Chính phủ / Bộ Quốc phòng.

---

### `UC-WMS-03`: Quản lý Hồ sơ 17 loại Giấy phép / GCN / Chứng chỉ (`ANTT`, `PCCC`, `VLNCN`, `Pháo`) & Cảnh báo Hết hạn (`30-60 ngày`)
- **Tác nhân chính:** `Chủ chuỗi (ACT-OWN)`, `Quản lý kho (ACT-WM)`, `Kế toán & Pháp chế (ACT-ACC)`.
- **Truy vết:** `FR-WMS-09`; `REF-MKT-005` (Mục 3 — Ma trận 17 loại Giấy phép bắt buộc).
- **Luồng chính (Happy Path):**
  1. Người dùng truy cập phân hệ **Hồ sơ Pháp lý & Tuân thủ An toàn (`Compliance & License Registry`)**, cập nhật và đính kèm bản chụp/PDF cục bộ cho 5 nhóm hồ sơ (17 loại chứng từ):
     - **Nhóm I (Doanh nghiệp & ANTT):** (1) GCN Đăng ký doanh nghiệp, (2) **GCN đủ điều kiện về ANTT (`C06/PC06`)**, (3) Phương án bảo đảm ANTT.
     - **Nhóm II (PCCC & Môi trường):** (4) GCN thẩm duyệt thiết kế PCCC, (5) **Văn bản chấp thuận nghiệm thu PCCC (`C07/PC07`)**, (6) Giấy phép môi trường.
     - **Nhóm III (Chuyên ngành VLN & Pháo):** (7) Giấy phép SX/KD Pháo hoa (`BQP`), (8) Văn bản chấp thuận địa điểm Cửa hàng pháo hoa (`Công an tỉnh & Z121`), (9) Giấy phép SX/KD/Sử dụng `VLNCN` (`Bộ/Sở Công Thương`), (10) **GCN đủ điều kiện bảo quản `VLNCN`/Tiền chất (`Sở Công Thương`)**.
     - **Nhóm IV (Vận chuyển Hàng nguy hiểm):** (11) **Giấy phép vận chuyển Pháo hoa từng chuyến (`C06`, hạn $\le 7$ ngày)**, (12) **Giấy phép vận chuyển Hàng nguy hiểm Loại 1 (`C07/PC07`)**, (13) GCN kiểm định ATKT & BVMT xe chở hàng nguy hiểm.
     - **Nhóm V (Chứng chỉ Con người):** (14) CN huấn luyện nghiệp vụ PCCC & CNCH (`5 năm`), (15) GCN huấn luyện kỹ thuật an toàn `VLNCN`/tiền chất (`2 năm`), (16) GCN tập huấn an toàn vận chuyển hàng nguy hiểm (`2 năm`), (17) Chứng chỉ thợ nổ mìn / chỉ huy nổ mìn.
  2. Mỗi giấy phép được gắn trực tiếp với thực thể tương ứng (`Kho`, `Cửa hàng`, `Phương tiện xe`, `Nhân sự Thủ kho/Lái xe/Người áp tải`) kèm `Số giấy phép`, `Cơ quan cấp`, `Ngày cấp`, `Ngày hết hạn` và `Định mức NEQ cấp phép (nếu có)`.
  3. Hệ thống tự động quét hàng ngày và hiển thị cảnh báo trước **$60\text{ ngày}$ (Vàng)** và **$30\text{ ngày}$ (Đỏ)** trước khi giấy phép hết hạn.
- **Luồng ngoại lệ (Exceptions):**
  - *`E1 - Giấy phép của Kho, Xe hoặc Chứng chỉ Nhân sự đã hết hạn (Expired)`:* Hệ thống tự động **khóa quyền thực thi (`Hard Compliance Lock`)**: không cho phép chọn Kho hết hạn PCCC/ANTT để nhập thêm hàng cháy nổ, không cho phép gán Xe hết hạn đăng kiểm hoặc Lái xe/Thủ kho hết hạn chứng chỉ PCCC vào lệnh điều chuyển/xuất kho.

---

### `UC-WMS-04`: Nhập kho (`Inbound`), Cất hàng (`Putaway`), Khóa chặn Trần `NEQ` (`Hard Lock`) & Chặn Xếp chung Hàng Kỵ nhau (`BM-KHO-01`)
- **Tác nhân chính:** `Quản lý kho (ACT-WM)`, `Nhân viên kho (ACT-WS)`, `Kế toán kho (ACT-ACC)`.
- **Truy vết:** `FR-WMS-04`, `FR-WMS-08`; Biểu mẫu **`BM-KHO-01` (`Mẫu số 01-VT` — TT133/TT200)** & `REF-MKT-005` (Mục 5.2, 7.2).
- **Luồng chính (Happy Path):**
  1. **Lập Phiếu Nhập kho (`BM-KHO-01`):** Ghi nhận Kho nhập, Nhà cung cấp (hoặc Nhà máy `Z121`/`MICCO`), Số hóa đơn gốc, Số Giấy phép vận chuyển đi kèm lô hàng nhập, danh sách `SKU`, **`Số lượng theo chứng từ`**, Đơn giá, Chiết khấu, Thuế GTGT, Chi phí nhập phân bổ.
  2. **Kiểm tra Tự động Định mức `NEQ` trước khi Nhập (`NEQ Capacity Pre-check`):**
     - Với hàng đặc thù có thuộc tính `Unit NEQ > 0`, hệ thống tự động tính:
       $$\text{Tổng NEQ dự kiến sau nhập} = \text{Tổng NEQ hiện tại trong kho} + \sum_{i=1}^{n} (\text{SL Thực nhập}_i \times \text{Unit NEQ}_i)$$
     - Cảnh báo vàng nếu đạt $\ge 80\%$ định mức cấp phép của Kho/`Zone`.
  3. **Kiểm nhận bằng Mã vạch & Phân bổ Vị trí (`Receiving & Safe Putaway`):**
     - Nhân viên kho quét mã vạch kiện hàng, xác nhận **`Số lượng thực nhập`**, `Số Lô (Batch)`, `Số Serial thùng`, `Ngày SX` & `Hạn sử dụng`.
     - Hệ thống gợi ý vị trí `Rack/Bin` trên **Sơ đồ kho 2D** tuân thủ nghiêm ngặt **Quy tắc Phân khu Cách ly (`Incompatible Storage Separation`)**: chỉ gợi ý `Bin` thuộc `Zone` tương thích.
     - Nhân viên kho quét **Mã vạch `Bin`** + **Mã vạch `SKU/Lô`** để xác nhận cất hàng.
  4. **Hoàn tất & Tính Giá vốn `MAC`:**
     - Chỉ cộng tồn kho và công nợ theo đúng **`Số lượng thực nhập`** quy đổi về `Base UoM`.
     - Cập nhật `Tổng NEQ hiện tại` của Kho/`Zone` và tính lại **Giá vốn bình quân gia quyền (`MAC`)** theo công thức chuẩn `BM-KHO-01`.
     - Ghi sổ Thẻ kho bất biến và in **Phiếu Nhập Kho (`Mẫu số 01-VT`)**.
- **Luồng ngoại lệ (Exceptions):**
  - *`E1 - Vượt định mức tồn chứa thuốc nổ cấp phép (`Tổng NEQ dự kiến > Max NEQ của Kho/Zone`)`:* Hệ thống kích hoạt **`Khóa chặn cứng (Hard Validation Lock)`** — tuyệt đối không cho phép hoàn tất nhập vượt trần `NEQ` trên Giấy phép ANTT/PCCC và gợi ý điều phối sang kho khác còn hạn mức.
  - *`E2 - Vi phạm quy tắc cách ly (`Quét cất Kíp nổ vào cùng Buồng/Zone đang chứa Thuốc nổ`, hoặc `Amoni Nitrat chung với Dầu mỡ/Axít`)`:* Thiết bị cầm tay phát còi cảnh báo đỏ và **chặn tuyệt đối thao tác `Putaway`** theo `QCVN 01:2019/BCT`.

---

### `UC-WMS-05`: Xuất kho (`Outbound`), Soạn hàng `FEFO/FIFO` (`Picking`), Kiểm tra Giấy phép & Xuất hủy Hàng hỏng (`BM-KHO-02`)
- **Tác nhân chính:** `Quản lý kho (ACT-WM)`, `Nhân viên kho (ACT-WS)`.
- **Truy vết:** `FR-WMS-03`, `FR-WMS-04`, `FR-WMS-08`; Biểu mẫu **`BM-KHO-02` (`Mẫu số 02-VT`)** & `REF-MKT-005` (Mục 4.2, 5.2, 7.6).
- **Luồng chính (Happy Path):**
  1. **Lập Phiếu Xuất kho (`BM-KHO-02`):** Chọn lý do xuất (`Xuất bán B2B/Bán buôn`, `Xuất trả NCC`, `Xuất nội bộ`, hoặc `Xuất hủy hàng hỏng/ẩm ướt/hết hạn`).
  2. **Kiểm tra Điều kiện Pháp lý khi Xuất Hàng Đặc thù:**
     - Nếu xuất bán `VLNCN` / Tiền chất thuốc nổ (`B2B`): Hệ thống bắt buộc chọn Khách hàng doanh nghiệp có **`Giấy phép sử dụng VLNCN`** còn hiệu lực và kiểm tra `Số lượng xuất <= Hạn mức nổ mìn còn lại` trên giấy phép của khách hàng; đồng thời gắn **`Số Giấy phép vận chuyển Hàng nguy hiểm Loại 1`**, `Biển số xe chuyên dụng` và `Họ tên/CCCD Người nhận & Người áp tải`.
  3. **Giữ chỗ & Chỉ định Lấy hàng theo Lô (`FEFO / FIFO Picking` trên Sơ đồ 2D):**
     - Tạm khóa số lượng vào `Tồn giữ chỗ (Reserved)`.
     - Tự động chỉ định lấy đúng `Lô/Serial` theo nguyên tắc `FIFO/FEFO` và hiển thị vị trí `Rack/Bin` trên **Sơ đồ kho 2D**.
  4. **Quét mã Xác nhận Thực xuất & Xác thực 2 lớp (`PIN/OTP`):**
     - Nhân viên kho quét `Mã Bin` + `Mã Lô/Serial` lấy hàng.
     - Với phiếu xuất Hàng đặc thù hoặc phiếu **`Xuất hủy`**, hệ thống yêu cầu `Quản lý kho / Chủ chuỗi` nhập **Mã PIN/OTP xác thực 2 lớp** trước khi trừ `Tồn thực tế (On-hand)`, giảm `Tổng NEQ hiện tại`, hạch toán chi phí hủy (nếu là xuất hủy) và in **Phiếu Xuất Kho (`Mẫu số 02-VT`)**.
- **Luồng ngoại lệ (Exceptions):**
  - *`E1 - Xuất vượt Tồn khả dụng (`SL Thực xuất > Available`) hoặc vượt Hạn mức Giấy phép của khách hàng B2B`:* Hệ thống chặn hoàn tất phiếu xuất.
  - *`E2 - Quét sai Lô/Serial so với Lệnh xuất Hàng đặc thù`:* Hệ thống chặn ngay tại bước quét mã để đảm bảo 100% truy xuất nguồn gốc từng thùng pháo/bao thuốc nổ.

---

### `UC-WMS-06`: Điều chuyển Liên kho 2 bước (`In-Transit Stock Transfer`), Gắn Giấy phép Vận chuyển & Niêm phong Kẹp chì (`BM-KHO-03`)
- **Tác nhân chính:** `Quản lý kho Xuất`, `Quản lý kho Nhận`, `Nhân viên kho (ACT-WS)`.
- **Truy vết:** `FR-WMS-05`, `FR-WMS-08`; Biểu mẫu **`BM-KHO-03`** & `REF-MKT-005` (Mục 6.1, 6.2).
- **Luồng chính (Happy Path — Quy trình 2 bước):**
  1. **Lập Phiếu Điều chuyển (`PDC` — `BM-KHO-03`):** Chọn `Kho Xuất`, `Kho Nhận`, danh sách `SKU/Lô`, `SL Yêu cầu`.
     - Nếu điều chuyển **Pháo hoa hoặc Vật liệu nổ**, bắt buộc đính kèm **`Số Giấy phép vận chuyển do C06/PC07 cấp`** (kiểm tra còn hạn $\le 7\text{ ngày}$), chọn `Xe chuyên dụng Hàng Loại 1`, `Lái xe`, `Người áp tải` và nhập **`Mã số Khóa niêm phong kẹp chì (Seal No)`**.
     - Hệ thống kiểm tra trước: đảm bảo `Kho Nhận` không bị vượt trần `Max NEQ` khi nhận lô hàng này, và trên cùng 1 chuyến xe không có cả `Kíp nổ` lẫn `Thuốc nổ`.
  2. **Bước 1 — Kho Xuất xác nhận Xuất chuyển (`In-Transit`):**
     - Quét mã `Picking` theo đúng `Lô/Serial`, khóa niêm chì thùng xe và bấm `Xuất chuyển`.
     - Hệ thống **trừ tồn kho và giảm `NEQ` tại `Kho Xuất`**, chuyển toàn bộ lượng hàng sang trạng thái **`Tồn đang vận chuyển (In-Transit Inventory)`** (chưa cộng vào `Kho Nhận`). In phiếu `BM-KHO-03`.
  3. **Bước 2 — Kho Nhận kiểm tra Niêm chì & Xác nhận Thực nhận (`Completed`):**
     - Khi xe đến `Kho Nhận`, Thủ kho nhận kiểm tra đối chiếu **`Mã số Kẹp chì (Seal No)`** nguyên vẹn, quét mã vạch kiểm đếm **`SL Thực nhận`** theo từng `Lô/Serial` và thực hiện `Putaway` vào `Bin`.
     - Hệ thống giải phóng `In-Transit`, cộng tồn kho và tăng `NEQ` tương ứng tại `Kho Nhận`.
- **Luồng ngoại lệ (Exceptions):**
  - *`E1 - Rách niêm phong kẹp chì hoặc Lệch số lượng (`SL Thực nhận != SL Xuất chuyển`)`:* Hệ thống giữ phần lệch ở trạng thái `Lệch điều chuyển chờ xử lý`, phát cảnh báo khẩn cấp cho `Chủ chuỗi` (đặc biệt nghiêm trọng nếu thất thoát hàng cháy nổ/pháo trên đường vận chuyển) và yêu cầu lập biên bản xác thực 2 lớp.

---

### `UC-WMS-07`: Kiểm kê Kho bằng Quét mã vạch (`Blind Count / Tally`), 3 Cột Phẩm chất & Phê duyệt Cân bằng kho 2 lớp (`BM-KHO-04`)
- **Tác nhân chính:** `Quản lý kho (ACT-WM)`, `Nhân viên kho (ACT-WS)`, `Chủ chuỗi (ACT-OWN)`.
- **Truy vết:** `FR-WMS-06`, `NFR-QLCH-01`; Biểu mẫu **`BM-KHO-04` (`Mẫu số 05-VT`)** & `REF-MKT-005` (Mục 7.6).
- **Luồng chính (Happy Path):**
  1. **Chốt mốc Kiểm kê (`Snapshot`) & Bật Kiểm kê mù (`Blind Count`):** Hệ thống chụp số `Tồn theo Sổ/Hệ thống` theo từng `Bin` và `Lô/Serial`, ẩn số tồn hệ thống trên màn hình nhân viên đếm.
  2. **Quét mã vạch cộng dồn (`Barcode Scan Tally`) & Phân loại 3 cột Phẩm chất (`Mẫu số 05-VT`):**
     - Nhân viên quét mã `Bin` và bắn liên tiếp mã vạch sản phẩm/lô (`+1` mỗi lần quét, `< 1s`).
     - Phân loại thực đếm theo 3 trạng thái: `(1) Còn tốt 100%`, `(2) Kém phẩm chất (móp vỏ, cận date)`, `(3) Mất phẩm chất / Hư hỏng / Ẩm ướt (bắt buộc cách ly chờ tiêu hủy an toàn)`.
  3. **Duyệt Cân bằng kho bằng Xác thực 2 lớp (`PIN/OTP`):**
     - Hệ thống tính chênh lệch `Thừa (+)` / `Thiếu (-)` cả về số lượng, giá trị tiền (`MAC`) và trọng lượng `NEQ`.
     - Khi Chủ chuỗi/Quản lý kho nhập **PIN/OTP phê duyệt `Cân bằng kho`**, hệ thống tự động sinh Phiếu Nhập/Xuất điều chỉnh trong Thẻ kho, chuyển hàng hỏng/ẩm ướt sang `Kho Cách ly (Quarantine)` và xuất bản in **Biên bản Kiểm kê (`Mẫu số 05-VT`)**.

---

### `UC-WMS-08`: Cảnh báo Tồn tối thiểu / Cận hạn / Trần `NEQ 80%` & Báo cáo Thẻ kho, `NXT`, Sổ Báo cáo Công an (`C06`) / Sở Công Thương
- **Tác nhân chính:** `Chủ chuỗi (ACT-OWN)`, `Quản lý kho (ACT-WM)`, `Kế toán & Pháp chế (ACT-ACC)`.
- **Truy vết:** `FR-WMS-06`, `FR-WMS-07`, `FR-WMS-09`; `REF-MKT-005` (Mục 5.2, 7.6).
- **Luồng chính (Happy Path):**
  1. **Trung tâm Cảnh báo Kho & Pháp lý (`Alert Center & 2D Map Badges`):**
     - Cảnh báo tồn kho chạm ngưỡng `Min Stock` hoặc vượt `Max Stock`.
     - Cảnh báo lô hàng sắp hết hạn (`Near-Expiry`) hoặc đã hết hạn (`Expired`).
     - Cảnh báo an toàn kho đặc thù: Tổng lượng thuốc nổ/thuốc pháo đạt $\ge 80\%$ định mức `NEQ`; Giấy phép `ANTT/PCCC/VLNCN/Kiểm định xe/Chứng chỉ nhân sự` còn $< 30 - 60\text{ ngày}$; Giấy phép vận chuyển pháo hoa sắp quá hạn 7 ngày phải nộp trả Công an.
  2. **Báo cáo Nhập - Xuất - Tồn (`NXT`), Thẻ kho (`Stock Card`) & Sổ Theo dõi Pháp lý Bất biến:**
     - Truy xuất Báo cáo `NXT` và `Thẻ kho` chi tiết đến từng `Bin`, `Lô/Serial`, đảm bảo khớp 100% công thức lũy kế.
     - **Trích xuất Sổ theo dõi Xuất - Nhập - Tồn Hàng đặc thù (`Compliance Audit Report`)** nộp định kỳ cho **Cục `C06/PC06` Bộ Công an** và **Sở Công Thương**: hiển thị đầy đủ Ngày giờ, Số chứng từ, Tên hàng, Số Lô/Serial, Trọng lượng `NEQ`, Họ tên & Số `CCCD` người nhận/mua, Biển số xe và Số Giấy phép vận chuyển Công an cấp.

---

### `UC-WMS-09`: Tác nghiệp Kho Ngoại tuyến (`Offline-first WMS`) tại Kho Cách ly / Chống nổ & Đồng bộ Hàng đợi Sự kiện
- **Tác nhân chính:** `Nhân viên kho (ACT-WS)`, `Quản lý kho (ACT-WM)`.
- **Truy vết:** `NFR-QLCH-02`, `NFR-QLCH-03`; `REF-BIZ-003` (Mục 5) & `REF-MKT-005` (Mục 5.1).
- **Luồng chính (Happy Path):**
  1. Do đặc thù các kho `VLNCN`/pháo hoa thường đặt ở khu vực cách ly xa dân cư, có ụ đất/tường chắn nổ dày gây cản sóng Wi-Fi/4G, ứng dụng Web App tự động nạp dữ liệu phiên làm việc (`SKU`, `Barcode`, `Lô/HSD`, `Sơ đồ 2D Bin`, `Giới hạn NEQ`, `Quy tắc cách ly`) vào bộ nhớ cục bộ **`IndexedDB`**.
  2. Khi mất mạng trong kho, nhân viên vẫn quét mã vạch kiểm kê, cất hàng `Putaway` và lấy hàng `Picking` bình thường (`< 1 giây/thao tác`); toàn bộ quy tắc kiểm tra **Chặn vượt trần `NEQ`** và **Chặn xếp chung Kíp nổ + Thuốc nổ** vẫn hoạt động **100% ngay ở chế độ Offline**.
  3. Khi ra khỏi buồng kho và có kết nối mạng lại, hệ thống tự động đồng bộ tuần tự các sự kiện biến động (`Delta Events`) trong `Sync Queue` lên Server và kiểm tra xung đột an toàn.

---

## 4. Đặc tả Định khung 07 Use Cases Giai đoạn 2 (`P2 — Bán lẻ POS & Vận chuyển Hàng Đặc thù TMS`)

### `UC-POS-01`: Mở ca, Thu/Chi tại quầy, Kết ca Mù (`Blind Close`) & Bàn giao Két tiền (`BM-POS-03`)
- **Truy vết:** `FR-POS-01`; Biểu mẫu **`BM-POS-03`**.
- **Luồng cốt lõi:** Xác nhận `Tiền mặt đầu ca` $\rightarrow$ Ghi nhận tự động `Thu tiền mặt bán hàng`, `Chi hoàn tiền trả hàng`, `Phiếu thu/chi tại quầy` $\rightarrow$ Cuối ca thu ngân nhập **`Tiền mặt thực đếm cuối ca` theo mệnh giá (`Blind Close` ẩn số lý thuyết)** $\rightarrow$ Đối chiếu `Chênh lệch quỹ ca` và in biên bản bàn giao ca `BM-POS-03`.

### `UC-POS-02`: Bán hàng POS Tốc độ cao (`< 15s`), Tạm lưu đa đơn (`Hold Bill`), VietQR cục bộ & In bill `K80/K57` (`BM-POS-01`)
- **Truy vết:** `FR-POS-01`, `NFR-QLCH-01..03`; Biểu mẫu **`BM-POS-01` (Chuẩn Nghị định `70/2025/NĐ-CP`)**.
- **Luồng cốt lõi:** Quét mã vạch tính tiền tức thì, hỗ trợ phím tắt `F1–F12`, tạm lưu nhiều hóa đơn (`Hold Order`), thanh toán kết hợp Tiền mặt + **VietQR động sinh cục bộ (`$0 First`)**, in hóa đơn nhiệt `K80/K57` kèm thông tin chuẩn HĐĐT máy tính tiền và trừ tồn kho trực tiếp từ Kho cửa hàng (`WMS`).

### `UC-POS-03`: Bán hàng Đặc thù: Bắt buộc Định danh `CCCD 12 số` & Khóa giá trần (Pháo hoa `Z121`) / Kiểm định mức (`VLNCN`)
- **Truy vết:** `FR-POS-02`; `REF-MKT-005` (Mục 4.1, 4.2, 7.5 — Nghị định `137/2020/NĐ-CP` & Luật `42/2024/QH15`).
- **Luồng cốt lõi:**
  1. **Khi giỏ hàng POS có sản phẩm `Pháo hoa tiêu dùng (Z121)`:**
     - Hệ thống tự động chuyển trường Thông tin người mua từ *Tùy chọn* sang **Bắt buộc (`Mandatory`)**: Thu ngân phải nhập hoặc quét mã QR trên thẻ **Căn cước công dân (`Số CCCD 12 số`, `Họ và tên`, `Ngày sinh >= 18 tuổi`, `Địa chỉ thường trú`, `Số điện thoại`)** và chọn đúng `Số Lô / Serial giàn pháo` xuất bán.
     - **Khóa giá bán (`Price Ceiling Lock`):** Không cho phép sửa đơn giá cao hơn bảng giá niêm yết chính thức của Nhà máy `Z121` / Bộ Quốc phòng.
     - In Hóa đơn bán hàng kiêm Giấy xác nhận nguồn gốc hợp pháp có đầy đủ `Họ tên, Số CCCD, Địa chỉ người mua, Số Lô pháo` và `Mã QR tra cứu` để người dân xuất trình khi lưu thông trên đường.
  2. **Khi xuất bán `Vật liệu nổ công nghiệp (VLNCN)`:** Chặn bán lẻ tự do tại quầy cho cá nhân; chỉ cho phép lập đơn B2B khi khách hàng có `Giấy phép sử dụng VLNCN` còn hiệu lực và số lượng nằm trong định mức được duyệt.

### `UC-POS-04`: Đổi / Trả hàng tại quầy POS theo Hóa đơn gốc & Phân loại Kho Hàng Trả / Kho Cách ly (`BM-POS-02`)
- **Truy vết:** `FR-POS-01`, `FR-POS-02`; Biểu mẫu **`BM-POS-02`**.
- **Luồng cốt lõi:** Quét mã hóa đơn gốc `BM-POS-01`, lấy đúng đơn giá thực tế sau khuyến mãi lúc mua; phân loại hàng trả về `Kho Bán Hàng (Sellable)` (nếu nguyên tem mác, an toàn 100%) hoặc bắt buộc đưa vào **`Kho Cách ly An toàn (Quarantine Stock)`** (nếu vỏ hộp pháo/hóa chất bị rách, ẩm ướt, móp méo để chờ kiểm tra kỹ thuật/tiêu hủy, tuyệt đối không bán lại cho khách sau).

### `UC-TMS-01`: Quản lý Đội xe Chuyên dụng Hàng Nguy hiểm Loại 1 (`Biển UN`, Kiểm định, PCCC) & Chứng chỉ Lái xe / Người áp tải
- **Truy vết:** `FR-TMS-01`, `FR-TMS-02`; `REF-MKT-005` (Mục 6.1 — Nghị định `34/2024/NĐ-CP`).
- **Luồng cốt lõi:** Quản lý hồ sơ từng xe tải chuyên dụng (Biển số, tải trọng tối đa, hạn `GCN kiểm định ATKT chở hàng nguy hiểm Loại 1`, trang bị xích tiếp địa, bình chữa cháy, biểu trưng nguy hiểm Loại 1 & biển cam `Mã UN`) và hồ sơ `Lái xe` + `Người áp tải` (gắn với Chứng chỉ PCCC & GCN tập huấn vận chuyển hàng nguy hiểm tại `UC-WMS-03`).

### `UC-TMS-02`: Lập Vận đơn, Gắn Giấy phép Vận chuyển (`C06/PC07`, hạn `<= 7 ngày`), Kiểm tra Ghép hàng & Điều phối Lộ trình 2D
- **Truy vết:** `FR-TMS-01`, `FR-TMS-02`; `REF-MKT-005` (Mục 6.2, 7.4 — Nghị định `137/2020/NĐ-CP` & `34/2024/NĐ-CP`).
- **Luồng cốt lõi:**
  1. Gom các Phiếu điều chuyển `BM-KHO-03` / Đơn xuất hàng thành Chuyến vận chuyển (`Shipment Trip`).
  2. **Kiểm tra Tuân thủ An toàn Chuyến xe (`Trip Safety Validation`):**
     - Nếu chuyến xe chở Pháo hoa / `VLNCN`, bắt buộc chọn **1 Lái xe + ít nhất 1 Người áp tải** đều còn hạn chứng chỉ an toàn, chọn **Xe chuyên dụng Loại 1** còn hạn kiểm định, và gắn **`Mã Giấy phép vận chuyển do C06/PC07 cấp`** (còn trong thời hạn hiệu lực $\le 07\text{ ngày}$).
     - **Chặn ghép hàng kỵ nhau trên cùng 1 xe:** Tuyệt đối khóa chặn nếu điều phối viên gán cả `Kíp nổ` và `Thuốc nổ` lên cùng một phương tiện.
  3. Thiết lập **Tuyến đường & Khung giờ chỉ định** theo đúng Giấy phép vận chuyển trên **Bản đồ/Sơ đồ tuyến 2D cục bộ (`$0 First`)** (tránh giờ cao điểm nội đô, tránh hầm đường bộ/phà chở khách).

### `UC-TMS-03`: Xác nhận Giao hàng (`POD`), Kiểm tra Niêm phong Kẹp chì, Đối soát `COD` 100% & Theo dõi Nộp trả Giấy phép Vận chuyển
- **Truy vết:** `FR-TMS-01`, `FR-TMS-02`; `REF-MKT-005` (Mục 6.2).
- **Luồng cốt lõi:**
  1. Tại điểm nhận, tài xế/người áp tải và thủ kho nhận đối chiếu **Mã niêm phong kẹp chì (`Seal No`)**, quét mã xác nhận giao hàng (`POD`) và ghi nhận tiền thu hộ **`COD`** (nếu có).
  2. Cuối chuyến, hệ thống thực hiện **Đối soát `COD` & Hàng hoàn 100%**.
  3. **Theo dõi nghĩa vụ nộp trả Giấy phép vận chuyển Pháo hoa:** Ngay khi chuyến xe chuyển sang trạng thái `Giao hàng thành công`, hệ thống bật bộ đếm ngược **$07\text{ ngày}$** nhắc bộ phận Pháp chế/Điều phối nộp trả bản gốc Giấy phép vận chuyển về cơ quan Công an (`C06`) đã cấp và cập nhật trạng thái `Đã hoàn trả giấy phép (Permit Returned)`.
