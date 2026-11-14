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
  - `#2` (`[QLCH-BA-01][BA][P0]` — `Done / CLOSED`): Đã làm rõ và ghi nhận đầy đủ `Q-QLCH-01..Q-QLCH-05` từ Chủ dự án vào `DECISIONS.md` (`QLCH-D002`), chuẩn hóa hoàn chỉnh `PROJECT_BRIEF.md`, `REQUIREMENTS.md` và `GLOSSARY.md` sẵn sàng qua **Cổng Brief**.
  - `#3` (`[QLCH-MKT-01][Marketing]` — `Done / CLOSED`): Đã hoàn thành khảo sát thị trường 5 phần mềm quản lý cửa hàng/POS (`KiotViet`, `Sapo POS`, `Haravan HaraRetail`, `PosApp`, `Odoo POS`) và tuyển chọn bộ 07 biểu mẫu hóa đơn POS, bàn giao ca, nhập/xuất/điều chuyển/kiểm kê kho chuẩn Việt Nam (`2.Tai_lieu_tham_khao/5.Tai_lieu_marketing/BAO_CAO_KHAO_SAT_PHAN_MEM_POS_VA_CHUOI_CUA_HANG_VN.md`, `2.Tai_lieu_tham_khao/3.Tai_lieu_nghiep_vu/DANH_MUC_VA_MA_TRAN_PHAN_MEM_POS_CHUOI_BAN_LE_VN.md`, `2.Tai_lieu_tham_khao/3.Tai_lieu_nghiep_vu/BO_BIEU_MAU_HOA_DON_POS_VA_XUAT_NHAP_KIEM_KHO_VN.md`, `02-nghiep-vu/NGHIEN_CUU_THI_TRUONG_VA_BIEU_MAU_THAM_KHAO.md`, `SO_DANG_KY_TRI_THUC.md`).
  - `#4` (`[QLCH-TECH-01][Tech]` — `Todo / OPEN` — **Đã mở khóa đầu vào từ `#2`**): Đánh giá phương án kiến trúc kỹ thuật & lập `TECH_PROFILE.md` theo phạm vi Brief đã chốt (`P1: WMS + Sơ đồ 2D + Offline-first + $0/Local-first`; `P2: POS + TMS`).
  - `#5` (`[QLCH-UX-01][UX]` — `Todo / OPEN` — **Đã mở khóa đầu vào từ `#2`**): Phác thảo luồng trải nghiệm người dùng cốt lõi & sơ đồ trực quan 2D kho bãi (`P1 WMS`) / cửa hàng & giao vận (`P2`).
  - `#6` (`[QLCH-QA-01][QA]` — `Todo / OPEN` — **Đã mở khóa đầu vào từ `#2`**): Thiết lập khung kiểm thử, đối soát tồn kho/doanh thu và tiêu chuẩn chất lượng (`QUALITY_AND_RELEASE.md`).

---

## 3. Tóm tắt Quyết định Cổng Brief đã chốt (`QLCH-D002` — `2026-11-14`)

Chủ dự án đã xác nhận toàn bộ 5 câu hỏi `Q-QLCH-01..Q-QLCH-05` (chi tiết tại `01-quan-ly/DECISIONS.md`, `01-quan-ly/PROJECT_BRIEF.md` và `02-nghiep-vu/REQUIREMENTS.md`):
1. **Mô hình hệ sinh thái & Sở hữu (`Q-QLCH-01`):** Quản lý hợp nhất **Bán lẻ (`POS`) - Kho bãi (`WMS`) - Vận chuyển (`TMS`)** cho **Đa ngành hàng tiêu dùng/bán lẻ** (SKU, mã vạch, đa đơn vị tính, lô/HSD) theo mô hình **1 chủ sở hữu quản lý toàn chuỗi (`Single-owner Multi-branch & Multi-warehouse`)**.
2. **Chiến lược phân kỳ P1 & P2 (`Q-QLCH-02`):**
   - **Giai đoạn 1 (`P1 MVP` — Trọng tâm hiện tại):** Chỉ làm trước **Hệ thống Quản lý Kho bãi (`WMS`)** (Kho tổng `Hub/DC` & kho chi nhánh, vị trí `Zone/Rack/Bin`, nhập kho NCC, xuất kho, điều chuyển liên kho `In-Transit`, kiểm kê, cảnh báo tồn tối thiểu & báo cáo NXT/Thẻ kho).
   - **Giai đoạn 2 (`P2`):** Mở rộng **Hệ thống Bán lẻ (`POS`)** và **Hệ thống Vận chuyển (`TMS`)** kết nối khép kín trên nền tảng `WMS` của `P1`.
3. **Loại hình Client & Trải nghiệm (`Q-QLCH-03`):** **Web App tốc độ cao** (Responsive cho PC, Tablet/POS, Mobile Web) **kết hợp Sơ đồ trực quan 2D** (P1: Sơ đồ 2D layout vị trí kệ/bin kho bãi; P2: Sơ đồ quầy cửa hàng & bản đồ theo dõi tuyến vận chuyển). Kích hoạt vai trò `2D Visual Artist`.
4. **Ràng buộc Vận hành, Thiết bị & Hạ tầng (`Q-QLCH-04`):** Hỗ trợ **Offline-first** (vùng sóng yếu trong kho/quầy/xe giao hàng); tích hợp **Máy quét mã vạch/QR** & **Máy in nhiệt**; tuân thủ nghiêm ngặt nguyên tắc **`$0 First`** và **`100% Thư viện cục bộ (Local Library-First)`** (chưa gọi API bên thứ 3 khi chưa có confirm của Chủ dự án).
5. **Thị trường & KPI (`Q-QLCH-05`):** Thị trường Việt Nam; KPI P1 (`WMS`) khớp tồn kho 100% theo `Bin` & `Lô/HSD`, quét mã `< 1s`, truy vết 100% chứng từ; KPI Toàn trình (`P1+P2`) khép kín luồng *Nhập kho $\rightarrow$ Điều chuyển/Vận chuyển $\rightarrow$ Bán lẻ POS/Giao khách*, khớp tồn kho & COD 100%, lên đơn POS `< 15s/đơn`.
