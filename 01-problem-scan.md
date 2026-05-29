# 01-problem-scan.md

## Phase 1 — SCAN (5 problems)
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Xanh SM (GSM) | Repetitive / Time-consuming | Dispatcher manually reassigns delayed trips; many reassignments per day causing delays and driver dissatisfaction. |
| 2 | VinFast | AI-upgrade | EV battery routing: drivers need fast suggestions for charging or mobile charger dispatch when battery low. |
| 3 | Vinhomes | Time-consuming | Manual processing of 1-star resident complaints and drafting personalized responses. |
| 4 | Vinmec | Stakeholder Pain | Triage of incoming patient messages to correct department; manual mistakes cause delays. |
| 5 | Vinpearl | Repetitive | Ticket refund and booking change requests processed manually across systems causing long SLA. |

---

## Phase 2 — QUICK-ASSESS (3 Quick Problem Cards)

### QUICK PROBLEM CARD #1
- Bài toán (1 câu): Tối ưu điều vận và phân bổ cuốc cho tài xế Xanh SM để giảm thời gian chờ và tỉ lệ huỷ chuyến.
- Công ty thành viên: Xanh SM (GSM)
- Ai đang đau (Actor)? Dispatcher operations team, drivers, end customers.
- Workflow thủ công hiện tại (3-5 bước):
  1. Hệ thống gợi ý cuốc ban đầu → 2. Dispatcher review và chỉnh sửa thủ công → 3. Giao tiếp với lái xe → 4. Theo dõi trạng thái và reassign nếu cần.
- Bước nào tốn thời gian/lỗi nhất? Manual reassignments và checking driver availability (⏱ ~5-10 phút/case).
- AI có thể nhảy vào ở bước nào? Tự động phân tích lịch sử, ưu tiên lái xe, đề xuất reassign tức thời.
- Đo thành công bằng gì (Metric có số)? Giảm thời gian reassign trung bình từ 8 phút xuống dưới 2 phút; giảm tỉ lệ huỷ < 5%.
- Quick Architecture: [ ] No AI  [x] LLM  [ ] Agent

---

### QUICK PROBLEM CARD #2
- Bài toán (1 câu): Khi pin EV xuống dưới ngưỡng, hệ thống phải quyết định gửi mobile charger hay điều hướng tới trạm gần nhất.
- Công ty thành viên: VinFast
- Ai đang đau (Actor)? Hỗ trợ đường dây cứu hộ và tài xế EV.
- Workflow thủ công hiện tại (3-5 bước):
  1. Tài xế gọi hỗ trợ → 2. Agent xác minh vị trí và trạng thái pin → 3. Dispatcher quyết định gửi mobile charger hoặc hướng dẫn trạm sạc → 4. Thực hiện hành động.
- Bước nào tốn thời gian/lỗi nhất? Quyết định dispatch vs hướng dẫn dựa trên vị trí và mức pin (⏱ ~10 phút/case).
- AI có thể nhảy vào ở bước nào? Tự động đánh giá rủi ro, quyết định dispatch mobile charger khi pin < 5%.
- Đo thành công bằng gì (Metric có số)? Giảm thời gian quyết định từ 10 phút xuống <1 phút; giảm số vụ chết máy do pin xuống 90%.
- Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent

---

### QUICK PROBLEM CARD #3
- Bài toán (1 câu): Tự động phân loại và soạn thảo draft trả lời cho phản hồi 1-star của cư dân Vinhomes.
- Công ty thành viên: Vinhomes
- Ai đang đau (Actor)? Nhóm CSKH và quản lý toà nhà.
- Workflow thủ công hiện tại (3-5 bước):
  1. Nhận phản hồi → 2. Người CSKH đọc và phân loại vấn đề → 3. Soạn trả lời → 4. Gửi và theo dõi.
- Bước nào tốn thời gian/lỗi nhất? Phân loại và soạn trả lời (⏱ ~15-20 phút/case).
- AI có thể nhảy vào ở bước nào? Phân loại nội dung và tạo draft trả lời chuẩn hoá.
- Đo thành công bằng gì (Metric có số)? Giảm thời gian xử lý trung bình từ 20 phút xuống <5 phút; tăng tỉ lệ phản hồi đúng chủ đề > 90%.
- Quick Architecture: [ ] No AI  [x] Rule  [ ] LLM  [ ] Agent

---