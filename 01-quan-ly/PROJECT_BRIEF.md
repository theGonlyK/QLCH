# Tóm tắt dự án — QLCH

- **Sản phẩm/dự án:** `QLCH` — Hệ thống Quản lý Chuỗi Cửa hàng, Kho bãi & Thương mại Điện tử Hợp nhất (`4 Phân hệ Tách biệt: Quản trị ứng dụng - Quản lý kho bãi - Quản lý cửa hàng - Cổng TMĐT Online`)
- **Mục tiêu và vấn đề cần giải quyết:**
  - Xây dựng hệ thống quản lý vận hành hợp nhất cho chuỗi cửa hàng đa ngành hàng tiêu dùng/bán lẻ (bao gồm cả **Hàng đặc thù: Chất gây cháy nổ, Vật liệu nổ công nghiệp `VLNCN`, Pháo hoa `Z121`**) theo mô hình **1 chủ sở hữu quản lý toàn chuỗi (`Single-owner Multi-branch & Multi-warehouse`)**.
  - **Cấu trúc 04 Phân hệ tách biệt rõ ràng (`QLCH-D003`):**
    1. **Phân hệ 1 — Quản trị Ứng dụng (`SYS-ADMIN`):** Quản trị cấu hình toàn chuỗi, cơ cấu tổ chức, phân quyền `RBAC` 4 phân hệ + xác thực 2 lớp (`PIN/OTP`), danh mục dùng chung (`Master Data: SKU, Đa ĐVT, Giá trần`), **Hồ sơ 17 loại Giấy phép Pháp lý (`ANTT/PCCC/VLNCN/Pháo`)** & Nhật ký Kiểm toán (`Audit Logs`).
    2. **Phân hệ 2 — Quản lý Kho bãi (`WMS`):** Quản lý Kho tổng (`Hub/DC`), Kho chuyên dụng & Kho cách ly; Sơ đồ 2D mặt bằng kho (`Zone/Rack/Bin`); Khóa chặn trần thuốc nổ quy đổi (`NEQ Hard-Lock`) & cách ly hàng kỵ nhau; Nhập kho, Xuất kho, Điều chuyển liên kho 2 bước (`In-Transit`), Kiểm kê mù bằng mã vạch, Thẻ kho bất biến & Tác nghiệp kho `Offline-first`.
    3. **Phân hệ 3 — Quản lý Cửa hàng (`STORE & POS`):** Quản lý vận hành tại điểm bán vật lý, Sơ đồ 2D quầy/kệ cửa hàng, nhận hàng điều chuyển từ kho, Mở/Kết ca mù, Bán hàng tại quầy `POS < 15s`, Bán hàng đặc thù tại quầy (định danh `CCCD 12 số` Pháo hoa `Z121`), và Đổi/Trả hàng.
    4. **Phân hệ 4 — Cổng Thương mại Điện tử Online (`ECOM`):** Cổng trưng bày & đặt hàng trực tuyến (`Storefront B2C` & `Portal B2B`) đồng bộ tồn kho khả dụng (`Available`) thời gian thực, kiểm soát tuân thủ pháp lý hàng đặc thù khi đặt hàng Online, thanh toán `VietQR cục bộ / COD`, và luồng xử lý đơn hàng Online (`Order Fulfillment` đẩy xuống `WMS`/`Cửa hàng` & giao vận `TMS`).
  - **Chiến lược phân kỳ triển khai (`QLCH-D002` & `QLCH-D003`):**
    - **Giai đoạn 1 (`P1 MVP` — Trọng tâm hiện tại):** Triển khai **Phân hệ 1 (`Quản trị Ứng dụng` nền tảng)** và **Phân hệ 2 (`Quản lý Kho bãi - WMS`)** kết hợp Sơ đồ 2D `Zone/Rack/Bin`, thiết bị mã vạch/in nhiệt và `Offline-first`.
    - **Giai đoạn 2 (`P2` — Mở rộng khép kín chuỗi Đa kênh `Omnichannel`):** Triển khai **Phân hệ 3 (`Quản lý Cửa hàng - STORE & POS`)** và **Phân hệ 4 (`Cổng Thương mại Điện tử Online - ECOM` & Giao vận `TMS`)** đấu nối trực tiếp trên nền dữ liệu tồn kho và phân quyền chuẩn của `P1`.
- **Thị trường đầu tiên:** Thị trường Việt Nam (áp dụng cho mô hình doanh nghiệp/chuỗi cửa hàng bán lẻ & phân phối đa kho bãi, đa chi nhánh).
- **Chủ dự án:** Người dùng (chủ workspace, thẩm quyền phê duyệt cao nhất)
- **Người phụ trách mảng (giai đoạn Khởi tạo & Chuẩn bị G1):**
  - **Điều phối chung:** `PM Dự án QLCH` (báo cáo `PM Workspace` — Codex PM vận hành)
  - **Mảng A (Thiết kế nghiệp vụ & trải nghiệm):** `BA Lead` (Gemini/Antigravity) chuẩn hóa nghiệp vụ `WMS/POS/TMS`, phối hợp `UX Lead` và `Marketing Lead`; Người dùng phê duyệt.
  - **Mảng B (Xây dựng dự án):** `Tech Lead` và `QA Lead` thiết kế kiến trúc Web App Offline-first, Local-first, tích hợp thiết bị mã vạch/in nhiệt và khung kiểm thử `X02` (cùng `2D Visual Artist` đã được kích hoạt để thiết kế sơ đồ 2D mặt bằng kho/kệ hàng/cửa hàng); Người dùng phê duyệt.
  - **Mảng C (Quản lý vận hành):** Agent phụ trách Hạ tầng/Vận hành phối hợp `Tech Lead` và `PM Lead`; Người dùng phê duyệt.
- **Đội ngũ đi kèm từng mảng:** Đội ngũ Subagent chuyên trách theo từng vai trò (chi tiết tại [`01-quan-ly/DOI_NGU_AGENT_VA_CO_CHE_PHOI_HOP.md`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/01-quan-ly/DOI_NGU_AGENT_VA_CO_CHE_PHOI_HOP.md))
- **Vòng đời/phạm vi đang thực hiện:** `Hoàn tất hồ sơ Cổng Brief` $\rightarrow$ Sẵn sàng trình duyệt **Cổng Brief** để chuyển sang giai đoạn **Phân tích & Thiết kế (`G1`) cho P1 (`WMS`)**
- **Loại hình và môi trường triển khai:**
  - **Client:** **Web App tốc độ cao** (Responsive trên PC quản trị/văn phòng kho, Tablet và Mobile Web cầm tay cho nhân viên tác nghiệp tại kệ kho/quầy/xe giao hàng) **kết hợp Sơ đồ trực quan 2D (`2D Interactive Layout`)**.
  - **Chế độ vận hành:** **Offline-first** (cho phép quét mã, nhập/xuất/kiểm kê kho tại vùng sóng yếu ở P1 và bán hàng POS/giao vận ở P2; tự động đồng bộ khi có mạng lại).
  - **Nguyên tắc Hạ tầng & Chi phí bắt buộc (`QLCH-D002`):** Áp dụng nghiêm ngặt **`$0 First`** và **`100% Thư viện cục bộ (Local Library-First)`** — tuyệt đối chưa kết nối API dịch vụ bên thứ 3 trả phí (bản đồ thương mại, cổng thanh toán, hãng vận chuyển ngoài) khi chưa có xác nhận của Chủ dự án.
- **Git repository:** `TEAM_ORCA/4.Du_an/QLCH` (nhánh `main`, remote `https://github.com/theGonlyK/QLCH`)
- **Ngày cập nhật:** `2026-11-14`

---

## Phạm vi

### Bao gồm trong Giai đoạn 1 (`P1 MVP` — Hệ thống Quản lý Kho bãi `WMS`)
1. **Quản lý Hệ thống Kho bãi đa cấp & Sơ đồ trực quan 2D (`Multi-warehouse & 2D Layout`):**
   - Quản lý Kho tổng (`Hub / Distribution Center - DC`) và các Kho chi nhánh/cửa hàng (`Branch Warehouse`).
   - Cấu hình cấu trúc vị trí lưu trữ phân cấp: Khu vực (`Zone`) $\rightarrow$ Dãy/Kệ (`Aisle/Rack`) $\rightarrow$ Tầng/Ô chứa (`Shelf/Bin`).
   - **Sơ đồ trực quan 2D mặt bằng kho (`2D Warehouse Map`):** Hiển thị trực quan bố cục khu vực/kệ/bin, mật độ lấp đầy, tra cứu nhanh vị trí mặt hàng trên sơ đồ 2D và cảnh báo trực quan các ô chứa có hàng sắp hết hạn/dưới định mức.
2. **Quản lý Danh mục Hàng hóa đa ngành (`Product & SKU Master`):**
   - Quản lý danh mục ngành hàng, nhóm hàng, thương hiệu, sản phẩm và biến thể (`SKU`).
   - Hỗ trợ mã vạch/QR (`Barcode/QR Code`), quy đổi đa đơn vị tính (`UoM` — ví dụ: Thùng $\leftrightarrow$ Hộp $\leftrightarrow$ Cái) và quản lý theo **Lô & Hạn sử dụng (`Batch/Lot & Expiry Date - FEFO/FIFO`)**.
3. **Nghiệp vụ Vận hành Kho cốt lõi (`Inbound - Outbound - Transfer - Stocktake`):**
   - **Nhập kho (`Inbound`):** Nhập hàng từ Nhà cung cấp (`Purchase Receipt`), nhập hàng hoàn trả/nội bộ, gán vị trí cất hàng (`Putaway` vào `Bin`) và in tem nhãn mã vạch/QR.
   - **Xuất kho (`Outbound`):** Xuất bán/xuất cấp phát nội bộ, gợi ý lấy hàng theo nguyên tắc `FEFO/FIFO` và vị trí `Bin` (`Picking & Packing`), in phiếu xuất kho.
   - **Điều chuyển liên kho (`Stock Transfer`):** Lập lệnh điều chuyển giữa Kho tổng (`Hub/DC`) và Kho chi nhánh (`2 bước`: Xuất điều chuyển $\rightarrow$ Hàng đang đi đường `In-Transit` $\rightarrow$ Nhập nhận điều chuyển), đối soát chênh lệch khi nhận.
   - **Kiểm kê kho (`Stocktake / Cycle Count`):** Kiểm kê toàn bộ hoặc kiểm kê từng khu vực/kệ/nhóm hàng bằng thiết bị quét mã vạch (hỗ trợ kiểm kê mù `Blind Count`), tự động tính chênh lệch và tạo phiếu điều chỉnh tồn kho sau khi phê duyệt.
4. **Cảnh báo & Báo cáo Kho bãi (`Inventory Alerts & Analytics`):**
   - Cảnh báo tồn kho tối thiểu/tối đa (`Min/Max Stock Alert`), cảnh báo lô hàng sắp hết hạn (`Near-Expiry Alert`).
   - Báo cáo Thẻ kho (`Stock Card`), Báo cáo Nhập - Xuất - Tồn (`NXT`) theo kho/vị trí/lô, và Lịch sử truy vết mọi biến động tồn kho (`100% Audit Trail`).
5. **Hỗ trợ Thiết bị ngoại vi, Offline-first & Phân quyền RBAC:**
   - Tích hợp máy quét mã vạch/QR (`HID/Camera`) và máy in nhiệt (`Thermal Printer` in tem nhãn `SKU/Bin` & phiếu kho).
   - Lưu trữ cục bộ (`Offline-first`) cho các tác vụ kiểm kê/nhập/xuất tại điểm mù sóng Wi-Fi trong kho và đồng bộ an toàn khi có kết nối.
   - Phân quyền theo vai trò (`Chủ chuỗi`, `Quản lý kho`, `Nhân viên kho`, `Kế toán kho`) và phạm vi kho được giao.

### Lộ trình Giai đoạn 2 (`P2` — Chưa triển khai trong P1, định hình sẵn kiến trúc chờ đấu nối)
- **Hệ thống Bán lẻ (`POS & Chuỗi cửa hàng`):** Quản lý chi nhánh cửa hàng, sơ đồ 2D quầy kệ cửa hàng, ca thu ngân, bán hàng tại quầy POS tốc độ cao (`< 15s/đơn`), thanh toán Tiền mặt/VietQR cục bộ, in hóa đơn nhiệt và quản lý khách hàng.
- **Hệ thống Vận chuyển (`TMS & Đội xe nội bộ`):** Quản lý đội xe/tài xế, lập chuyến & điều phối lộ trình giao hàng 2D (`Kho tổng -> Cửa hàng` và `Kho/Cửa hàng -> Khách`), theo dõi trạng thái vận đơn, xác nhận giao hàng (`POD`) và đối soát tiền thu hộ (`COD`).
- **Báo cáo & Đối soát hợp nhất toàn chuỗi (`POS + WMS + TMS`):** Doanh thu bán lẻ, giá trị tồn kho toàn chuỗi, chi phí vận chuyển và đối soát dòng tiền/COD.

### Chưa bao gồm (Out-of-Scope trong P1)
- Chưa phát triển mô-đun Bán hàng tại quầy (`POS`) và Vận chuyển/Đội xe (`TMS`) trong `P1` (đưa vào `P2` theo `QLCH-D002`).
- Chưa làm mô hình `Multi-tenant SaaS` cho thuê đa chủ thương hiệu độc lập (tập trung mô hình `1 chủ sở hữu quản lý toàn chuỗi`).
- Chưa làm mô phỏng không gian 3D hoặc Gamification (chỉ làm **Sơ đồ trực quan 2D** phục vụ nghiệp vụ).
- Chưa kết nối API trả phí hoặc dịch vụ bên thứ 3 (Google Maps trả phí, cổng thanh toán tự động, hãng vận chuyển GHN/GHTK/ViettelPost, hóa đơn điện tử thuế) khi chưa có xác nhận của Chủ dự án.

---

## Thành công được xác định như thế nào (KPIs — `QLCH-D002`)

### 1. Chỉ số thành công Giai đoạn 1 (`P1 MVP — Hệ thống Kho bãi WMS`)
- **Độ chính xác tồn kho (`Inventory Accuracy`):** Khớp **100%** giữa tồn kho hệ thống và phép tính cộng/trừ lũy kế từ các phiếu Nhập - Xuất - Điều chuyển - Kiểm kê theo từng `Kho`, `Vị trí kệ/Bin` và `Lô/Hạn sử dụng`.
- **Tốc độ tác nghiệp tại kho:** Quét mã vạch tra cứu sản phẩm/vị trí `Bin` hoặc ghi nhận 1 lượt đếm kiểm kê **$< 1$ giây/thao tác**; hoàn tất tạo và in phiếu nhập/xuất/tem mã vạch nhanh chóng trên Web App.
- **Khả năng vận hành liên tục (`Offline-first`):** Nhân viên kho thực hiện kiểm kê, soạn hàng tại khu vực mất mạng cục bộ không bị gián đoạn; đồng bộ chính xác 100% khi có mạng lại, có cơ chế phát hiện xung đột dữ liệu.
- **Truy vết & Kiểm soát nội bộ (`Auditability`):** **100%** biến động số lượng tồn kho đều phải gắn với chứng từ hợp lệ (Phiếu nhập, Phiếu xuất, Phiếu điều chuyển, Biên bản kiểm kê) kèm người thực hiện và thời gian.

### 2. Chỉ số thành công Toàn trình (khi hoàn tất `P2 — WMS + POS + TMS`)
- Khép kín hoàn toàn luồng: **Nhập kho (`WMS`) $\rightarrow$ Điều chuyển/Vận chuyển (`TMS`) $\rightarrow$ Bán lẻ tại quầy/Giao khách (`POS`)**.
- Khớp tồn kho toàn chuỗi và đối soát tiền mặt / thu hộ `COD` chính xác **100%**.
- Tốc độ thao tác lên đơn tại quầy `POS` **$< 15$ giây/đơn**.

---

## Rủi ro, phụ thuộc và câu hỏi cần chốt

- **Trạng thái câu hỏi Cổng Brief (`Q-QLCH-01..Q-QLCH-05`):** **Đã chốt 100%** với Chủ dự án tại Quyết định [`QLCH-D002`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/01-quan-ly/DECISIONS.md) và [`02-nghiep-vu/REQUIREMENTS.md`](file:///Users/uni/orca/workspaces/QLCH/c-ng-brief-qlch-ba-01-ba-p0-ch-n-ng-g-ng-l-m-r-y/02-nghiep-vu/REQUIREMENTS.md).
- **Rủi ro nghiệp vụ & kỹ thuật cần kiểm soát ở giai đoạn thiết kế (`G1`):**
  1. **Xung đột tồn kho khi đồng bộ Offline (`Offline Sync Conflict`):** Khi nhiều nhân viên kho cùng xuất/kiểm kê một `SKU/Bin` trong lúc mất mạng, cần quy tắc đồng bộ theo sự kiện biến động (`Delta/Event Log`) và cảnh báo duyệt thay vì ghi đè số tuyệt đối.
  2. **Sai lệch quy đổi đa đơn vị tính (`Multi-UoM`) và Lô/Hạn sử dụng (`Batch/FEFO`):** Cần quy định rõ đơn vị tính cơ sở nhỏ nhất (`Base UoM`) để lưu trữ tồn kho chuẩn, tránh sai số làm tròn khi quy đổi Thùng $\leftrightarrow$ Hộp $\leftrightarrow$ Lẻ.
  3. **Khả năng mở rộng sang `P2` (`POS` & `TMS`):** Cấu trúc dữ liệu `Kho bãi`, `Chứng từ xuất/nhập` và `Hàng đang đi đường (In-Transit)` ở `P1` phải được thiết kế mở để `P2` gắn trực tiếp `Đơn hàng POS` và `Vận đơn TMS` mà không phải đập đi xây lại Database.
- **Phụ thuộc:**
  - Thiết kế chuẩn giao tiếp Web với máy quét mã vạch (`Keyboard Emulation / WebHID / Camera`) và mẫu in nhiệt (`CSS Print / ESC-POS cục bộ`) tuân thủ nguyên tắc `Local Library-First`.
