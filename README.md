# QLCH — Quản lý hệ thống cửa hàng

Trước khi dùng bộ khung này, đọc rule chuẩn tại `3.DOC_AI/quan-tri/RULES_CORE.md` và `3.DOC_AI/HANDOVER.md`. Trong lúc sử dụng dự án, đọc thêm handover riêng của dự án tại `HANDOVER.md`.

> Khởi tạo `2026-11-14` từ `3.DOC_AI/templates/du-an-base` theo quyết định `QLCH-D001`. Nhãn `Cần xác nhận` là thông tin chưa được Chủ dự án chốt — các Agent tuyệt đối không tự suy đoán.

## Hồ sơ nhanh

- **Mã dự án:** `QLCH`
- **Tên dự án:** Quản lý hệ thống cửa hàng (Store / Retail Chain Management System)
- **Mục tiêu sản phẩm:** Hệ thống quản lý vận hành cửa hàng và chuỗi cửa hàng (chi tiết ngành hàng, mô hình chuỗi/nhượng quyền, kênh bán hàng và chỉ số thành công: `Cần xác nhận`)
- **Chủ dự án / người quyết định:** Người dùng (chủ workspace, thẩm quyền phê duyệt cao nhất)
- **Người phụ trách mảng (giai đoạn Khởi tạo):**
  - **Điều phối dự án:** `PM Dự án QLCH` (báo cáo `PM Workspace` — Codex PM vận hành)
  - **Mảng A (Thiết kế nghiệp vụ & trải nghiệm):** `BA Lead` (Gemini/Antigravity) + `UX Lead` + phối hợp `Marketing Lead`
  - **Mảng B (Xây dựng dự án):** `Tech Lead`, `QA Lead`, `2D/3D Visual Lead` *(chỉ kích hoạt khi có phạm vi giao diện tương ứng)*
  - **Mảng C (Quản lý vận hành) & Tri thức:** `Vận hành/Hạ tầng` + `Knowledge Governance Lead`
- **Phạm vi vòng đời hiện tại:** `Khởi tạo` — Chuẩn bị hồ sơ và làm rõ yêu cầu cho **Cổng Brief**
- **Nhóm loại hình:** `Cần xác nhận` *(Web quản trị / POS Desktop-Tablet / Mobile App / Đa nền tảng)*
- **Môi trường triển khai:** `Cần xác nhận` *(Local / Cloud / Hybrid Offline-Online cho quầy POS)*
- **Repository Git:** `TEAM_ORCA/4.Du_an/QLCH` (Git riêng, nhánh `main`, remote `theGonlyK/QLCH`)
- **Quản lý Task & Sprint:** GitHub Issues trong `theGonlyK/QLCH` đồng bộ 100% với GitHub Project `QLCH` (`RULES_CORE.md` Mục 8 & Mục 10)
- **Trạng thái:** `Khởi tạo` — Đã thiết lập Git repo, bộ khung tài liệu và đội ngũ Agent chuyên trách; đang chờ Chủ dự án xác nhận thông tin đầu vào để chốt **Cổng Brief**.

## Cách dùng khung

- Bắt đầu với phần lõi trong `01-quan-ly` đến `04-van-hanh`.
- Chỉ hoàn thiện mức cần thiết cho phạm vi hiện tại; cập nhật dần qua mỗi vòng đời.
- Phần nào chưa cần thì đánh dấu `Chưa áp dụng` hoặc để trong backlog, không tạo tài liệu cho đủ hình thức.
- Các yêu cầu riêng, dữ liệu, quyết định, mã nguồn và cấu hình thuộc repository của dự án này (`theGonlyK/QLCH`).
- Chỉ đề xuất chuyển tri thức nghiệp vụ sang `3.DOC_AI` nếu có thể tái sử dụng ở dự án khác; cần nguồn, phạm vi và người xác minh.

## Hồ sơ dự án

- `HANDOVER.md`: điểm bắt đầu và trạng thái bàn giao nhanh của dự án `QLCH`.
- `01-quan-ly/PROJECT_BRIEF.md`: mục tiêu, phạm vi, vai trò, vòng đời và câu hỏi Cổng Brief.
- `01-quan-ly/DECISIONS.md`: sổ quyết định dự án (`QLCH-D001`...) và người chốt.
- `01-quan-ly/DOI_NGU_AGENT_VA_CO_CHE_PHOI_HOP.md`: danh sách đội ngũ Agent theo dõi dự án `QLCH`, phân quyền 3 mảng và quy tắc điều phối task.
- `02-nghiep-vu/REQUIREMENTS.md`: yêu cầu, quy tắc nghiệp vụ và danh sách câu hỏi cần Chủ dự án xác nhận.
- `02-nghiep-vu/GLOSSARY.md`: thuật ngữ nghiệp vụ trong phạm vi hệ thống cửa hàng.
- `03-ky-thuat/TECH_PROFILE.md`: kiến trúc, công nghệ, tích hợp và môi trường.
- `04-van-hanh/QUALITY_AND_RELEASE.md`: chất lượng, kiểm thử, phát hành và vận hành.
- `04-van-hanh/IMPROVEMENTS.md`: nhật ký cải tiến rút ra sau mỗi vòng đời/sprint.

## Vòng đời và cổng duyệt (`Thử nghiệm`)

Áp dụng mô hình 3 mảng và cổng **Brief**, **G1 (Yêu cầu sẵn sàng)**, **G3 (Sẵn sàng phát hành)** theo `3.DOC_AI/quan-tri/MO_HINH_VAN_HANH.md`. Ghi kết quả từng cổng vào `01-quan-ly/DECISIONS.md`.
