# Báo cáo Khảo sát Thị trường & Xu hướng Phần mềm Quản lý Cửa hàng / Chuỗi Bán lẻ (POS) tại Việt Nam

- **Mã tài liệu đề xuất đăng ký:** `REF-MKT-003`
- **Dự án khởi tạo nhu cầu:** `QLCH` — Quản lý hệ thống cửa hàng (`Store / Retail Chain Management System`)
- **Mã công việc:** `QLCH-MKT-01` (GitHub Issue [`#3`](https://github.com/theGonlyK/QLCH/issues/3))
- **Vai trò thực hiện:** `Marketing Lead` (áp dụng chuẩn `3.DOC_AI/skills/marketing-research/SKILL.md`)
- **Ngày thu thập & lập báo cáo:** `2026-11-14`
- **Trạng thái:** Hoàn thành Desk Research — Bàn giao cho `PM Dự án QLCH`, `BA Lead`, `UX Lead` và `Tech Lead` phục vụ **Cổng Brief**

> **Tuyên bố tuân thủ `RULES_CORE.md` & `marketing-research/SKILL.md`:**
> Báo cáo này cung cấp bằng chứng thị trường, phân tích đối thủ và xu hướng vận hành thực tế có nguồn trích dẫn rõ ràng. Báo cáo **không tự chốt phạm vi sản phẩm, mô hình giá, kiến trúc kỹ thuật hay độ ưu tiên tính năng** cho dự án `QLCH`. Mọi đề xuất liên quan đến `QLCH` đều được gắn nhãn `Cần xác nhận` và tham chiếu trực tiếp tới bộ câu hỏi Cổng Brief (`Q-QLCH-01` $\rightarrow$ `Q-QLCH-05`) tại [`02-nghiep-vu/REQUIREMENTS.md`](../../02-nghiep-vu/REQUIREMENTS.md).

---

## 1. Mục tiêu, Câu hỏi Nghiên cứu, Phương pháp & Giới hạn Mẫu

### 1.1. Câu hỏi nghiên cứu trọng tâm (Bám sát Cổng Brief `QLCH`)
1. **RQ-01 (Phân khúc & Mô hình chuỗi — hỗ trợ `Q-QLCH-01`):** Các phần mềm quản lý cửa hàng/POS phổ biến tại Việt Nam đang phục vụ những ngành hàng nào và tổ chức mô hình đa chi nhánh (`Multi-branch` vs `Multi-tenant SaaS`) ra sao?
2. **RQ-02 (Cấu trúc phân hệ cốt lõi — hỗ trợ `Q-QLCH-02`):** Bộ tính năng tiêu chuẩn (Baseline) của một phần mềm quản lý cửa hàng/chuỗi bán lẻ tại Việt Nam gồm những nhóm nghiệp vụ nào? Đâu là ranh giới giữa gói cơ bản (1 cửa hàng) và gói chuỗi chi nhánh?
3. **RQ-03 (Trải nghiệm thiết bị & Quầy thu ngân — hỗ trợ `Q-QLCH-03`):** Giao diện POS tại quầy, Web quản trị và Mobile App cho chủ cửa hàng/nhân viên được phân bổ vai trò như thế nào để tối ưu tốc độ bán hàng?
4. **RQ-04 (Vận hành Offline, Phần cứng & Hóa đơn/Thanh toán — hỗ trợ `Q-QLCH-04`):** Các đối thủ xử lý bài toán mất kết nối mạng (Offline POS), kết nối thiết bị ngoại vi (máy in bill, máy quét mã vạch), mã VietQR và Hóa đơn điện tử khởi tạo từ máy tính tiền theo quy định mới (Nghị định `123/2020/NĐ-CP` & Nghị định `70/2025/NĐ-CP`) như thế nào?

### 1.2. Phương pháp, Cỡ mẫu & Cách chọn mẫu
- **Phương pháp:** Nghiên cứu tại bàn (*Desk Research*) trên dữ liệu công khai chính thức của nhà cung cấp (trang tính năng, bảng giá niêm yết, tài liệu hướng dẫn sử dụng) và văn bản pháp quy hiện hành của Bộ Tài chính / Chính phủ truy cập ngày `2026-11-14`.
- **Cỡ mẫu & Tiêu chí chọn mẫu ($N = 5$ nền tảng đại diện):**
  1. **KiotViet (`kiotviet.vn`):** Đại diện thị phần dẫn đầu nhóm cửa hàng bán lẻ SME & hộ kinh doanh tại Việt Nam (tuyên bố $>300.000$ cửa hàng sử dụng).
  2. **Sapo POS / Sapo Omnichannel (`sapo.vn`):** Đại diện nhóm bán lẻ hợp kênh (*Omnichannel*) và quản trị chuỗi cửa hàng vừa & lớn.
  3. **Haravan — HaraRetail (`haravan.com`):** Đại diện nhóm chuỗi bán lẻ thương hiệu (*Brand Retail*), D2C và tích hợp sâu CRM/Loyalty/E-commerce.
  4. **PosApp (`posapp.vn`):** Đại diện nhóm POS đa nền tảng mạnh về thiết bị phần cứng thu ngân cầm tay/2 màn hình, F&B, dịch vụ tính giờ và bán lẻ (tuyên bố $>135.000$ cửa hàng).
  5. **Odoo POS (`odoo.com`):** Đại diện hệ thống ERP mã nguồn mở / Cloud quốc tế có phân hệ POS tích hợp chặt với Kho (*Inventory*) và Kế toán (*Accounting*), có cơ chế PWA Offline-first điển hình.

### 1.3. Giới hạn & Sai lệch cần lưu ý (Limitations & Biases)
- **Sai lệch từ thông điệp công bố của nhà cung cấp:** Các con số về số lượng cửa hàng và tuyên bố "đồng bộ tức thì / không giới hạn" trên trang giới thiệu là thông điệp marketing của nhà cung cấp; hiệu năng thực tế khi kho có hàng chục nghìn SKU hoặc mạng chập chờn cần được kiểm chứng kỹ thuật độc lập.
- **Biến động giá & gói khuyến mãi:** Giá niêm yết trên website thường yêu cầu thanh toán chu kỳ 12–24 tháng và chưa bao gồm chi phí thiết bị phần cứng, phí khởi tạo hóa đơn điện tử vượt gói tặng kèm hoặc phí ZNS/SMS bên thứ ba.
- **Chưa bao gồm phỏng vấn người dùng thực địa:** Báo cáo này là bước Desk Research đầu vào cho Cổng Brief; kế hoạch phỏng vấn chủ cửa hàng/thu ngân thực tế được đề xuất tại **Mục 6** và chỉ triển khai khi có phê duyệt của PM/Chủ dự án.

---

## 2. Tổng quan Thị trường & Phân khúc 5 Giải pháp POS / Quản lý Chuỗi tại Việt Nam

### 2.1. Bảng định vị thị trường & Mô hình thương mại (Dữ liệu thu thập ngày `2026-11-14`)

| Nền tảng | Định vị cốt lõi & Ngành hàng mục tiêu | Mô hình gói & Giá niêm yết tham khảo (VNĐ/tháng) | Chính sách mở rộng Chi nhánh / Kho | Nguồn xác minh trực tiếp (`2026-11-14`) |
| :--- | :--- | :--- | :--- | :--- |
| **1. KiotViet** | **Bán buôn - Bán lẻ SME, Tạp hóa, Thời trang, Điện máy, Nhà thuốc, F&B, Lưu trú.**<br>Tập trung vào tính đơn giản, dễ dùng cho hộ kinh doanh & chuỗi vừa. | • **Hỗ trợ:** `250.000đ – 270.000đ/tháng` (1 cửa hàng, tối đa 3 user).<br>• **Chuyên nghiệp:** `310.000đ – 330.000đ/tháng` (1 cửa hàng, không giới hạn user, đa kênh TMĐT/MXH).<br>• **Cao cấp:** `490.000đ/tháng` (1 cửa hàng, không giới hạn user, Public API, phân tích chuyên sâu). | • Thêm chi nhánh: `~270.000đ – 375.000đ/chi nhánh/tháng` (tùy gói).<br>• Thêm kho độc lập: `~150.000đ/kho/tháng`. | • [`kiotviet.vn/phi-dich-vu/`](https://www.kiotviet.vn/phi-dich-vu/) |
| **2. Sapo POS / Omnichannel** | **Bán lẻ đa kênh, Chuỗi cửa hàng, F&B, Dịch vụ.**<br>Thế mạnh kết nối POS tại quầy với Shopee/TikTok Shop/Facebook và hệ sinh thái Thuế/HĐĐT (`Sapo 6870`, `Sapo Invoice`). | • **Start Up:** `170.000đ/tháng` (1 kênh bán, tối đa 3 nhân viên).<br>• **Pro (Retail Pro):** `249.000đ/tháng` (Đa kênh cơ bản).<br>• **Omni:** `449.000đ/tháng` (10 gian hàng, không giới hạn nhân viên).<br>• **Advanced:** `600.000đ/tháng` (**2 cửa hàng**, Open API).<br>• **Growth:** `999.000đ/tháng` (**5 cửa hàng**, quản trị chuỗi). | • Mua thêm chi nhánh (gói Advanced/Growth): `200.000đ/cửa hàng/tháng`.<br>• **Sapo Enterprise:** Báo giá riêng cho chuỗi lớn không giới hạn điểm bán. | • [`sapo.vn/bang-gia.html`](https://www.sapo.vn/bang-gia.html)<br>• [`sapo.vn/phan-mem-quan-ly-ban-hang.html`](https://www.sapo.vn/phan-mem-quan-ly-ban-hang.html) |
| **3. Haravan (HaraRetail)** | **Chuỗi bán lẻ thương hiệu (Fashion, Mỹ phẩm, Mẹ & Bé, Nội thất), Omnichannel & Loyalty.**<br>Tập trung đồng bộ Online-to-Offline (O2O), phân hạng thành viên và tự động hóa CSKH. | • **Standard:** `300.000đ/tháng` (**1 cửa hàng**, 10 nhân viên).<br>• **Omni Pro:** `680.000đ/tháng` (**2 cửa hàng**, 10 nhân viên + Website).<br>• **Omni Advanced:** `800.000đ/tháng` (**2 cửa hàng**, 10 nhân viên).<br>• **Grow:** `1.500.000đ/tháng` (**5 cửa hàng**, 25 nhân viên, CRM/Loyalty).<br>• **Scale:** `3.000.000đ/tháng` (**8 cửa hàng**, 50 nhân viên). | • Thêm chi nhánh: từ `200.000đ/cửa hàng/tháng`.<br>• **Priority / Enterprise:** Từ `8.000.000đ/tháng` (8+ cửa hàng, không giới hạn nhân viên, ERP/API riêng). | • [`haravan.com/pages/pricing`](https://www.haravan.com/pages/pricing)<br>• [`haravan.com/pages/phan-mem-quan-ly-cua-hang-hararetail`](https://www.haravan.com/pages/phan-mem-quan-ly-cua-hang-hararetail) |
| **4. PosApp** | **Bán lẻ (Siêu thị, Tạp hóa, Shop), F&B, Dịch vụ tính giờ (Bida/Karaoke), Spa & Chuỗi nhượng quyền.**<br>Mạnh về đồng bộ thiết bị POS Android, Kiosk, QR Order và Zalo Mini App. | • **Khởi Đầu:** `~220.000đ/tháng/điểm bán` (Không giới hạn thiết bị đăng nhập, POS, kho cơ bản, xuất HĐĐT MTT).<br>• **Nâng Cao:** `~299.000đ/tháng/điểm bán` (Nhiều kho hàng, kho sản xuất/chế biến, CRM hạng thẻ).<br>• **Phát Triển (PRO):** Liên hệ báo giá (Chuỗi & Nhượng quyền). | • Tính phí theo điểm bán/tháng; ưu đãi giảm `10%` khi mở thêm chi nhánh mới; chuỗi $\ge 20$ điểm bán báo giá riêng.<br>• Cung cấp Open API kết nối SAP, Odoo, Bravo. | • [`posapp.vn/phi-dich-vu`](https://posapp.vn/phi-dich-vu)<br>• [`posapp.vn/`](https://posapp.vn/) |
| **5. Odoo POS** | **Hệ thống ERP tích hợp toàn diện (POS + Kho + Kế toán + Mua hàng + HRM + E-commerce).**<br>Phù hợp doanh nghiệp cần chuẩn hóa quy trình kho – kế toán đa công ty/đa chi nhánh hoặc tự chủ mã nguồn. | • **One App Free:** `0 USD` (Miễn phí trọn đời nếu chỉ dùng duy nhất 1 app POS trên Cloud, nhưng bị giới hạn khi cần cài thêm Inventory/Accounting).<br>• **Standard:** `~7,25 – 9,10 USD/user/tháng` (Tất cả ứng dụng trên Odoo Online).<br>• **Custom:** `~10,90 – 13,60 USD/user/tháng` (Multi-company, Odoo Studio, External API, tự host On-premise / Odoo.sh). | • Không tính phí theo số cửa hàng vật lý mà tính theo **số lượng người dùng (User/Light User)**.<br>• Hỗ trợ cấu hình không giới hạn điểm bán POS gắn với từng Kho/Vị trí kho (*Stock Location*). | • [`odoo.com/vi_VN/app/point-of-sale-shop`](https://www.odoo.com/vi_VN/app/point-of-sale-shop)<br>• [`odoo.com/vi_VN/pricing`](https://www.odoo.com/vi_VN/pricing) |

---

## 3. Phân tích Chuyên sâu theo Câu hỏi Nghiên cứu & Xu hướng Thị trường (`2025–2026`)

### 3.1. Mô hình quản lý hàng hóa (SKU) & Chuỗi đa chi nhánh (`RQ-01`, `RQ-02`)
- **Dữ kiện đã xác minh từ nguồn công khai:**
  - Cả 5 nền tảng đều tách biệt khái niệm **Điểm bán (Cửa hàng/POS)** và **Kho hàng (Warehouse/Location)**: một chi nhánh có thể có 1 kho bán hàng trực tiếp + 1 kho trữ hàng (hoặc 1 kho tổng cấp hàng cho nhiều chi nhánh).
  - Cấu trúc danh mục hàng hóa trên thị trường chia làm 4 kiểu quản lý tồn kho đặc thù theo ngành hàng:
    1. **Hàng hóa tiêu chuẩn & Quy đổi đơn vị tính (UoM):** Ví dụ Tạp hóa/Siêu thị mini nhập theo *Thùng (24 lon)*, bán lẻ theo *Lon* hoặc *Lốc (6 lon)* — cùng 1 mặt hàng nhưng tự động quy đổi số lượng tồn kho gốc.
    2. **Hàng hóa nhiều biến thể (Variants — Màu sắc / Kích cỡ / Chất liệu):** Đặc thù ngành Thời trang, Giày dép, Phụ kiện (1 mã sản phẩm cha sinh ra $N \times M$ mã SKU con kèm mã vạch riêng).
    3. **Hàng hóa quản lý theo Lô & Hạn sử dụng (Batch / Lot & Expiry Date — FEFO):** Đặc thù ngành Dược phẩm, Mỹ phẩm, Thực phẩm, Mẹ & Bé (cảnh báo hàng sắp hết hạn và ưu tiên xuất lô hết hạn trước).
    4. **Hàng hóa quản lý theo Serial / IMEI (Định danh từng cá thể):** Đặc thù ngành Điện thoại, Điện máy, Linh kiện công nghệ (theo dõi bảo hành trên từng mã IMEI xuất bán).
  - **Nghiệp vụ điều chuyển kho liên chi nhánh (`Stock Transfer`):** Không trừ/cộng tồn kho tức thời 1 chiều mà luôn đi qua **quy trình 2 bước (hoặc 3 trạng thái)**: `Phiếu xuất điều chuyển (Kho đi trừ tồn khả dụng)` $\rightarrow$ `Đang vận chuyển (Hàng In-Transit)` $\rightarrow$ `Chi nhánh đích xác nhận thực nhận (Kho đến cộng tồn / Ghi nhận chênh lệch nếu thiếu hàng)`.
  - **Chính sách giá theo chi nhánh (`Branch Pricelist`):** KiotViet, Sapo (Growth), Haravan (Omni Pro+), PosApp (PRO) và Odoo POS đều hỗ trợ thiết lập bảng giá bán khác nhau theo từng chi nhánh/khu vực (ví dụ: chi nhánh trung tâm hoặc sân bay có giá cao hơn chi nhánh ngoại thành) bên cạnh bảng giá chung toàn chuỗi.

### 3.2. Trải nghiệm Quầy thu ngân (POS), Phân tách Vai trò & Chế độ Offline (`RQ-03`, `RQ-04`)
- **Dữ kiện đã xác minh từ nguồn công khai:**
  - **Giao diện thu ngân tốc độ cao (2D Task-oriented UI):** 100% phần mềm khảo sát sử dụng giao diện 2D phẳng, mật độ thông tin cao, tối ưu cho **phím tắt bàn phím (`F1–F12`, `Enter`)** trên PC/Laptop hoặc **ô lưới nút bấm lớn (Touch Grid)** trên máy POS cảm ứng/Tablet. Thu ngân có thể mở **nhiều tab hóa đơn cùng lúc (Tạm tính / Hold Bill)** khi khách trước đang tìm thêm đồ hoặc chờ chuyển khoản để thanh toán cho khách sau.
  - **Cơ chế Bán hàng Offline (Offline-first POS):**
    - KiotViet, PosApp và Odoo POS đều công bố khả năng bán hàng không gián đoạn khi mất kết nối Internet.
    - Cụ thể trên **Odoo POS** (kiến trúc Web/PWA chuẩn): khi mở ca (*POS Session*), trình duyệt tải trước danh mục sản phẩm, bảng giá, khách hàng vào bộ nhớ cục bộ (`IndexedDB` / Local Cache). Khi rớt mạng, thu ngân vẫn quét mã vạch, tạo đơn, tính tiền và in bill nhiệt qua mạng nội bộ/USB; đơn hàng nằm trong hàng đợi đồng bộ (*Sync Queue*) và tự động đẩy lên Server khi có mạng trở lại.
  - **Kiểm soát Ca làm việc & Két tiền (`POS Shift & Cash Drawer Reconciliation`):**
    - Quy trình chuẩn tại quầy: `Mở ca (Nhập tiền mặt đầu ca / Tiền lẻ thối khách)` $\rightarrow$ `Bán hàng & Thu/Chi tiền mặt tại két` $\rightarrow$ `Kết ca / Bàn giao ca (Nhập số tiền mặt thực đếm trong két)` $\rightarrow$ `Hệ thống đối chiếu Tiền lý thuyết vs Tiền thực tế (Báo Thừa/Thiếu quỹ ca)`.
    - Phân quyền chống gian lận (*Anti-fraud RBAC*): Nhân viên thu ngân thường bị chặn quyền xem **Giá vốn / Lợi nhuận gộp**, chặn quyền tự ý xóa hóa đơn đã thanh toán hoặc sửa giá bán thấp hơn sàn nếu không có mã PIN/phê duyệt của Cửa hàng trưởng.

### 3.3. Xu hướng Pháp lý Thuế, Hóa đơn điện tử Máy tính tiền & Thanh toán VietQR (`2025–2026`)
- **Dữ kiện đã xác minh từ nguồn công khai:**
  1. **Bùng nổ tích hợp Hóa đơn điện tử khởi tạo từ máy tính tiền (HĐĐT MTT) & Kê khai thuế Hộ kinh doanh:**
     - Theo **Nghị định `70/2025/NĐ-CP`** (có hiệu lực từ `01/06/2025`, sửa đổi Nghị định `123/2020/NĐ-CP`), hộ kinh doanh có doanh thu từ **01 tỷ đồng/năm trở lên** và doanh nghiệp bán lẻ trực tiếp đến người tiêu dùng bắt buộc sử dụng hóa đơn điện tử khởi tạo từ máy tính tiền kết nối dữ liệu với Cơ quan Thuế.
     - KiotViet, Sapo (`Sapo 6870`), Haravan và PosApp đều đã đưa "Xuất HĐĐT từ máy tính tiền + Sổ kế toán/Thuế Hộ kinh doanh" thành thông điệp bán hàng mũi nhọn ngay trên trang chủ và bảng giá năm 2026.
  2. **Thanh toán QR động (Dynamic VietQR) hiển thị tại quầy / in trên hóa đơn:**
     - Thay vì dán mã QR tĩnh (khách phải tự gõ số tiền dễ nhầm lẫn và thu ngân phải chụp màn hình bill để đối chiếu), các hệ thống POS hiện tại đều tự động sinh **mã VietQR động chứa chính xác số tiền đơn hàng và mã hóa đơn (`Order ID`)**, hiển thị trên màn hình phụ hướng về phía khách (*Customer Display*) hoặc in trực tiếp ở chân phiếu tạm tính/hóa đơn nhiệt K80.

---

## 4. Tổng hợp Điểm đau (Pain Points), Diễn giải & Giả thuyết cho Dự án `QLCH`

### 4.1. Phân tách Dữ kiện — Diễn giải — Giả thuyết (Theo chuẩn `marketing-research/SKILL.md`)

| Phân loại | Nội dung chi tiết | Mức độ tin cậy & Nguồn |
| :--- | :--- | :--- |
| **1. Dữ kiện đã xác minh (*Verified Facts*)** | • Cả 5 đối thủ đều cung cấp 6 nhóm nghiệp vụ lõi: (1) Danh mục hàng hóa/SKU/Mã vạch, (2) Bán hàng POS & In bill/VietQR, (3) Quản lý kho (Nhập - Xuất - Điều chuyển - Kiểm kê), (4) Quản lý khách hàng/Tích điểm, (5) Quản lý ca thu ngân & Phân quyền nhân viên, (6) Báo cáo doanh thu - lãi lỗ - công nợ.<br>• Chi phí thuê bao phần mềm POS thương mại tại VN dao động từ `170.000đ – 330.000đ/tháng` cho 1 cửa hàng đơn lẻ, nhưng tăng lên `600.000đ – 3.000.000đ+/tháng` khi vận hành chuỗi từ 2–8 chi nhánh (cộng thêm phí mua thêm từng chi nhánh `200.000đ – 375.000đ/tháng`).<br>• Hóa đơn bán lẻ từ máy tính tiền theo NĐ `70/2025/NĐ-CP` không bắt buộc chữ ký số trên từng bill bán lẻ nhưng bắt buộc có thông tin người bán (Tên, Địa chỉ, MST), chi tiết hàng hóa/thuế suất và mã tra cứu của Cơ quan Thuế. | **Cao** — Xác minh trực tiếp từ `kiotviet.vn`, `sapo.vn`, `haravan.com`, `posapp.vn`, `odoo.com` và Nghị định `123/2020/NĐ-CP`, `70/2025/NĐ-CP` ngày `2026-11-14`. |
| **2. Diễn giải (*Interpretations*)** | • **Rào cản chi phí mở rộng chuỗi (`Multi-store Cost Scaling`):** Với các chuỗi cửa hàng vừa và nhỏ (từ 3–10 điểm bán), mô hình tính phí theo từng chi nhánh/kho của các SaaS nội địa khiến chi phí phần mềm hàng năm tăng nhanh. Đây là lý do nhiều chuỗi tự xây hệ thống nội bộ hoặc dùng kiến trúc tương tự Odoo.<br>• **Tốc độ thao tác tại quầy là yếu tố sống còn của UX POS:** Khác với phần mềm quản lý nhà trọ (`QLNT` — giao dịch phát sinh theo chu kỳ hàng tháng nên phù hợp với ẩn dụ Sổ 3D lật trang), tại quầy thu ngân bán lẻ (`QLCH`), giao dịch diễn ra liên tục từng giây/phút. Giao diện bán hàng POS bắt buộc phải ưu tiên tốc độ quét mã/tìm hàng/thanh toán trong **1–3 chạm hoặc phím tắt**, không để hiệu ứng chuyển cảnh làm chậm thao tác thu ngân.<br>• **Kiểm soát chênh lệch tồn kho & bàn giao ca là "điểm đau" lớn nhất của chủ chuỗi:** Thất thoát tại cửa hàng thường xảy ra ở 3 khâu: (a) Hàng đang điều chuyển giữa các kho bị treo không rõ ai giữ, (b) Nhân viên sửa/hủy đơn hoặc thu tiền mặt không khớp két cuối ca, và (c) Kiểm kê kho phải dừng bán hàng lâu. | **Trung bình – Cao** — Rút ra từ cấu trúc tính năng, cách phân tầng gói cước và quy trình kiểm soát nội bộ của 5 phần mềm khảo sát. |
| **3. Giả thuyết cần kiểm chứng (*Hypotheses*)** | • **H-01:** Nếu `QLCH` áp dụng kiến trúc Web/PWA hỗ trợ lưu đệm cục bộ (`IndexedDB` + `Sync Queue`) tương tự Odoo POS kết hợp sinh mã VietQR động cục bộ và in bill qua trình duyệt (`K80/K57`), hệ thống có thể vận hành với chi phí hạ tầng `$0 First` mà vẫn đáp ứng trọn vẹn nhu cầu bán hàng tại quầy.<br>• **H-02:** Nếu Chủ dự án mong muốn có yếu tố trực quan 2D/3D cho `QLCH`, việc đặt chế độ trực quan ở **Sơ đồ mặt bằng chuỗi cửa hàng / Sơ đồ kệ kho (Visual Shelf/Store Map)** cho Chủ chuỗi/Thủ kho trong khi giữ **Màn hình POS 2D tốc độ cao** cho Thu ngân sẽ cân bằng được cả tính thẩm mỹ lẫn hiệu suất thực chiến.<br>• **H-03:** Quy trình kiểm kê kho hỗ trợ **"Kiểm kê từng phần theo nhóm/kệ hàng + Quét mã vạch cộng dồn"** sẽ giúp nhân viên cửa hàng kiểm kho ngay trong ca vắng khách mà không cần đóng cửa hàng. | **Cần kiểm chứng & chờ Chủ dự án xác nhận** tại Cổng Brief (`Q-QLCH-01` $\rightarrow$ `Q-QLCH-05`). |

---

## 5. Khuyến nghị Đầu vào cho BA, UX & Tech Lead (Phục vụ Cổng Brief `QLCH`)

1. **Dành cho `BA Lead` (Hỗ trợ làm rõ `Q-QLCH-01` & `Q-QLCH-02` tại [`02-nghiep-vu/REQUIREMENTS.md`](../../02-nghiep-vu/REQUIREMENTS.md)):**
   - Sử dụng ma trận đối sánh tại [`DANH_MUC_VA_MA_TRAN_PHAN_MEM_POS_CHUOI_BAN_LE_VN.md`](../3.Tai_lieu_nghiep_vu/DANH_MUC_VA_MA_TRAN_PHAN_MEM_POS_CHUOI_BAN_LE_VN.md) để gợi ý Chủ dự án chọn rõ kiểu đặc tính hàng hóa cho P1 MVP: **Hàng hóa tiêu chuẩn + Quy đổi ĐVT**, **Biến thể Màu/Size**, **Lô/Hạn sử dụng**, hay **Serial/IMEI** (vì mỗi kiểu làm thay đổi trực tiếp bảng dữ liệu `Product / Inventory`).
   - Chuẩn hóa ngay 4 quy trình chứng từ kho – bán hàng cốt lõi dựa trên [`BO_BIEU_MAU_HOA_DON_POS_VA_XUAT_NHAP_KIEM_KHO_VN.md`](../3.Tai_lieu_nghiep_vu/BO_BIEU_MAU_HOA_DON_POS_VA_XUAT_NHAP_KIEM_KHO_VN.md): (1) Hóa đơn POS & Đổi trả, (2) Bàn giao ca thu ngân, (3) Nhập - Xuất - Điều chuyển kho 2 bước, (4) Kiểm kê kho & Cân bằng tồn.
2. **Dành cho `UX Lead` (Hỗ trợ `QLCH-UX-01` / `#5` và `Q-QLCH-03`):**
   - Tham khảo bố cục màn hình POS chia 2 cột kinh điển (Cột trái: Giỏ hàng + Số lượng + Chiết khấu; Cột phải: Tìm kiếm/Quét mã + Lưới sản phẩm nhanh + Khung Thanh toán Tiền mặt/VietQR + Phím tắt `F1–F9`) và hỗ trợ **Đa tab đơn hàng (Hold Orders)**.
   - Tham khảo bố cục mẫu in nhiệt `K80 (80mm)` và `K57 (58mm)` tại tài liệu biểu mẫu để thiết kế giao diện Xem trước hóa đơn (*Print Preview*).
3. **Dành cho `Tech Lead` (Hỗ trợ `QLCH-TECH-01` / `#4` và `Q-QLCH-04`):**
   - Tham khảo mô hình **POS Session + Local IndexedDB Cache + Order Sync Queue** của Odoo POS cho bài toán Offline POS tại quầy thu ngân.
   - Lưu ý cơ chế **Trạng thái kho trung gian (`In-Transit Stock`)** khi thiết kế CSDL cho nghiệp vụ điều chuyển hàng hóa giữa các chi nhánh để không làm lệch tổng tồn kho toàn chuỗi.

---

## 6. Kế hoạch Khảo sát Thực địa Đề xuất (Chưa triển khai — Trình PM & Chủ dự án duyệt)

Tuân thủ Bước 1 & Bước 2 của `3.DOC_AI/skills/marketing-research/SKILL.md`, trường hợp Chủ dự án và PM cần thu thập thêm dữ liệu sơ cấp (*Primary Research*) từ người vận hành cửa hàng thực tế sau Cổng Brief, `Marketing Lead` đề xuất kế hoạch khung như sau:

| Nhóm đối tượng | Cỡ mẫu đề xuất | Phương pháp & Kênh | Bộ câu hỏi phỏng vấn mở đầu (Bán cấu trúc) |
| :--- | :---: | :--- | :--- |
| **1. Chủ chuỗi / Quản lý cửa hàng** (Đang vận hành từ 2–5 điểm bán) | `3 – 5` người | Phỏng vấn sâu 1-1 (30 phút/người) hoặc quan sát quy trình kiểm kho cuối tháng | • *"Khâu nào trong việc điều chuyển hàng giữa các cơ sở hoặc đối soát tiền mặt cuối ngày đang làm anh/chị mất nhiều thời gian nhất?"*<br>• *"Khi kiểm kho phát hiện lệch tồn, quy trình tìm nguyên nhân và xử lý chênh lệch hiện tại diễn ra như thế nào?"* |
| **2. Nhân viên thu ngân (Cashier)** | `5 – 8` người | Quan sát thao tác tại quầy giờ cao điểm & thử nghiệm nguyên mẫu (Usability Test) | • *"Lúc đông khách xếp hàng, thao tác nào trên màn hình bán hàng dễ bấm nhầm hoặc làm chậm việc in bill nhất?"*<br>• *"Khi khách muốn đổi hàng hoặc thanh toán một nửa tiền mặt, một nửa chuyển khoản QR, anh/chị xử lý thế nào?"* |
| **3. Nhân viên kho / Kiểm kê** | `3 – 5` người | Thử nghiệm luồng nhập hàng & kiểm kê trên thiết bị di động/máy quét | • *"Khi nhận hàng từ nhà cung cấp hoặc chi nhánh khác gửi sang, anh/chị kiểm đếm và đối chiếu với phiếu giao hàng bằng cách nào?"* |

> **Trạng thái kế hoạch khảo sát thực địa:** `Đề xuất — Chưa triển khai`. Không liên hệ người tham gia, không phát tán bảng hỏi và không thu thập dữ liệu cá nhân khi chưa có xác nhận của Chủ dự án và PM về phạm vi, địa bàn, cỡ mẫu và ngân sách (`$0`).

---

## 7. Danh mục Nguồn Trích dẫn & Tài liệu Liên kết (`2026-11-14`)

1. **KiotViet:** Trang Phí dịch vụ & Tính năng theo ngành hàng — [`https://www.kiotviet.vn/phi-dich-vu/`](https://www.kiotviet.vn/phi-dich-vu/) *(Truy cập: `2026-11-14`)*.
2. **Sapo POS / Sapo Omnichannel:**
   - Bảng giá giải pháp Sapo — [`https://www.sapo.vn/bang-gia.html`](https://www.sapo.vn/bang-gia.html) *(Truy cập: `2026-11-14`)*.
   - Phần mềm quản lý bán hàng cho shop bán lẻ — [`https://www.sapo.vn/phan-mem-quan-ly-ban-hang.html`](https://www.sapo.vn/phan-mem-quan-ly-ban-hang.html) *(Truy cập: `2026-11-14`)*.
3. **Haravan (HaraRetail / Haravan POS):**
   - Trang tính năng Haravan POS — [`https://www.haravan.com/pages/phan-mem-quan-ly-cua-hang-hararetail`](https://www.haravan.com/pages/phan-mem-quan-ly-cua-hang-hararetail) *(Truy cập: `2026-11-14`)*.
   - Bảng giá dịch vụ Haravan — [`https://www.haravan.com/pages/pricing`](https://www.haravan.com/pages/pricing) *(Truy cập: `2026-11-14`)*.
4. **PosApp:**
   - Trang chủ hệ sinh thái PosApp 2026 — [`https://posapp.vn/`](https://posapp.vn/) *(Truy cập: `2026-11-14`)*.
   - Báo giá phần mềm quản lý bán hàng F&B & Bán lẻ — [`https://posapp.vn/phi-dich-vu`](https://posapp.vn/phi-dich-vu) *(Truy cập: `2026-11-14`)*.
5. **Odoo POS:**
   - Phần mềm POS cho cửa hàng bán lẻ — [`https://www.odoo.com/vi_VN/app/point-of-sale-shop`](https://www.odoo.com/vi_VN/app/point-of-sale-shop) *(Truy cập: `2026-11-14`)*.
   - Bảng giá Odoo Việt Nam — [`https://www.odoo.com/vi_VN/pricing`](https://www.odoo.com/vi_VN/pricing) *(Truy cập: `2026-11-14`)*.
6. **Văn bản pháp quy về Hóa đơn & Chứng từ Kho tại Việt Nam:**
   - **Nghị định `123/2020/NĐ-CP`** và **Nghị định `70/2025/NĐ-CP`** (sửa đổi, bổ sung một số điều của Nghị định `123/2020/NĐ-CP` quy định về hóa đơn, chứng từ, hiệu lực từ `01/06/2025`) — Điều 11 quy định về Hóa đơn điện tử khởi tạo từ máy tính tiền.
   - **Thông tư `133/2016/TT-BTC`** và **Thông tư `200/2014/TT-BTC`** của Bộ Tài chính — Quy định hệ thống biểu mẫu chứng từ kế toán hàng tồn kho (`Mẫu số 01-VT: Phiếu nhập kho`, `Mẫu số 02-VT: Phiếu xuất kho`, `Mẫu số 05-VT: Biên bản kiểm kê vật tư, công cụ, sản phẩm, hàng hóa`).
