# Handover Dự án — Quản lý hệ thống cửa hàng (`QLCH`)

- **Mã dự án:** `QLCH`
- **Cập nhật gần nhất:** `2026-11-14`
- **Repository:** `theGonlyK/QLCH` (thư mục local: `TEAM_ORCA/4.Du_an/QLCH`, nhánh `main`)
- **Trạng thái vòng đời:** `Khởi tạo` (Chuẩn bị **Cổng Brief**)

---

## 1. Thứ tự đọc bắt buộc cho mọi Agent tham gia `QLCH` (`RULES_CORE.md` Mục 1)

1. `TEAM_ORCA/3.DOC_AI/quan-tri/RULES_CORE.md` (Nguồn chuẩn cao nhất về quy tắc bắt buộc toàn workspace).
2. `TEAM_ORCA/3.DOC_AI/HANDOVER.md` (Handover cấp workspace).
3. `TEAM_ORCA/4.Du_an/QLCH/HANDOVER.md` (Tài liệu này — ngữ cảnh riêng của dự án `QLCH`).
4. `01-quan-ly/DECISIONS.md` và `01-quan-ly/PROJECT_BRIEF.md` (Các quyết định đã chốt và phạm vi hiện tại của `QLCH`).
5. `01-quan-ly/DOI_NGU_AGENT_VA_CO_CHE_PHOI_HOP.md` (Phân công đội ngũ Agent chuyên trách dự án `QLCH`).
6. Skill chuyên môn tương ứng tại `TEAM_ORCA/3.DOC_AI/skills/<ten-skill>/SKILL.md`.

---

## 2. Tóm tắt hiện trạng dự án (`2026-11-14`)

- **Khởi tạo dự án (`QLCH-D001`):**
  - Đã tạo thư mục dự án độc lập tại `TEAM_ORCA/4.Du_an/QLCH` từ khung chuẩn `3.DOC_AI/templates/du-an-base/`.
  - Đã khởi tạo Git riêng (`main`) và kết nối với GitHub repository `theGonlyK/QLCH`.
  - Đã thiết lập bảng quản lý công việc **GitHub Project `QLCH`** đồng bộ 100% với Issues trong repo `theGonlyK/QLCH` (tuyệt đối không dùng `DraftIssue` trôi nổi theo `RULES_CORE.md` Mục 8).
- **Đội ngũ Agent theo dõi dự án (`01-quan-ly/DOI_NGU_AGENT_VA_CO_CHE_PHOI_HOP.md`):**
  - Đã cấu hình đầy đủ đội ngũ Agent chuyên trách theo mô hình 3 mảng (`A. Nghiệp vụ & UX`, `B. Xây dựng & QA`, `C. Vận hành & Hạ tầng`) cùng `PM Dự án QLCH` (`.claude/agents/pm-qlch.md`), `Marketing` và `Quản trị tri thức`.
  - Giữ ranh giới dữ liệu và Git hoàn toàn tách biệt với dự án `QLNT`.
- **Các hạng mục công việc giai đoạn Khởi tạo (Cổng Brief) trên `theGonlyK/QLCH`:**
  - `#1` (`[QLCH-INIT-01][PM]` — `Done / CLOSED`): Khởi tạo dự án `QLCH`, Git repo `theGonlyK/QLCH`, GitHub Project `QLCH` và đội ngũ Agent chuyên trách.
  - `#2` (`[QLCH-BA-01][BA][P0]` — `Todo / OPEN`): Làm rõ yêu cầu với Chủ dự án & hoàn thiện hồ sơ Cổng Brief (`PROJECT_BRIEF.md`, `REQUIREMENTS.md`, `GLOSSARY.md`).
  - `#3` (`[QLCH-MKT-01][Marketing]` — `Todo / OPEN`): Nghiên cứu thị trường phần mềm quản lý chuỗi cửa hàng/POS và thu thập bộ biểu mẫu nghiệp vụ bán lẻ.
  - `#4` (`[QLCH-TECH-01][Tech]` — `Todo / OPEN`): Đánh giá phương án kiến trúc kỹ thuật & lập `TECH_PROFILE.md` sau khi chốt phạm vi Brief.
  - `#5` (`[QLCH-UX-01][UX]` — `Todo / OPEN`): Phác thảo luồng trải nghiệm người dùng cốt lõi theo vai trò cửa hàng.
  - `#6` (`[QLCH-QA-01][QA]` — `Todo / OPEN`): Thiết lập khung kiểm thử, đối soát tồn kho/doanh thu và tiêu chuẩn chất lượng (`QUALITY_AND_RELEASE.md`).

---

## 3. Điểm đang chờ Chủ dự án xác nhận để qua Cổng Brief

Chi tiết câu hỏi nằm tại `02-nghiep-vu/REQUIREMENTS.md` (Mục *"Câu hỏi cần làm rõ"*), bao gồm:
1. **Ngành hàng & Mô hình chuỗi cửa hàng:** Bán lẻ tổng hợp/tạp hóa, thời trang, F&B, dược phẩm hay đa ngành? Mô hình 1 chủ nhiều chi nhánh hay nền tảng SaaS cho nhiều chủ thương hiệu?
2. **Phạm vi nghiệp vụ cốt lõi (P1 MVP):** Quản lý danh mục hàng hóa/SKU/mã vạch, Bán hàng tại quầy (POS) & in hóa đơn, Quản lý tồn kho đa chi nhánh (nhập - xuất - điều chuyển - kiểm kê), Quản lý nhân viên/ca làm việc, Quản lý khách hàng/tích điểm, hay Báo cáo tài chính/lãi lỗ?
3. **Loại hình Client & Định hướng trải nghiệm:** Web App, POS Desktop/Tablet, Mobile App? Giao diện chuẩn nghiệp vụ hiện đại (ERP/POS tốc độ cao) hay có kết hợp không gian trực quan 2D/3D/Gamification?
4. **Ràng buộc Hạ tầng, Chi phí & Thư viện:** Có áp dụng nguyên tắc **`$0 First`** và **`Local Library-First` (chưa kết nối bên thứ 3 khi chưa có confirm của Chủ dự án)** tương tự dự án `QLNT` hay không?
