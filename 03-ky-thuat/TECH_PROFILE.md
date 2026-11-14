# Hồ sơ kỹ thuật và môi trường — QLCH

> Trạng thái: `Khởi tạo` — Chờ kết quả xác nhận Cổng Brief (`Q-QLCH-01..Q-QLCH-05`) trước khi Mảng B (`Tech Lead`) đề xuất kiến trúc và công nghệ. Tuyệt đối không suy đoán công nghệ chỉ từ nhãn sản phẩm (`RULES_CORE.md` Mục 7).

## Phân loại cần xác nhận

- **Loại hình:** `Cần xác nhận` *(Web / Web-app / POS Application / Mobile App)*
- **Client:** `Cần xác nhận` *(Web browser / Desktop POS / Tablet / Mobile / Thiết bị ngoại vi máy in bill, máy quét mã vạch)*
- **Môi trường:** `Cần xác nhận` *(Local / Development / Staging / Production)*
- **Mô hình triển khai:** `Cần xác nhận` *(Single-tenant Multi-branch hay Multi-tenant SaaS; Offline-first POS hay Online)*
- **Người dùng và quy mô dự kiến:** `Cần xác nhận`

## Thành phần kỹ thuật

- Kiến trúc tổng quan: `Cần xác nhận`
- Ngôn ngữ/framework: `Cần xác nhận`
- Lưu trữ và dữ liệu: `Cần xác nhận`
- Tích hợp/API: `Cần xác nhận`
- Xác thực và phân quyền: `Cần xác nhận`
- Logging/monitoring: `Cần xác nhận`
- Sao lưu/khôi phục: `Cần xác nhận`
- Ràng buộc hạ tầng/chi phí: `Cần xác nhận` *(Làm rõ việc áp dụng nguyên tắc `$0 First` và `Local Library-First / Chưa kết nối bên thứ 3` theo `Q-QLCH-04`)*

## Quyết định cần chốt

Không chọn công nghệ hay kiến trúc chỉ dựa trên loại hình sản phẩm. Ghi phương án, đánh đổi và người quyết định trong `../01-quan-ly/DECISIONS.md`.
