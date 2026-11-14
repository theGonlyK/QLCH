# Tóm tắt dự án — QLCH

- **Sản phẩm/dự án:** `QLCH` — Quản lý hệ thống cửa hàng (Store / Retail Chain Management System)
- **Mục tiêu và vấn đề cần giải quyết:** Xây dựng hệ thống quản lý vận hành cửa hàng và chuỗi cửa hàng đồng bộ, chính xác, dễ sử dụng. *(Chi tiết bài toán trọng tâm theo ngành hàng và chỉ số thành công: `Cần xác nhận`)*
- **Người dùng/đối tượng sử dụng:** `Cần xác nhận` *(Dự kiến làm rõ: Chủ hệ thống/chuỗi cửa hàng, Quản lý cửa hàng/chi nhánh, Nhân viên thu ngân/bán hàng POS, Nhân viên kho/kiểm kê, Kế toán, Khách mua hàng)*
- **Thị trường đầu tiên:** `Cần xác nhận`
- **Chủ dự án:** Người dùng (chủ workspace, thẩm quyền phê duyệt cao nhất)
- **Người phụ trách mảng (giai đoạn Khởi tạo):**
  - **Điều phối chung:** `PM Dự án QLCH` (báo cáo `PM Workspace` — Codex PM vận hành)
  - **Mảng A (Thiết kế nghiệp vụ & trải nghiệm):** `BA Lead` (Gemini/Antigravity) đề xuất chuẩn hóa nghiệp vụ, phối hợp `UX Lead` và `Marketing Lead`; Người dùng phê duyệt.
  - **Mảng B (Xây dựng dự án):** `Tech Lead` và `QA Lead` đề xuất kiến trúc, công nghệ và khung kiểm thử (cùng `2D/3D Visual Lead` nếu có phạm vi đồ họa); Người dùng phê duyệt.
  - **Mảng C (Quản lý vận hành):** Agent phụ trách Hạ tầng/Vận hành phối hợp `Tech Lead` và `PM Lead`; Người dùng phê duyệt.
- **Đội ngũ đi kèm từng mảng:** Đội ngũ Subagent chuyên trách theo từng vai trò (chi tiết tại `01-quan-ly/DOI_NGU_AGENT_VA_CO_CHE_PHOI_HOP.md`)
- **Vòng đời/phạm vi đang thực hiện:** `Khởi tạo` — Thu thập yêu cầu đầu vào để trình duyệt **Cổng Brief**
- **Loại hình và môi trường triển khai:** `Cần xác nhận` *(Không tự suy đoán công nghệ/kiến trúc trước khi chốt loại hình Client Web/POS/Mobile và chế độ Offline/Online)*
- **Git repository:** `TEAM_ORCA/4.Du_an/QLCH` (nhánh `main`, remote `https://github.com/theGonlyK/QLCH`)
- **Ngày cập nhật:** `2026-11-14`

---

## Phạm vi

### Bao gồm
- Quản lý hệ thống cửa hàng (`QLCH`) — chi tiết các phân hệ P1 (Cửa hàng/Chi nhánh, Hàng hóa/Kho, Bán hàng POS/Đơn hàng, Nhân sự/Ca, Khách hàng, Báo cáo doanh thu/công nợ): `Cần xác nhận` tại `02-nghiep-vu/REQUIREMENTS.md`.

### Chưa bao gồm
- `Cần xác nhận` (Sẽ xác định rõ ranh giới Out-of-Scope của P1 ngay khi Chủ dự án chốt mục tiêu Cổng Brief).

---

## Thành công được xác định như thế nào

- `Cần xác nhận` (KPI vận hành, tốc độ lên đơn/kiểm kho, quy mô số cửa hàng/chi nhánh mục tiêu giai đoạn Pilot).

---

## Rủi ro, phụ thuộc và câu hỏi cần chốt

- **Câu hỏi cần chốt trước Cổng Brief:** Xem bảng câu hỏi chi tiết tại [`02-nghiep-vu/REQUIREMENTS.md`](file:///Users/uni/Documents/AI/AI-Workspace/AI-Workspace/TEAM_ORCA/4.Du_an/QLCH/02-nghiep-vu/REQUIREMENTS.md).
- **Rủi ro nghiệp vụ đặc thù ngành bán lẻ/chuỗi cửa hàng cần lưu ý khi thiết kế:**
  - Sai lệch tồn kho thực tế và tồn kho hệ thống khi bán hàng đa kênh hoặc điều chuyển giữa các chi nhánh.
  - Gián đoạn bán hàng tại quầy (POS) nếu mất kết nối mạng tại cửa hàng (cần làm rõ yêu cầu Offline-first tại quầy thu ngân).
  - Phân quyền chặt chẽ giữa Chủ chuỗi, Quản lý cửa hàng và Thu ngân (tránh gian lận hủy hóa đơn, sửa giá, hoàn trả hàng hoặc lộ dữ liệu giá vốn/lợi nhuận).
- **Phụ thuộc:**
  - Kết nối thiết bị phần cứng tại cửa hàng nếu có (máy quét mã vạch, máy in hóa đơn nhiệt, ngăn kéo đựng tiền) và phương thức thanh toán (tiền mặt, VietQR...).
