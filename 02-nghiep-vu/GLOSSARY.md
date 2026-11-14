# Thuật ngữ dự án — QLCH

> Bảng thuật ngữ chuẩn hóa cho dự án **Hệ thống Quản lý Chuỗi Cửa hàng, Kho bãi & Thương mại Điện tử Hợp nhất (`QLCH`)**, cập nhật theo Quyết định [`QLCH-D002`, `QLCH-D003`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/01-quan-ly/DECISIONS.md) ngày `2026-11-14`.

## 1. Thuật ngữ Mô hình Tổ chức & 04 Phân hệ Tách biệt (`QLCH-D003`)

| Thuật ngữ | Định nghĩa trong phạm vi dự án | Nguồn/người xác nhận | Ghi chú / Giai đoạn |
| :--- | :--- | :--- | :--- |
| **Hệ thống Chuỗi hợp nhất (`Single-owner Multi-branch & Multi-warehouse`)** | Mô hình tổ chức trong đó một chủ sở hữu duy nhất quản lý tập trung toàn bộ hệ thống thông qua **04 Phân hệ tách biệt** (`SYS-ADMIN`, `WMS`, `STORE & POS`, `ECOM`) dùng chung một Cơ sở dữ liệu lõi (`PostgreSQL`). | **Đã chốt** (`QLCH-D002`, `QLCH-D003` — Người dùng) | Không áp dụng mô hình thuê bao đa chủ `Multi-tenant SaaS` |
| **Phân hệ 1 — Quản trị Ứng dụng (`SYS-ADMIN — @qlch/admin-portal`)** | Phân hệ quản trị trung tâm dành cho Chủ hệ thống/Admin/Pháp chế: quản lý cơ cấu tổ chức (Kho/Cửa hàng/Kênh Online), phân quyền `RBAC` 4 phân hệ, xác thực 2 lớp (`PIN/OTP`), Danh mục dùng chung (`Master Data: SKU, Đa ĐVT, Giá trần`), **Hồ sơ 17 loại Giấy phép Pháp lý (`ANTT/PCCC/VLNCN/Pháo`)** và Nhật ký kiểm toán (`Audit Logs`). | **Đã chốt** (`QLCH-D003` — Người dùng) | Triển khai nền tảng ở `P1 MVP` (`#12`) |
| **Phân hệ 2 — Quản lý Kho bãi (`WMS — @qlch/wms-portal`)** | Phân hệ cốt lõi triển khai ở **Giai đoạn 1 (`P1 MVP`)**, quản lý Kho tổng (`Hub/DC`), Kho chuyên dụng (`VLNCN/Pháo`) & Kho cách ly (`Quarantine`), cấu trúc vị trí (`Zone/Rack/Bin`), sơ đồ kho 2D, khóa chặn trần `NEQ`, nhập/xuất/điều chuyển 2 bước `In-Transit`/kiểm kê mù, Thẻ kho bất biến và `Offline-first`. | **Đã chốt** (`QLCH-D002`, `QLCH-D003` — Người dùng) | Trọng tâm `P1 MVP` (`#13`) |
| **Phân hệ 3 — Quản lý Cửa hàng (`STORE & POS — @qlch/store-pos-portal`)** | Phân hệ độc lập dành cho Cửa hàng trưởng và Thu ngân: quản lý sơ đồ 2D quầy/kệ trưng bày & định mức an toàn tại điểm bán, nhận hàng điều chuyển từ `WMS`, Mở/Kết ca mù (`BM-POS-03`), bán hàng `POS < 15s/đơn` (`BM-POS-01`), định danh `CCCD 12 số` khi bán Pháo hoa `Z121`, bàn giao đơn `Click & Collect` và Đổi/Trả hàng (`BM-POS-02`). | **Đã chốt** (`QLCH-D002`, `QLCH-D003` — Người dùng) | Định khung ở `G1`, triển khai ở `P2` (`#14`) |
| **Phân hệ 4 — Cổng Thương mại Điện tử Online (`ECOM — @qlch/ecom-portal`)** | Phân hệ đặt hàng trực tuyến (`Storefront B2C` cho khách lẻ & `Portal B2B` cho doanh nghiệp): đồng bộ thời gian thực với `Tồn kho khả dụng (Available)`, áp dụng **Bộ lọc Pháp lý tự động** (ẩn hàng cấm dân sự `VLNCN` khỏi B2C, bắt buộc định danh `CCCD 12 số` & khóa giá trần khi đặt mua Pháo hoa `Z121`), thanh toán `VietQR cục bộ / COD`, xử lý đơn hàng Online (`Order Fulfillment`) và điều phối giao vận (`TMS`). | **Đã chốt** (`QLCH-D003` — Người dùng) | Định khung ở `G1`, triển khai ở `P2` (`#15`) |
| **Hệ thống Quản lý Vận chuyển (`TMS — Transportation Management`)** | Mô-đun điều phối đội xe/tài xế nội bộ và xe chuyên dụng Hàng nguy hiểm Loại 1 (`Biển UN`, kiểm định, Giấy phép vận chuyển `C06/PC07 <= 7 ngày`, kẹp chì `Seal No`), phục vụ cả luồng Điều chuyển liên kho (`WMS`) và Giao đơn hàng từ Cổng TMĐT Online (`ECOM`) kèm đối soát `COD` 100%. | **Đã chốt** (`QLCH-D002`, `QLCH-D003` — Người dùng) | Liên thông giữa `WMS` (`P1`) và `ECOM` (`P2`) |
| **Kho tổng / Trung tâm phân phối (`Hub / Distribution Center — DC`)** | Kho trung tâm có quy mô lớn, nơi tiếp nhận hàng hóa nhập từ Nhà cung cấp, lưu trữ số lượng lớn và phân phối/điều chuyển hàng hóa về các Kho chi nhánh hoặc Cửa hàng. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` |
| **Kho chi nhánh / Kho cửa hàng (`Branch / Store Warehouse`)** | Kho gắn liền với một chi nhánh hoặc điểm bán lẻ, nhận hàng điều chuyển từ Kho tổng (hoặc nhập trực tiếp) để phục vụ xuất bán tại quầy `POS` và giao đơn hàng Online (`ECOM`) trong khu vực. | **Đã chốt** (`QLCH-D002`, `QLCH-D003` — Người dùng) | `P1 MVP` & `P2` |

---

## 2. Thuật ngữ Hàng hóa & Cấu trúc Vị trí Kho (`P1 — WMS`)

| Thuật ngữ | Định nghĩa trong phạm vi dự án | Nguồn/người xác nhận | Ghi chú / Giai đoạn |
| :--- | :--- | :--- | :--- |
| **Mã hàng hóa (`SKU — Stock Keeping Unit`)** | Mã định danh duy nhất cho từng mặt hàng hoặc biến thể mặt hàng (phân biệt theo quy cách, màu sắc, kích cỡ...) dùng làm khóa chính để quản lý tồn kho, vị trí cất giữ và giá bán. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` |
| **Đơn vị tính cơ sở & Đa đơn vị tính (`Base UoM & Multi-UoM`)** | Mỗi `SKU` có một **Đơn vị tính cơ sở nhỏ nhất (`Base UoM`**, ví dụ: `Cái/Lon/Gói`) để lưu trữ tồn kho chuẩn trong cơ sở dữ liệu, và các **Đơn vị quy đổi** (ví dụ: `Lốc = 6 Lon`, `Thùng = 24 Lon`) phục vụ nhập/xuất linh hoạt. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` |
| **Lô hàng & Hạn sử dụng (`Batch/Lot & Expiry Date`)** | Mã định danh một đợt hàng nhập vào kho có cùng ngày sản xuất và hạn sử dụng (`HSD`), dùng để truy xuất nguồn gốc và áp dụng quy tắc xuất kho theo hạn dùng. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` |
| **Nguyên tắc xuất kho `FEFO` / `FIFO`** | - **`FEFO` (`First Expired, First Out`):** Ưu tiên gợi ý xuất lô hàng có **hạn sử dụng gần nhất** trước (áp dụng cho hàng có HSD).<br>- **`FIFO` (`First In, First Out`):** Ưu tiên gợi ý xuất lô hàng **nhập kho sớm nhất** trước (áp dụng cho hàng không có HSD). | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` |
| **Cấu trúc vị trí kho (`Zone -> Rack -> Bin`)** | Hệ thống phân cấp địa chỉ vật lý trong kho:<br>- **`Zone` (Khu vực):** Khu hàng khô, khu hàng mát, khu chờ nhập/xuất, khu hàng lỗi...<br>- **`Rack` (Dãy/Kệ):** Dãy kệ chứa hàng nằm trong một `Zone`.<br>- **`Bin` (Tầng/Ô chứa):** Ô vị trí nhỏ nhất trên kệ có gắn mã vạch riêng để cất (`Putaway`) và lấy hàng (`Picking`). | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` |
| **Sơ đồ trực quan 2D (`2D Interactive Layout`)** | Bản đồ mặt bằng 2D tương tác ngay trên Web App, hiển thị trực quan bố cục `Zone/Rack/Bin` trong kho (ở `P1`) và sơ đồ quầy cửa hàng/tuyến giao vận (ở `P2`), hỗ trợ tra cứu vị trí hàng, mật độ lấp đầy và cảnh báo màu sắc. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` (`WMS`) & `P2` (`POS/TMS`) |

---

## 3. Thuật ngữ Nghiệp vụ Vận hành Kho, Bán lẻ & Vận chuyển

| Thuật ngữ | Định nghĩa trong phạm vi dự án | Nguồn/người xác nhận | Ghi chú / Giai đoạn |
| :--- | :--- | :--- | :--- |
| **Cất hàng vào vị trí (`Putaway`)** | Thao tác phân bổ và xác nhận đưa hàng hóa vừa nhập từ khu vực tiếp nhận (`Receiving Dock`) vào đúng ô chứa (`Bin`) trên kệ kho thông qua quét mã vạch. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` |
| **Soạn hàng / Lấy hàng (`Picking & Packing`)** | Thao tác nhân viên kho đi theo lộ trình gợi ý trên thiết bị/sơ đồ 2D đến đúng `Bin` để lấy đúng `SKU`, đúng `Lô (FEFO/FIFO)` và đóng gói phục vụ phiếu xuất kho hoặc điều chuyển. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` |
| **Điều chuyển liên kho & Tồn đang đi đường (`Stock Transfer & In-Transit Inventory`)** | Quy trình chuyển hàng giữa hai kho (ví dụ: `Kho tổng -> Kho chi nhánh`). Khi kho xuất đã xác nhận xuất nhưng kho nhận chưa xác nhận nhập, lượng hàng đó được ghi nhận ở trạng thái **`Tồn đang đi đường (In-Transit)`** để không bị mất dấu tài sản. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` (nền tảng nối với `TMS` ở `P2`) |
| **Kiểm kê kho & Kiểm kê mù (`Stocktake / Cycle Count & Blind Count`)** | Quy trình đếm số lượng thực tế tại `Bin` bằng máy quét mã vạch để đối chiếu với tồn hệ thống. **Kiểm kê mù (`Blind Count`)** ẩn số tồn hệ thống trên màn hình nhân viên đếm để đảm bảo tính khách quan, chống gian lận. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` |
| **Tồn thực tế (`On-hand`) vs Tồn khả dụng (`Available`)** | - **`Tồn thực tế (On-hand)`:** Tổng số lượng vật lý đang nằm trong kho/ô chứa.<br>- **`Tồn giữ chỗ (Reserved/Allocated)`:** Số lượng đã được khóa cho các phiếu xuất/điều chuyển đang chờ lấy hàng.<br>- **`Tồn khả dụng (Available)` = `On-hand` $-$ `Reserved`:** Số lượng thực sự có thể xuất hoặc bán tiếp. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` |
| **Thẻ kho / Sổ cái tồn kho (`Stock Card / Inventory Ledger`)** | Bảng ghi nhận bất biến (`Append-only Audit Trail`) toàn bộ lịch sử giao dịch tăng/giảm của từng `SKU` theo thời gian, gắn chặt với mã chứng từ, vị trí `Bin`, số `Lô` và người thực hiện. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` |
| **Vận đơn & Đối soát thu hộ (`Shipment Order & COD Reconciliation`)** | Chứng từ giao nhận hàng hóa do đội xe vận chuyển (`TMS`) thực hiện kèm theo số tiền thu hộ tại điểm giao (`Cash on Delivery — COD`), bắt buộc đối soát khớp 100% khi tài xế kết thúc chuyến. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P2` (`TMS`) |

---

## 4. Thuật ngữ Hàng Đặc thù: Chất gây cháy nổ, Vật liệu nổ & Pháo (`REF-MKT-005`)

| Thuật ngữ | Định nghĩa trong phạm vi dự án | Nguồn/người xác nhận | Ghi chú / Giai đoạn |
| :--- | :--- | :--- | :--- |
| **Định mức Tồn chứa Thuốc nổ Quy đổi (`NEQ / NEW — Net Explosive Quantity`)** | Tổng khối lượng thuốc nổ/thuốc pháo thực tế quy đổi (tính bằng `kg` hoặc `tấn`) của toàn bộ sản phẩm đang lưu trữ trong một Kho hoặc Buồng kho (`Zone`). Hệ thống `WMS` bắt buộc khóa chặn nhập kho (`Hard Lock`) nếu tổng `NEQ` vượt định mức trên Giấy chứng nhận `ANTT/PCCC`. | **Đã chốt** (`REF-MKT-005` — `QCVN 01:2019/BCT`) | `P1 MVP` (`UC-WMS-01, 04`) |
| **Mã số Liên Hợp Quốc & Nhóm Nguy hiểm (`UN Number & Hazard Division`)** | Mã định danh quốc tế 4 chữ số (ví dụ: `UN 0336` cho Pháo hoa `1.4G`, `UN 1942` cho Amoni Nitrat) và phân nhóm nguy hiểm cháy nổ (Loại 1: Chất nổ; Loại 2, 3, 4: Khí/Lỏng/Rắn dễ cháy) theo Nghị định `34/2024/NĐ-CP`. | **Đã chốt** (`REF-MKT-005` — NĐ `34/2024/NĐ-CP`) | `P1 MVP` (`UC-WMS-02`) & `P2` (`TMS`) |
| **Phân khu Cách ly Hàng Kỵ nhau (`Incompatible Storage Separation`)** | Quy tắc bắt buộc trong `WMS` và `TMS`: Nghiêm cấm xếp chung hoặc chở chung **Kíp nổ / Phụ kiện nổ** với **Thuốc nổ**, hoặc **Tiền chất Amoni Nitrat ($NH_4NO_3$)** với dầu mỡ, axít, kim loại kiềm (`QCVN 01:2019/BCT`). | **Đã chốt** (`REF-MKT-005` — `QCVN 01:2019/BCT`) | `P1 MVP` (`UC-WMS-04`) & `P2` (`UC-TMS-02`) |
| **Pháo hoa Tiêu dùng (`Z121 Consumer Fireworks`) vs Pháo nổ** | **Pháo hoa tiêu dùng** (do Nhà máy `Z121` — Bộ Quốc phòng độc quyền sản xuất) chỉ tạo hiệu ứng ánh sáng/màu sắc/âm thanh không gây tiếng nổ, được phép bán lẻ dân sự kèm định danh **`CCCD 12 số`** người mua. **Pháo nổ / Pháo hoa nổ** gây tiếng nổ bị nghiêm cấm mua bán dân sự (Nghị định `137/2020/NĐ-CP`). | **Đã chốt** (`REF-MKT-005` — NĐ `137/2020/NĐ-CP`) | `P1 MVP` (`WMS`) & `P2` (`UC-POS-03`) |
| **Giấy phép Vận chuyển Hàng Nguy hiểm / Pháo hoa (`Transport Permit C06/PC07`)** | Giấy phép do Cục `C06` hoặc Phòng `C07/PC07` Công an cấp cho từng chuyến vận chuyển hàng cháy nổ/pháo hoa (thời hạn hiệu lực $\le 07\text{ ngày}$, bắt buộc nộp trả lại cơ quan Công an trong vòng `07 ngày` sau khi hoàn tất chuyến hàng). | **Đã chốt** (`REF-MKT-005` — NĐ `137/2020` & `34/2024`) | `P1 MVP` (`UC-WMS-03, 06`) & `P2` (`UC-TMS-02, 03`) |

---

Thuật ngữ riêng dự án ở đây không tự động trở thành tri thức dùng chung.
