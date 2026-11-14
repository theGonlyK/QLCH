# Thuật ngữ dự án — QLCH

> Bảng thuật ngữ chuẩn hóa cho dự án **Hệ thống Quản lý Chuỗi Bán lẻ, Kho bãi & Vận chuyển (`QLCH`)**, cập nhật theo Quyết định [`QLCH-D002`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/01-quan-ly/DECISIONS.md) ngày `2026-11-14`.

## 1. Thuật ngữ Mô hình Tổ chức & Hệ sinh thái (`QLCH`)

| Thuật ngữ | Định nghĩa trong phạm vi dự án | Nguồn/người xác nhận | Ghi chú / Giai đoạn |
| :--- | :--- | :--- | :--- |
| **Hệ thống Chuỗi hợp nhất (`Single-owner Multi-branch & Multi-warehouse`)** | Mô hình tổ chức trong đó một chủ sở hữu duy nhất quản lý tập trung toàn bộ hệ thống Kho tổng (`Hub/DC`), các Kho chi nhánh, Cửa hàng bán lẻ (`POS`) và Đội xe vận chuyển nội bộ (`TMS`) trên cùng một nền tảng `QLCH`. | **Đã chốt** (`QLCH-D002` — Người dùng) | Không áp dụng mô hình thuê bao đa chủ `Multi-tenant SaaS` |
| **Hệ thống Quản lý Kho bãi (`WMS — Warehouse Management System`)** | Phân hệ cốt lõi triển khai ở **Giai đoạn 1 (`P1 MVP`)**, quản lý toàn diện danh mục hàng hóa, cấu trúc vị trí lưu trữ (`Zone/Rack/Bin`), sơ đồ kho 2D, nhập kho, xuất kho, điều chuyển liên kho, kiểm kê và đối soát tồn kho. | **Đã chốt** (`QLCH-D002` — Người dùng) | Trọng tâm `P1 MVP` |
| **Hệ thống Bán lẻ & Quầy thu ngân (`POS — Point of Sale`)** | Phân hệ triển khai ở **Giai đoạn 2 (`P2`)**, thực hiện quản lý cửa hàng/chi nhánh, ca thu ngân, tạo đơn bán lẻ tốc độ cao (`< 15s/đơn`), quét mã tính tiền, thanh toán Tiền mặt/VietQR cục bộ và in hóa đơn nhiệt. | **Đã chốt** (`QLCH-D002` — Người dùng) | Triển khai ở `P2`, trừ tồn kho trực tiếp từ Kho chi nhánh thuộc `WMS` |
| **Hệ thống Quản lý Vận chuyển (`TMS — Transportation Management System`)** | Phân hệ triển khai ở **Giai đoạn 2 (`P2`)**, quản lý đội xe/tài xế nội bộ, vận đơn, điều phối lộ trình giao hàng (`Kho tổng -> Cửa hàng` và `Kho/Cửa hàng -> Khách`), theo dõi trạng thái giao nhận và đối soát tiền thu hộ (`COD`). | **Đã chốt** (`QLCH-D002` — Người dùng) | Triển khai ở `P2`, kết nối với phiếu xuất/điều chuyển của `WMS` |
| **Kho tổng / Trung tâm phân phối (`Hub / Distribution Center — DC`)** | Kho trung tâm có quy mô lớn, nơi tiếp nhận hàng hóa nhập từ Nhà cung cấp, lưu trữ số lượng lớn và phân phối/điều chuyển hàng hóa về các Kho chi nhánh hoặc Cửa hàng. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` |
| **Kho chi nhánh / Kho cửa hàng (`Branch / Store Warehouse`)** | Kho gắn liền với một chi nhánh hoặc điểm bán lẻ, nhận hàng điều chuyển từ Kho tổng (hoặc nhập trực tiếp) để phục vụ xuất bán tại quầy `POS` và giao hàng cho khách trong khu vực. | **Đã chốt** (`QLCH-D002` — Người dùng) | `P1 MVP` |

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

Thuật ngữ riêng dự án ở đây không tự động trở thành tri thức dùng chung.
