# Bộ Biểu mẫu Hóa đơn Bán hàng POS, Phiếu Nhập/Xuất/Điều chuyển Kho & Biên bản Kiểm kê Chuẩn Việt Nam

- **Mã tài liệu đề xuất đăng ký:** `REF-MKT-004`
- **Thực hiện:** `Marketing Lead` (Xử lý Task Độc lập Ưu tiên Cao `QLCH-MKT-01` — GitHub Issue [`#3`](https://github.com/theGonlyK/QLCH/issues/3))
- **Ngày hoàn thành:** `2026-11-14`
- **Căn cứ pháp lý & Thực tiễn đối chiếu:**
  1. **Nghị định `123/2020/NĐ-CP`** và **Nghị định `70/2025/NĐ-CP`** (hiệu lực từ `01/06/2025`, sửa đổi Điều 11 Nghị định `123/2020/NĐ-CP`) về **Hóa đơn điện tử khởi tạo từ máy tính tiền (POS)**.
  2. **Thông tư `133/2016/TT-BTC`** và **Thông tư `200/2014/TT-BTC`** của Bộ Tài chính quy định hệ thống chứng từ kế toán hàng tồn kho (`Mẫu số 01-VT`, `Mẫu số 02-VT`, `Mẫu số 05-VT`).
  3. **Thực tiễn mẫu in chứng từ** trên 5 phần mềm quản lý cửa hàng phổ biến tại Việt Nam (`KiotViet`, `Sapo POS`, `Haravan HaraRetail`, `PosApp`, `Odoo POS`).
- **Mục đích sử dụng:** Cung cấp đặc tả trường dữ liệu, công thức tính toán, trạng thái chứng từ và bố cục trình bày trực quan (Wireframe ASCII) làm nguồn đầu vào chuẩn cho **BA Lead**, **UX Lead**, **Tech Lead** và **QA Lead** dự án `QLCH`.

---

## Danh mục 07 Biểu mẫu Nghiệp vụ Tuyển chọn

1. **Biểu mẫu 01 (`BM-POS-01`):** Hóa đơn Bán hàng / Phiếu Thanh toán Quầy POS (Khổ in nhiệt `K80 - 80mm` & `K57 - 58mm`, tích hợp VietQR động & chuẩn HĐĐT Máy tính tiền).
2. **Biểu mẫu 02 (`BM-POS-02`):** Phiếu Đổi / Trả Hàng & Hoàn Tiền tại Quầy POS (`Return / Exchange Receipt`).
3. **Biểu mẫu 03 (`BM-POS-03`):** Biên bản Bàn giao Ca & Đối soát Két tiền Thu ngân (`Shift Handover & Cash Drawer Reconciliation`).
4. **Biểu mẫu 04 (`BM-KHO-01`):** Phiếu Nhập Kho Hàng hóa (`Mẫu số 01-VT` — Nhập mua từ Nhà cung cấp / Nhập khác).
5. **Biểu mẫu 05 (`BM-KHO-02`):** Phiếu Xuất Kho & Phiếu Xuất Hủy Hàng hóa (`Mẫu số 02-VT` — Xuất bán buôn / Xuất sử dụng / Xuất hủy).
6. **Biểu mẫu 06 (`BM-KHO-03`):** Phiếu Điều chuyển Kho Liên Chi nhánh (`Inter-Branch Stock Transfer` — Quy trình 2 bước Xuất đi & Nhận hàng).
7. **Biểu mẫu 07 (`BM-KHO-04`):** Biên bản Kiểm kê Hàng hóa & Phiếu Cân bằng Kho (`Mẫu số 05-VT` — Kiểm đếm thực tế & Xử lý chênh lệch Thừa/Thiếu).

---

## 1. Biểu mẫu 01 (`BM-POS-01`): Hóa đơn Bán hàng / Phiếu Thanh toán Quầy POS (Khổ nhiệt `K80` & `K57`)

### 1.1. Bố cục Trực quan Chuẩn In nhiệt `K80` (Khổ giấy `80mm`, vùng in `72mm`)

```text
+------------------------------------------------------------------+
|                   [LOGO / TÊN HỆ THỐNG CỬA HÀNG]                 |
|             CHI NHÁNH: CỬA HÀNG SỐ 01 - CẦU GIẤY, HÀ NỘI         |
|       Đ/c: Số 123 Đường Cầu Giấy, P. Quan Hoa, Q. Cầu Giấy, HN   |
|               MST: 0101234567  |  Hotline: 1900 xxxx             |
+------------------------------------------------------------------+
|                     HÓA ĐƠN BÁN HÀNG (POS)                       |
| Số HĐ: HD-CN01-20261114-0089           Ngày: 14/11/2026 10:15    |
| Thu ngân: Nguyễn Thị Mai (NV04)        Quầy: POS-01 (Ca Sáng)    |
| Khách hàng: Anh Trần Văn Hùng          SĐT: 0987.xxx.321         |
| Hạng thẻ: Thành viên Vàng (Điểm tích lũy hiện có: 1.250 điểm)    |
+------------------------------------------------------------------+
| Tên hàng hóa / SKU            ĐVT    SL     Đơn giá    Thành tiền|
|------------------------------------------------------------------|
| 1. Sữa tươi TH True Milk 1L   Hộp     2      36.000       72.000 |
|    [8935217400012]                                               |
| 2. Bánh quy bơ Danisa 454g    Hộp     1     145.000      145.000 |
|    [8934567890123] (KM: Giảm 10.000đ/hộp)    -10.000      135.000 |
| 3. Nước khoáng Lavie 500ml    Chai    6       5.000       30.000 |
|    [8935001234567]                                               |
+------------------------------------------------------------------+
| Tổng số lượng hàng:                                         9 SP |
| Cộng tiền hàng (Tạm tính):                             247.000 đ |
| Chiết khấu dòng hàng:                                  -10.000 đ |
| Chiết khấu tổng đơn (Voucher VIP5):                    -12.000 đ |
| Tiền trước thuế GTGT:                                  225.000 đ |
| Thuế GTGT (VAT 8%):                                     18.000 đ |
| Làm tròn (Rounding):                                         0 đ |
|------------------------------------------------------------------|
| TỔNG THANH TOÁN:                                       243.000 đ |
| (Bằng chữ: Hai trăm bốn mươi ba nghìn đồng chẵn)                 |
|------------------------------------------------------------------|
| Phương thức thanh toán:                Chuyển khoản QR / Tiền mặt|
|   - Chuyển khoản VietQR:                               143.000 đ |
|   - Tiền mặt khách đưa:                                100.000 đ |
|   - Tiền thừa trả khách:                                     0 đ |
+------------------------------------------------------------------+
|             [ MÃ QR THANH TOÁN ĐỘNG (VIETQR NAPAS247) ]          |
|                 Ngân hàng: Vietcombank - 001100xxxx              |
|                 Số tiền: 143.000 VND | ND: HDCN010089            |
+------------------------------------------------------------------+
| * Thông tin tra cứu Hóa đơn điện tử khởi tạo từ máy tính tiền:   |
|   Mã CQT: M1-26-ABC12-00000089123                                |
|   Link tra cứu: https://tracuu.qlch.vn  |  Mã tra cứu: X9K2P8    |
|                  [ MÃ VẠCH SỐ HÓA ĐƠN ĐỂ ĐỔI TRẢ ]               |
|         (Quý khách vui lòng giữ hóa đơn khi đổi trả trong 07 ngày)|
|                    CẢM ƠN & HẸN GẶP LẠI QUÝ KHÁCH!               |
+------------------------------------------------------------------+
```

### 1.2. Đặc tả Trường Dữ liệu & Quy tắc Nghiệp vụ (Chuẩn Nghị định `123/2020/NĐ-CP` & `70/2025/NĐ-CP`)

| Nhóm dữ liệu | Tên trường | Kiểu / Định dạng | Bắt buộc? | Quy tắc nghiệp vụ & Ràng buộc pháp lý |
| :--- | :--- | :--- | :---: | :--- |
| **1. Định danh Người bán** | Tên đơn vị, Tên Chi nhánh, Địa chỉ cửa hàng, Mã số thuế (`MST`), Số điện thoại | Chuỗi ký tự | **Bắt buộc** | Theo điểm a khoản 3 Điều 11 NĐ `123/2020/NĐ-CP` (sửa đổi bởi NĐ `70/2025/NĐ-CP`). |
| **2. Định danh Hóa đơn & Ca** | Số hóa đơn (`HD-{MaCN}-{YYYYMMDD}-{XXXX}`), Ngày giờ lập (`DD/MM/YYYY HH:mm:ss`), Quầy POS, Nhân viên thu ngân | Chuỗi / Thời gian | **Bắt buộc** | Nếu tạo khi đang **Offline**, sinh mã tạm cục bộ có tiền tố `OFF-` (kèm UUID) và ánh xạ sang số chính thức khi đồng bộ Server. |
| **3. Thông tin Người mua** | Tên khách hàng, SĐT, Địa chỉ, MST hoặc Số định danh cá nhân (`CCCD` 12 số) | Chuỗi ký tự | *Tùy chọn* (Khách lẻ) / **Bắt buộc** (Khi khách yêu cầu lấy HĐĐT) | Theo NĐ `70/2025/NĐ-CP`: Khách mua lẻ thông thường có thể để `"Khách lẻ"`; nếu khách yêu cầu lấy hóa đơn để kê khai thuế thì điền MST hoặc CCCD. |
| **4. Bảng kê Hàng hóa** | Mã SKU/Barcode, Tên hàng hóa, Đơn vị tính (`ĐVT`), Số lượng (`SL`), Đơn giá gốc, Chiết khấu dòng, Thuế suất GTGT (`0%`, `5%`, `8%`, `10%`, `KCT`), Thành tiền | Mảng `1..N` dòng | **Bắt buộc** | Trên khổ giấy nhỏ `K57 (58mm)`, tên hàng hóa hiển thị ở dòng 1, còn `SL x Đơn giá = Thành tiền` hiển thị thụt lề ở dòng 2 để không bị tràn lề. |
| **5. Tổng hợp Tiền & Thanh toán** | Cộng tiền hàng, Tổng chiết khấu, Tiền trước thuế, Tiền thuế GTGT, Tổng thanh toán, Tiền khách đưa (hỗ trợ **Thanh toán kết hợp / Split Payment**: Tiền mặt + Chuyển khoản QR), Tiền thừa trả khách | Số nguyên (`VNĐ`) | **Bắt buộc** | Công thức bất biến:<br>$\text{Tổng thanh toán} = \sum \text{Thành tiền sau CK dòng} - \text{CK tổng đơn} + \text{Thuế GTGT} + \text{Làm tròn}$. |
| **6. Truy xuất HĐĐT & VietQR** | Mã QR thanh toán (`VietQR` EMVCo), Mã của Cơ quan Thuế (`Mã CQT`), Mã/Link tra cứu HĐĐT, Mã vạch đơn hàng (`Code128`) | Chuỗi / QR / Barcode | *Tùy cấu hình* | Theo khoản 2 Điều 11 NĐ `123/2020/NĐ-CP`: Hóa đơn từ máy tính tiền **không bắt buộc có chữ ký số** trên bản in giao cho khách. |

---

## 2. Biểu mẫu 02 (`BM-POS-02`): Phiếu Đổi / Trả Hàng & Hoàn Tiền tại Quầy POS (`POS Return / Exchange Slip`)

Trong thực tế bán lẻ (đặc biệt ngành Thời trang, Mỹ phẩm, Gia dụng, Siêu thị), khách thường mang hàng ra quầy để **Trả hàng hoàn tiền** hoặc **Đổi sang size/mặt hàng khác**.

### 2.1. Cấu trúc Bảng Tính Bù trừ Đổi – Trả tại Quầy

```text
+------------------------------------------------------------------+
|                 PHIẾU ĐỔI / TRẢ HÀNG TẠI QUẦY POS                |
| Số phiếu: TH-CN01-20261114-0012        Ngày: 14/11/2026 15:40    |
| Tham chiếu HĐ gốc: HD-CN01-20261112-0045 (Mua ngày: 12/11/2026)  |
| Khách hàng: Chị Lê Thu Trang           Thu ngân: Nguyễn Thị Mai  |
+------------------------------------------------------------------+
| A. HÀNG KHÁCH TRẢ LẠI (NHẬP LẠI KHO):                            |
| 1. Áo sơ mi Oxford Trắng - Size M     SL: 1 x 350.000 = 350.000  |
|    Tình trạng: Nguyên tem mác (Nhập lại Kho Bán Hàng)            |
| -> Cộng giá trị hàng trả lại (A):                      350.000 đ |
|    Phí đổi/trả hàng (0%):                                    0 đ |
|------------------------------------------------------------------|
| B. HÀNG KHÁCH MUA ĐỔI MỚI (XUẤT KHO):                            |
| 1. Áo sơ mi Oxford Xanh Navy - Size L SL: 1 x 380.000 = 380.000  |
| -> Cộng giá trị hàng mua mới (B):                      380.000 đ |
+------------------------------------------------------------------+
| CHÊNH LỆCH THANH TOÁN (B - A):                         +30.000 đ |
| -> KHÁCH CẦN THANH TOÁN THÊM:                           30.000 đ |
| (Nếu B - A < 0: Cửa hàng hoàn lại tiền mặt/chuyển khoản cho khách)|
+------------------------------------------------------------------+
| Lý do đổi/trả: Đổi kích cỡ (Size M -> Size L)                    |
| Xác nhận Khách hàng                   Xác nhận Thu ngân / Quản lý|
+------------------------------------------------------------------+
```

### 2.2. Quy tắc Nghiệp vụ Rút ra cho BA & Dev
- **Định giá hàng trả lại:** Giá nhận trả lại phải lấy đúng **Đơn giá thực tế sau khuyến mãi trên Hóa đơn gốc** (không lấy giá niêm yết hiện tại để tránh khách mua lúc giảm giá 50% rồi trả lại lấy tiền theo giá gốc 100%).
- **Phân loại kho khi nhận hàng trả:** Khi thu ngân nhận hàng trả, hệ thống bắt buộc chọn 1 trong 2 trạng thái hàng:
  1. `Hàng còn tốt (Good Condition)` $\rightarrow$ Tự động cộng lại vào **Kho Bán Hàng (`Sellable Stock`)**.
  2. `Hàng lỗi / Hư hỏng (Damaged / Defective)` $\rightarrow$ Chuyển vào **Kho Hàng Lỗi / Chờ Xử Lý (`Damaged / Quarantine Stock`)**, không cộng vào tồn có thể bán để tránh bán nhầm hàng hỏng cho khách sau.

---

## 3. Biểu mẫu 03 (`BM-POS-03`): Biên bản Bàn giao Ca & Đối soát Két tiền Thu ngân (`Shift Handover`)

Biểu mẫu bắt buộc khi thu ngân bấm **"Kết ca / Đóng phiên POS"** để bàn giao két tiền cho ca tiếp theo hoặc nộp tiền cuối ngày cho Cửa hàng trưởng.

| Chỉ tiêu trên Phiếu Kết Ca | Công thức / Nguồn dữ liệu | Ví dụ số liệu (`VNĐ`) | Ghi chú kiểm soát nội bộ |
| :--- | :--- | ---: | :--- |
| **1. Tiền mặt đầu ca (`Opening Cash`)** | Số tiền lẻ để sẵn trong két lúc mở ca (kế thừa từ ca trước hoặc nạp mới) | `1.000.000` | Thu ngân xác nhận lúc Mở ca. |
| **2. Thu tiền mặt bán hàng trong ca (`Cash Sales`)** | Tổng phần thanh toán bằng **Tiền mặt** của tất cả hóa đơn trong ca | `+8.450.000` | Không bao gồm tiền khách chuyển khoản VietQR/Quẹt thẻ. |
| **3. Chi hoàn tiền mặt trả hàng (`Cash Refunds`)** | Tổng tiền mặt lấy từ két hoàn trả cho khách trả hàng trong ca | `-350.000` | Tham chiếu các phiếu `BM-POS-02` hoàn tiền mặt. |
| **4. Phiếu Thu / Chi tiền mặt khác tại quầy (`Cash In / Out`)** | Thu/chi vặt tại cửa hàng lấy từ két (VD: trả tiền nước đá, mua túi nilon, nộp bớt tiền về két tổng) | `-200.000` | Bắt buộc có phiếu chi/thu kèm lý do. |
| **5. TIỀN MẶT LÝ THUYẾT TRONG KÉT (`Expected Cash`)** | $(1) + (2) - (3) \pm (4)$ | **`8.900.000`** | Hệ thống tự động tính. |
| **6. TIỀN MẶT THỰC ĐẾM CUỐI CA (`Actual Counted Cash`)** | Thu ngân kiểm đếm thực tế (hỗ trợ bảng đếm theo mệnh giá: `500k`, `200k`, `100k`, `50k`, `20k`, `10k`, `5k`, `2k`, `1k`) | **`8.890.000`** | Thu ngân nhập trước khi đóng ca (cấu hình **Blind Close**: ẩn mục 5 cho đến khi thu ngân nhập xong mục 6 để chống gian lận). |
| **7. CHÊNH LỆCH QUỸ CA (`Cash Variance`)** | $(6) - (5)$ | **`-10.000` (Thiếu)** | Nếu $\neq 0$, bắt buộc nhập giải trình lý do và lưu vào báo cáo lệch ca gửi Chủ cửa hàng. |
| **8. Doanh thu Không tiền mặt trong ca (Đối chiếu Ngân hàng)** | Tổng tiền **VietQR / Chuyển khoản** (`12.300.000`) + **Thẻ POS** (`2.500.000`) | `14.800.000` | Kế toán đối chiếu với sao kê tài khoản ngân hàng. |

---

## 4. Biểu mẫu 04 (`BM-KHO-01`): Phiếu Nhập Kho Hàng hóa (`Mẫu số 01-VT` — Chuẩn Thông tư `133` & `200/TT-BTC`)

Áp dụng khi cửa hàng hoặc kho tổng nhận hàng mua từ Nhà cung cấp (NCC), nhập hàng sản xuất nội bộ, hoặc nhập hàng thừa phát hiện qua kiểm kê.

### 4.1. Bố cục Chuẩn `Mẫu số 01-VT` (Khổ in A4 / A5)

```text
+-----------------------------------------------------------------------------+
| ĐƠN VỊ: HỆ THỐNG CỬA HÀNG [TÊN CHUỖI]             Mẫu số 01-VT              |
| Bộ phận / Chi nhánh: Kho Tổng Hà Nội              (Ban hành theo Thông tư   |
|                                                    133/2016/TT-BTC & 200)   |
|                              PHIẾU NHẬP KHO                                 |
|                            Ngày 14 tháng 11 năm 2026                        |
|                                Số: PNK-KT-202611-0024                       |
| - Họ và tên người giao hàng: Nguyễn Văn Nam - Công ty TNHH Phân phối ABC   |
| - Theo Hóa đơn số: 0004582 ngày 14/11/2026 của Công ty TNHH Phân phối ABC   |
| - Nhập tại kho: Kho Tổng Hà Nội  |  Địa điểm: KCN Cầu Giấy, Hà Nội          |
+-----+--------------------------+----------+------+------------+---------+-----------+
| STT | Tên, nhãn hiệu, quy cách | Mã số    | ĐVT  | Số lượng   | Đơn giá | Thành tiền|
|     | phẩm chất vật tư, HH     | (SKU)    |      | C.Từ |Thực | (VNĐ)   | (VNĐ)     |
|     |                          |          |      |      |nhập |         |           |
+-----+--------------------------+----------+------+------+-----+---------+-----------+
|  A  |            B             |    C     |  D   |  1   |  2  |    3    | 4 = 2 x 3 |
+-----+--------------------------+----------+------+------+-----+---------+-----------+
|  1  | Sữa tươi TH True Milk 1L | SKU-0001 | Thùng|  20  |  20 | 380.000 | 7.600.000 |
|     | (Lô: L2611 - HSD: 05/27) |          | (12H)|      |     |         |           |
|  2  | Bánh quy Danisa 454g     | SKU-0042 | Thùng|  10  |   9 |1.440.000|12.960.000 |
|     | (Thiếu 1 thùng so với HĐ)|          | (12H)|      |     |         |           |
+-----+--------------------------+----------+------+------+-----+---------+-----------+
| Cộng tiền hàng thực nhập:                                                20.560.000 |
| Chiết khấu thương mại Nhà cung cấp (-):                                    -560.000 |
| Thuế GTGT đầu vào (+):                                                    1.600.000 |
| Chi phí vận chuyển/bốc xếp phân bổ vào giá vốn (+):                         200.000 |
| TỔNG CỘNG GIÁ TRỊ NHẬP KHO:                                              21.800.000 |
| Đã thanh toán cho NCC: 10.000.000 đ  |  Còn ghi nợ công nợ NCC: 11.800.000 đ        |
+-----------------------------------------------------------------------------+
| - Tổng số tiền (viết bằng chữ): Hai mươi mốt triệu tám trăm nghìn đồng chẵn.|
| - Số chứng từ gốc kèm theo: 01 Hóa đơn GTGT + 01 Biên bản giao nhận.        |
|                                                                             |
|   Người lập phiếu      Người giao hàng       Thủ kho        Kế toán trưởng  |
|   (Ký, họ tên)          (Ký, họ tên)       (Ký, họ tên)      (Ký, họ tên)   |
+-----------------------------------------------------------------------------+
```

### 4.2. Quy tắc Nghiệp vụ Cốt lõi của Phiếu Nhập Kho
- **Tách cột `Số lượng theo chứng từ` và `Số lượng thực nhập`:** Trong thực tế, NCC có thể xuất hóa đơn 10 thùng nhưng giao thực tế chỉ có 9 thùng (1 thùng bị móp/thiếu). Hệ thống **chỉ cộng tồn kho và tính công nợ phải trả theo `Số lượng thực nhập`**.
- **Tự động quy đổi Đơn vị tính & Tính lại Giá vốn bình quân (`Moving Average Cost — MAC`):**
  - Khi nhập `20 Thùng` (mỗi thùng `12 Hộp`) với giá `380.000đ/Thùng`, nếu đơn vị cơ sở quản lý tồn kho là `Hộp`, hệ thống tự động cộng `240 Hộp` vào kho và cập nhật giá vốn bình quân gia quyền:
    $$\text{Giá vốn mới} = \frac{(\text{Tồn cũ} \times \text{Giá vốn cũ}) + (\text{SL thực nhập} \times \text{Đơn giá nhập sau CK + Chi phí nhập})}{\text{Tồn cũ} + \text{SL thực nhập}}$$

---

## 5. Biểu mẫu 05 (`BM-KHO-02`): Phiếu Xuất Kho & Phiếu Xuất Hủy Hàng hóa (`Mẫu số 02-VT`)

Áp dụng cho các nghiệp vụ xuất kho không qua màn hình POS bán lẻ: **(1) Xuất bán buôn/giao sỉ**, **(2) Xuất trả lại Nhà cung cấp**, **(3) Xuất sử dụng nội bộ**, hoặc **(4) Xuất hủy hàng hỏng / vỡ / hết hạn sử dụng**.

| Nhóm trường dữ liệu | Các trường chi tiết theo `Mẫu số 02-VT` (TT133 / TT200) | Quy tắc xử lý trong hệ thống `QLCH` |
| :--- | :--- | :--- |
| **Thông tin chung** | • Số phiếu (`PXK-{MaCN}-{YYYYMM}-{XXXX}`), Ngày tháng năm lập<br>• Họ tên người nhận hàng, Bộ phận / Địa chỉ nhận<br>• **Lý do xuất kho** (`Xuất bán sỉ` / `Xuất trả NCC` / `Xuất nội bộ` / `Xuất hủy hàng hỏng - hết hạn`)<br>• Xuất tại kho (Chi nhánh / Kho con) | Khi chọn lý do **`Xuất hủy`**, hệ thống tự động hạch toán giá trị hàng hủy (theo Giá vốn hiện tại) vào khoản mục **Chi phí hao hụt / Hủy hàng** trong báo cáo lãi lỗ. |
| **Bảng kê chi tiết** | • STT, Tên/quy cách hàng hóa, Mã SKU/Barcode, Đơn vị tính<br>• **Số lượng Yêu cầu** vs **Số lượng Thực xuất**<br>• Đơn giá xuất (Giá vốn hoặc Giá bán buôn), Thành tiền | Kiểm tra ràng buộc: Không cho phép `Số lượng Thực xuất > Tồn khả dụng (Available)` trừ khi cửa hàng bật cấu hình cho phép bán/xuất âm tồn kho. |
| **Chữ ký xác nhận** | • Người lập phiếu, Người nhận hàng, Thủ kho, Kế toán trưởng, Giám đốc/Chủ cửa hàng | Trên phần mềm: Tương ứng với luồng trạng thái `Nháp (Draft)` $\rightarrow$ `Chờ duyệt (Pending)` $\rightarrow$ `Đã xuất kho (Completed)` kèm lưu vết User ID & Timestamp. |

---

## 6. Biểu mẫu 06 (`BM-KHO-03`): Phiếu Điều chuyển Kho Liên Chi nhánh (`Inter-Branch Stock Transfer`)

Đây là chứng từ quan trọng bậc nhất đối với mô hình **Chuỗi cửa hàng (`Multi-store`)**, giải quyết bài toán luân chuyển hàng từ Kho tổng xuống các cửa hàng hoặc điều hàng từ Chi nhánh thừa sang Chi nhánh thiếu.

### 6.1. Sơ đồ Trạng thái & Bố cục Phiếu Điều chuyển Liên Chi nhánh

```text
[1. Tạo Yêu cầu / Nháp] ---> [2. Kho Đi Xuất Chuyển (Đang vận chuyển / In-Transit)] ---> [3. Kho Đến Xác nhận Thực Nhận (Hoàn thành)]
                               (Kho Đi đã trừ tồn khả dụng; Kho Đến chưa cộng tồn)         (Kho Đến cộng tồn thực nhận; xử lý lệch nếu có)
```

```text
+-----------------------------------------------------------------------------+
|                PHIẾU ĐIỀU CHUYỂN KHO NỘI BỘ LIÊN CHI NHÁNH                  |
|            (Kiêm Phiếu Xuất Kho Vận Chuyển Nội Bộ)                          |
| Số phiếu: PDC-20261114-0018             Trạng thái: [ ĐANG VẬN CHUYỂN ]     |
|-----------------------------------------------------------------------------|
| TỪ KHO (KHO XUẤT):  Kho Tổng Hà Nội     Người xuất: Trần Văn Bình (Thủ kho) |
|                     Thời gian xuất:     14/11/2026 08:30                    |
| ĐẾN KHO (KHO NHẬN): Chi nhánh 02 - Đống Đa  Người nhận: Phạm Thị Lan        |
|                     Thời gian nhận:     14/11/2026 11:15                    |
| Phương tiện / Người vận chuyển: Xe tải nội bộ 29C-123.45 (Tài xế: Lê Văn C) |
+-----+--------------------------+----------+------+--------+--------+--------+
| STT | Tên hàng hóa / Quy cách  | Mã SKU   | ĐVT  | SL Yêu | SL Xuất| SL Thực|
|     |                          |          |      | cầu    | chuyển | nhận   |
+-----+--------------------------+----------+------+--------+--------+--------+
|  1  | Sữa tươi TH True Milk 1L | SKU-0001 | Hộp  |   120  |   120  |   120  |
|  2  | Bánh quy Danisa 454g     | SKU-0042 | Hộp  |    50  |    50  |    48  |
|     | -> Ghi chú lệch: 02 hộp bị móp vỏ khi vận chuyển, trả lại Kho Tổng   |
+-----+--------------------------+----------+------+--------+--------+--------+
| Tổng cộng số lượng:                              |   170  |   170  |   168  |
+-----------------------------------------------------------------------------+
| Xác nhận Thủ kho Xuất        Người vận chuyển         Xác nhận Thủ kho Nhận |
|     (Ký, họ tên)               (Ký, họ tên)               (Ký, họ tên)      |
+-----------------------------------------------------------------------------+
```

### 6.2. Quy tắc Nghiệp vụ Chống Thất thoát khi Điều chuyển Kho
1. **Không bao giờ cộng tồn ngay vào Kho Nhận khi Kho Xuất vừa bấm Xuất:** Hàng hóa cần thời gian di chuyển vật lý (vài giờ đến vài ngày). Trong thời gian đó, lượng hàng này phải nằm ở trạng thái **`Đang vận chuyển (In-Transit)`** để:
   - Kho Xuất không bán nhầm hàng đã đóng thùng gửi đi.
   - Kho Nhận không bán nhầm hàng chưa về tới cửa hàng.
   - Báo cáo tổng tài sản toàn chuỗi vẫn nhìn thấy đầy đủ giá trị hàng đang đi trên đường.
2. **Xử lý chênh lệch khi `SL Thực nhận < SL Xuất chuyển`:** Hệ thống giữ phần chênh lệch (`2 hộp`) ở trạng thái `Lệch chờ xử lý` để Quản lý chuỗi quyết định: (a) Hoàn trả lại về Kho Xuất, hoặc (b) Lập phiếu xuất hủy/bắt đền đơn vị vận chuyển.

---

## 7. Biểu mẫu 07 (`BM-KHO-04`): Biên bản Kiểm kê Hàng hóa & Cân bằng Kho (`Mẫu số 05-VT`)

Tuân thủ đúng kết cấu **`Mẫu số 05-VT`** (*Biên bản kiểm kê vật tư, công cụ, sản phẩm, hàng hóa* ban hành theo Thông tư `133/2016/TT-BTC` & `200/2014/TT-BTC`), đồng thời tối ưu cho thao tác kiểm kho bằng máy quét mã vạch/điện thoại tại cửa hàng.

### 7.1. Cấu trúc Bảng Kiểm kê Chuẩn `Mẫu số 05-VT`

```text
+---------------------------------------------------------------------------------------------------+
| ĐƠN VỊ: HỆ THỐNG CỬA HÀNG [TÊN CHUỖI]                                         Mẫu số 05-VT        |
| Chi nhánh / Kho: Cửa hàng Số 01 - Cầu Giấy                         (Ban hành theo TT 133 & TT 200)|
|                        BIÊN BẢN KIỂM KÊ HÀNG HÓA TỒN KHO                                          |
| - Thời điểm chốt số liệu kiểm kê: 22 giờ 00 ngày 14 tháng 11 năm 2026 (Số phiếu: PKK-CN01-2611-05)|
| - Phạm vi kiểm kê: [ Toàn bộ kho ] hoặc [ Theo nhóm hàng: Sữa & Bánh kẹo ]                        |
| - Ban kiểm kê gồm: Ông/Bà Nguyễn Văn A (Cửa hàng trưởng - Trưởng ban), Bà Lê Thị B (Thủ kho)      |
+-----+--------------------+--------+-----+---------+-------------+-------------+-------------------+
| STT | Tên hàng hóa,      | Mã SKU | ĐVT | Đơn giá | Theo Sổ/Hệ  | Theo Kiểm   | Chênh lệch        |
|     | nhãn hiệu, quy cách|        |     | vốn     | thống       | kê Thực tế  | (Thực tế - Sổ)    |
|     |                    |        |     | (VNĐ)   |------+------+------+------+------+------------+
|     |                    |        |     |         |  SL  | Tiền |  SL  | Tiền | Thừa | Thiếu      |
+-----+--------------------+--------+-----+---------+------+------+------+------+------+------------+
|  1  | Sữa TH True Milk 1L|SKU-0001| Hộp |  31.667 |  100 |3.167k|  102 |3.230k|  +2  |     0      |
|  2  | Bánh Danisa 454g   |SKU-0042| Hộp | 120.000 |   45 |5.400k|   43 |5.160k|   0  |    -2      |
|     | (Phẩm chất: 42 hộp tốt 100%, 01 hộp rách vỏ kém phẩm chất)                                  |
+-----+--------------------+--------+-----+---------+------+------+------+------+------+------------+
| TỔNG CỘNG CHÊNH LỆCH: Tổng giá trị Thừa: +63.334 đ  |  Tổng giá trị Thiếu: -240.000 đ             |
| -> Ý kiến giải quyết chênh lệch của Chủ cửa hàng / Giám đốc:                                      |
|    [x] Duyệt Cân bằng kho tự động (Sinh Phiếu Nhập điều chỉnh +2 hộp SKU-0001 & Phiếu Xuất điều   |
|        chỉnh -2 hộp SKU-0042).                                                                    |
+---------------------------------------------------------------------------------------------------+
|     Giám đốc / Chủ CH          Kế toán          Thủ kho          Người kiểm đếm / Trưởng ban KK   |
|       (Ký, họ tên)           (Ký, họ tên)     (Ký, họ tên)                (Ký, họ tên)            |
+---------------------------------------------------------------------------------------------------+
```

### 7.2. Quy tắc Nghiệp vụ & UX Kiểm kê Kho Thực tế cho `QLCH`
1. **Chốt mốc tồn kho (`Snapshot System Stock`):** Khi tạo Phiếu kiểm kê, hệ thống ghi nhận số `Tồn hệ thống tại thời điểm bắt đầu kiểm`. Khi nhân viên bấm **"Cân bằng kho (`Balance Inventory`)"**, hệ thống cập nhật tồn kho thực tế và tự động sinh các bản ghi điều chỉnh tăng/giảm (`Inventory Adjustment`) trong Thẻ kho (`Stock Card`).
2. **Hỗ trợ 3 колон Phẩm chất hàng hóa (Theo chuẩn `Mẫu số 05-VT`):**
   - `Còn tốt 100%` (Bán bình thường).
   - `Kém phẩm chất` (Móp vỏ, cận date — đề xuất chuyển sang khu vực giảm giá xả hàng).
   - `Mất phẩm chất / Hư hỏng` (Vỡ, hết hạn — đề xuất chuyển sang lập Phiếu xuất hủy `BM-KHO-02`).
3. **Chế độ Quét mã vạch cộng dồn (`Barcode Scan Tally`):** Cho phép nhân viên dùng điện thoại hoặc máy quét bắn liên tiếp mã vạch trên kệ; mỗi lần quét cùng 1 mã vạch thì cột `SL Thực tế` tự động tăng `+1`, giúp kiểm kho nhanh gấp 5 lần so với gõ số thủ công.
