# Hồ sơ Kỹ thuật và Môi trường (Tech Profile) — QLCH

> Trạng thái: **`Đề xuất Mảng B (Trình duyệt Cổng Brief / G1)`** — Đã cập nhật đầy đủ theo Quyết định Cổng Brief [`01-quan-ly/DECISIONS.md`](file:///Users/uni/Documents/AI/AI-Workspace/AI-Workspace/TEAM_ORCA/4.Du_an/QLCH/01-quan-ly/DECISIONS.md) (`QLCH-D002`), [`02-nghiep-vu/REQUIREMENTS.md`](file:///Users/uni/Documents/AI/AI-Workspace/AI-Workspace/TEAM_ORCA/4.Du_an/QLCH/02-nghiep-vu/REQUIREMENTS.md) và 16 Use Cases tại [`02-nghiep-vu/USE_CASES.md`](file:///Users/uni/Documents/AI/AI-Workspace/AI-Workspace/TEAM_ORCA/4.Du_an/QLCH/02-nghiep-vu/USE_CASES.md).
> Tài liệu Thiết kế Cơ sở dữ liệu & Cấu trúc bảng chi tiết (ERD, 7 nhóm bảng, 5 bất biến DB & Offline IndexedDB) được đặc tả tại: **[`03-ky-thuat/DATABASE_SCHEMA.md`](file:///Users/uni/Documents/AI/AI-Workspace/AI-Workspace/TEAM_ORCA/4.Du_an/QLCH/03-ky-thuat/DATABASE_SCHEMA.md)**.

---

## 1. Phân loại Kỹ thuật Đã Xác nhận (`QLCH-D002`)

- **Loại hình hệ thống:** Hệ thống Quản lý Hợp nhất **Kho bãi (`WMS` - P1 MVP) $\rightarrow$ Bán lẻ (`POS` - P2) & Vận chuyển (`TMS` - P2)** cho Đa ngành hàng tiêu dùng/bán lẻ và **Hàng đặc thù (Chất gây cháy nổ, Vật liệu nổ công nghiệp `VLNCN`, Pháo hoa `Z121`)**.
- **Mô hình tổ chức & dữ liệu:** **`Single-owner Multi-branch & Multi-warehouse`** (1 chủ sở hữu quản lý toàn chuỗi nhiều Kho tổng `Hub/DC`, Kho chuyên dụng `VLNCN/Pháo`, Kho cách ly `Quarantine` và Cửa hàng chi nhánh).
- **Client & Trải nghiệm:** **Web App tốc độ cao (PWA Responsive)** cho PC quản trị/kho, Tablet/Máy POS và Mobile Web tác nghiệp tại kệ kho, **kết hợp Sơ đồ trực quan 2D (`2D Interactive Warehouse Layout: Zone -> Rack -> Bin`)**.
- **Thiết bị ngoại vi hỗ trợ:** Máy quét mã vạch/QR cầm tay (`USB/Bluetooth HID Keyboard Emulation` & Camera thiết bị di động) và Máy in nhiệt (`Thermal Printer` khổ `K80/K57` & tem mã vạch `SKU/Bin`).
- **Chế độ vận hành mạng:** **`Offline-first`** — Nhân viên kho tác nghiệp `Putaway`, `Picking`, `Kiểm kê mù (Blind Count)` trong buồng kho chống nổ/góc khuất mất sóng (`UC-WMS-09`), lưu trên `IndexedDB` và tự động đồng bộ qua `offline_sync_queue`.
- **Ràng buộc hạ tầng & chi phí (`NFR-QLCH-03`):** **`$0 First`** và **`100% Thư viện cục bộ (Local Library-First)`** — Tuyệt đối không kết nối dịch vụ API bên thứ 3 trả phí khi chưa có phê duyệt của Chủ dự án trong `01-quan-ly/DECISIONS.md`.

---

## 2. Kiến trúc Giải pháp & Thành phần Công nghệ Đề xuất (`$0 First` & `Local Library-First`)

| Thành phần | Lựa chọn đề xuất (`100% Open-Source / Local Library`) | Lý do & Đánh đổi (Trade-offs) |
| :--- | :--- | :--- |
| **Frontend & PWA** | **TypeScript + React 18 / Vue 3 (Vite) + Tailwind CSS** | Khởi tạo tức thời, hỗ trợ Service Worker (PWA) để mở ứng dụng và quét mã vạch `< 1s` ngay cả khi mất mạng cục bộ trong kho sâu. |
| **Sơ đồ 2D Mặt bằng Kho (`FR-WMS-02`)** | **HTML5 Canvas 2D / SVG tương tác (`Konva.js` hoặc `Fabric.js` / Native SVG-Canvas)** | Thư viện 100% cục bộ (`$0`), nhẹ, hỗ trợ kéo-thả thiết kế layout `Zone -> Rack -> Bin`, phóng to/thu nhỏ (`Zoom/Pan`), tô màu cảnh báo tải trọng `% NEQ` và làm nổi bật vị trí kệ khi tìm `SKU`. |
| **CSDL Trung tâm (Server DB)** | **PostgreSQL 16+ + Drizzle ORM / Prisma** *(hỗ trợ chạy Docker cục bộ `$0`)* | Đảm bảo giao dịch **ACID tuyệt đối** cho Sổ cái Thẻ kho bất biến (`stock_ledger_entries`), tính giá vốn `MAC`, khóa chặn trần `NEQ` (`INV-DB-02`) và cách ly hàng kỵ nhau (`INV-DB-03`). Xem chi tiết tại [`03-ky-thuat/DATABASE_SCHEMA.md`](file:///Users/uni/Documents/AI/AI-Workspace/AI-Workspace/TEAM_ORCA/4.Du_an/QLCH/03-ky-thuat/DATABASE_SCHEMA.md). |
| **CSDL Cục bộ Ngoại tuyến (`Offline DB`)** | **IndexedDB (`Dexie.js`) + `offline_sync_queue`** | Lưu cache `SKU/Barcode`, sơ đồ `Bin` và hàng đợi sự kiện quét mã vạch ngoại tuyến kèm `idempotency_key` (`UC-WMS-09`). |
| **Backend API** | **Node.js (Fastify / NestJS) + TypeScript** | Hiệu năng cao, chia sẻ trọn vẹn kiểu dữ liệu (`Zod Schema / TypeScript Types`) giữa Backend, PostgreSQL và Frontend Offline Store. |
| **Quét & Sinh Mã vạch / QR / VietQR** | **HID Scanner Listener + `html5-qrcode` / `ZXing` (đọc camera) + `Bwip-js` / `JsBarcode` / `qrcode` (sinh mã cục bộ)** | 100% xử lý cục bộ trên trình duyệt/server nội bộ, không gọi bất kỳ API bên thứ 3 nào (`NFR-QLCH-01`, `NFR-QLCH-03`). |
| **In ấn Tem nhãn & Phiếu kho (`BM-KHO-01..04`)** | **CSS `@media print` chuẩn khổ nhiệt `K80/K57/A4` + `WebUSB / ESC-POS` cục bộ** | Cho phép in ngay Phiếu Nhập (`01-VT`), Phiếu Xuất (`02-VT`), Điều chuyển (`BM-KHO-03`), Biên bản Kiểm kê (`05-VT`) và tem mã vạch `SKU/Bin` ra máy in nhiệt/máy in văn phòng mà không tốn phí phần mềm trung gian. |
| **Xác thực & Phân quyền (`RBAC + 2FA PIN`)** | **JWT / Local Session + `Argon2/Bcrypt` + Mã PIN/TOTP nội bộ (`otplib`)** | Phân quyền chặt theo 6 Actor (`ACT-OWN`, `ACT-WM`, `ACT-WS`, `ACT-ACC`, `ACT-POS`, `ACT-TMS`) và bắt buộc xác thực 2 lớp (`PIN/TOTP` cục bộ) khi duyệt xuất `VLNCN`, xuất hủy hoặc cân bằng kiểm kê (`FR-WMS-09`). |

---

## 3. Liên kết Thiết kế Cơ sở Dữ liệu (`03-ky-thuat/DATABASE_SCHEMA.md`)

Toàn bộ cấu trúc Cơ sở dữ liệu của dự án `QLCH` đã được tách thành tài liệu kiến trúc chuyên biệt tại **[`03-ky-thuat/DATABASE_SCHEMA.md`](file:///Users/uni/Documents/AI/AI-Workspace/AI-Workspace/TEAM_ORCA/4.Du_an/QLCH/03-ky-thuat/DATABASE_SCHEMA.md)**, bao gồm:
1. **Sơ đồ Quan hệ Thực thể (`Mermaid ERD`)** kết nối xuyên suốt `P1 (WMS)` và `P2 (POS + TMS)`.
2. **Đặc tả 7 nhóm bảng cốt lõi**:
   - Nhóm 1: Đa Kho bãi & Sơ đồ 2D (`warehouses`, `warehouse_zones`, `warehouse_racks`, `warehouse_bins`, `users`, `roles`).
   - Nhóm 2: Hàng hóa, Đa ĐVT, Lô/Serial/HSD & Hàng Cháy nổ (`products`, `product_uoms`, `inventory_lots`).
   - Nhóm 3: Hồ sơ 17 loại Giấy phép Pháp lý (`compliance_licenses` với cảnh báo hạn `30-60 ngày` & khóa tự động khi hết hạn).
   - Nhóm 4: Tồn kho Đa trạng thái & Sổ cái Thẻ kho Bất biến (`inventory_balances` 3 cột phẩm chất, `stock_ledger_entries` Append-only).
   - Nhóm 5: Chứng từ Giao dịch Kho P1 (`wms_inbound_orders`, `wms_outbound_orders`, `wms_stock_transfers` 2 bước In-Transit, `wms_stocktakes` kiểm kê mù).
   - Nhóm 6: CSDL Cục bộ `Offline-first` (`IndexedDB / Dexie.js`: 5 Object Stores & `offline_sync_queue`).
   - Nhóm 7: Điểm nối Mở rộng P2 (`pos_shifts`, `pos_orders` có định danh CCCD 12 số khi mua Pháo Z121, `pos_returns`, `tms_vehicles`, `tms_shipments`).
3. **5 Bất biến Cơ sở dữ liệu (`INV-DB-01..05`)** và chiến lược đánh chỉ mục (`Indexing`) đảm bảo tốc độ quét mã vạch `< 1 giây`.
