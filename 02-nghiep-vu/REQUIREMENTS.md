# Yêu cầu và quy tắc nghiệp vụ — QLCH

> Trạng thái: `Khởi tạo` — Chưa có yêu cầu nghiệp vụ được xác nhận. Các mục dưới đây sẽ được `BA Lead` cập nhật ngay sau khi Chủ dự án phản hồi bảng câu hỏi Cổng Brief.

| ID | Yêu cầu/quy tắc | Nguồn | Ưu tiên | Trạng thái xác nhận | Người xác nhận | Tiêu chí chấp nhận |
|---|---|---|---|---|---|---|
| *(Chờ cập nhật)* | *(Sẽ điền sau khi Chủ dự án xác nhận phạm vi Cổng Brief)* | — | — | `Cần xác nhận` | Người dùng (Chủ dự án) | — |

---

## Câu hỏi cần làm rõ (Trình Chủ dự án để chốt Cổng Brief)

| Mã câu hỏi | Câu hỏi cần Chủ dự án xác nhận | Ảnh hưởng nếu chưa rõ | Người cần quyết định | Trạng thái |
| :---: | :--- | :--- | :--- | :---: |
| **Q-QLCH-01** | **Ngành hàng & Mô hình chuỗi cửa hàng mục tiêu là gì?**<br>*(Ví dụ: Bán lẻ tạp hóa/siêu thị mini, Thời trang/Phụ kiện, F&B/Cà phê, Điện máy/Linh kiện, hay Đa ngành? Hệ thống phục vụ 1 chủ sở hữu nhiều chi nhánh hay nền tảng SaaS cho nhiều chủ cửa hàng độc lập?)* | Quyết định cấu trúc dữ liệu hàng hóa (biến thể size/màu, hạn sử dụng, số serial/IMEI, định lượng nguyên vật liệu) và kiến trúc phân tách dữ liệu (`Multi-branch` vs `Multi-tenant SaaS`). | Người dùng (Chủ dự án) | `Chờ trả lời` |
| **Q-QLCH-02** | **Phạm vi các phân hệ cốt lõi cần có trong Giai đoạn 1 (P1 MVP) gồm những gì?**<br>*(Gợi ý lựa chọn: (1) Quản lý cửa hàng/chi nhánh & nhân viên/ca làm việc; (2) Quản lý sản phẩm, giá bán & tồn kho đa chi nhánh (nhập/xuất/điều chuyển/kiểm kê); (3) Bán hàng tại quầy POS & hóa đơn/thanh toán; (4) Quản lý khách hàng & tích điểm/khuyến mãi; (5) Quản lý nhà cung cấp & công nợ; (6) Báo cáo doanh thu - lãi lỗ)* | Xác định biên giới phạm vi P1 (In-scope / Out-of-scope) để BA lập BRD/SRS và PM chia Sprint hợp lý. | Người dùng (Chủ dự án) | `Chờ trả lời` |
| **Q-QLCH-03** | **Định hướng trải nghiệm & Loại hình thiết bị (Client) sử dụng chính?**<br>*(1) Giao diện chuẩn phần mềm quản lý/POS tốc độ cao hay có kết hợp mô phỏng không gian 2D/3D/Gamification như `QLNT`?<br>(2) Sử dụng trên Web trình duyệt, Máy POS/Tablet tại quầy, hay App Mobile cho chủ cửa hàng & nhân viên?* | Quyết định kích hoạt vai trò `2D/3D Artist`, thiết kế UX (`UX Lead`) và lựa chọn công nghệ Frontend/Mobile (`Tech Lead`). | Người dùng (Chủ dự án) | `Chờ trả lời` |
| **Q-QLCH-04** | **Yêu cầu về vận hành Offline tại quầy, Thiết bị ngoại vi & Nguyên tắc Hạ tầng/Thư viện?**<br>*(1) Quầy thu ngân có cần bán hàng Offline khi mất mạng không?<br>(2) Có kết nối máy quét mã vạch, máy in hóa đơn nhiệt không?<br>(3) Dự án `QLCH` có áp dụng nguyên tắc **`$0 First`** và **`100% Thư viện cục bộ / Chưa kết nối dịch vụ bên thứ 3 khi chưa có confirm của Chủ dự án`** (bao gồm sinh VietQR offline tại quầy) giống `QLNT` không?* | Quyết định kiến trúc lưu trữ (`IndexedDB` / Local DB sync), chuẩn kết nối phần cứng và ràng buộc kỹ thuật bắt buộc cho Dev. | Người dùng (Chủ dự án) | `Chờ trả lời` |
| **Q-QLCH-05** | **Thị trường mục tiêu đầu tiên và Chỉ số đánh giá thành công (KPI) của dự án là gì?** | Hoàn tất điều kiện bắt buộc của **Cổng Brief** trong `01-quan-ly/PROJECT_BRIEF.md`. | Người dùng (Chủ dự án) | `Chờ trả lời` |
