# 01 — Problem Scan & Quick Cards (Cá nhân)

> **Lab 02 — AI Product Scoping (Vin Smart Future)**
> File này thể hiện kết quả Phase 1 (SCAN) và Phase 2 (QUICK-ASSESS).

---

## 🔍 Phase 1 — SCAN: Quét cơ hội AI tại các công ty thành viên Vingroup

Sử dụng **4 Lenses** (Lặp lại, Tốn thời gian, AI-upgrade, Stakeholder Pain) để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Dưới đây là danh sách **6 bài toán/bottleneck** thực tế:

### 📝 List bài toán của tôi:

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | **Vinmec** | Tốn thời gian | Bác sĩ điều trị mất 20-30 phút/bệnh nhân để soạn thảo tóm tắt hồ sơ xuất viện (Discharge Summary) — phải tổng hợp thủ công từ bệnh án điện tử, kết quả xét nghiệm, ghi chú lâm sàng và đơn thuốc vào một bản tóm tắt ngắn gọn bằng ngôn ngữ dễ hiểu cho bệnh nhân. |
| 2 | **Vinhomes** | Lặp lại | Phân loại và điều hướng hàng trăm phản ánh/khiếu nại cư dân gửi qua App Vinhomes Resident mỗi ngày (mất nước, hỏng đèn, ồn ào, vi phạm nội quy...) đến đúng ban quản lý từng tòa nhà — nhân viên CSKH phải đọc từng tin nhắn và phân loại thủ công, phản hồi rập khuôn mất trung bình 12 tiếng. |
| 3 | **VinFast** | AI-upgrade | Khách hàng mô tả lỗi xe bằng tiếng Việt tự nhiên (ví dụ: *"xe đi qua gờ giảm tốc kêu cụp cụp ở bánh trước"*), nhân viên CSKH phải tự suy luận và phân loại mã lỗi kỹ thuật ban đầu — quy trình chậm, dễ sai, phụ thuộc kinh nghiệm cá nhân nhân viên. |
| 4 | **Xanh SM** | Pain từ người khác | Tài xế Xanh SM liên tục phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác — khách đặt xe ở ngõ hẻm nhưng GPS pinpoint ra mặt đường lớn, tài xế tốn thêm 5-10 phút liên hệ và tìm đường vào, gây trễ giờ và tăng tỉ lệ hủy chuyến ~12%. |
| 5 | **Vinpearl** | Pain từ người khác | Bộ phận Guest Experience phải quét thủ công hàng nghìn review trên Booking.com, Agoda, Google Maps mỗi tuần để lọc phàn nàn khẩn cấp (*"phòng bẩn"*, *"nhân viên thái độ tệ"*) — mất 2 ngày mới report được cho Manager, bỏ lỡ cơ hội xử lý kịp thời. |
| 6 | **Vinmec** | AI-upgrade | Khách hàng mô tả triệu chứng bệnh qua chatbot đặt lịch khám, hệ thống hiện tại chỉ route theo keyword cứng — thường xuyên xếp sai chuyên khoa (ví dụ: đau ngực do trào ngược dạ dày bị route sang Tim mạch thay vì Tiêu hóa), gây lãng phí thời gian khám lại và ảnh hưởng trải nghiệm bệnh nhân. |

---

## 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards

Chọn **top 3 bài toán** từ danh sách SCAN: **#1 (Vinmec Discharge Summary), #2 (Vinhomes CSKH), #3 (VinFast Chẩn đoán lỗi xe).**

---

### Quick Problem Card #1 — Vinmec: Soạn thảo tóm tắt hồ sơ xuất viện

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Bác sĩ tại Vinmec mất 20-30 phút để soạn thảo   │
│ tóm tắt hồ sơ xuất viện (Discharge Summary) cho mỗi bệnh  │
│ nhân, phải tổng hợp thủ công từ nhiều nguồn dữ liệu lâm   │
│ sàng rời rạc.                                               │
│ Công ty thành viên: [x] Vinmec                              │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Bác sĩ điều trị (quá tải giấy tờ, ít thời gian thăm khám) │
│ và bệnh nhân (chờ đợi lâu để nhận giấy xuất viện).         │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Thu thập bệnh án điện tử (EMR) & lịch sử điều trị     │
│   ──> 2. Rà soát kết quả xét nghiệm & chẩn đoán hình ảnh  │
│   ──> 3. Tổng hợp thủ công thông tin từ nhiều hệ thống     │
│   ──> 4. Soạn bản tóm tắt bằng ngôn ngữ dễ hiểu           │
│   ──> 5. Bác sĩ trưởng ký duyệt & in gửi bệnh nhân        │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Bước 3-4 (⏱ 20 phút/lượt) — tổng hợp dữ liệu rời rạc và  │
│ diễn giải thành văn bản dễ hiểu cho bệnh nhân.              │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ Bước 3-4: Tự động trích xuất thông tin từ EMR, xét nghiệm, │
│ ghi chú bác sĩ → draft bản tóm tắt xuất viện có cấu trúc.  │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ "Giảm thời gian soạn tóm tắt xuất viện từ 25 phút ──>      │
│ dưới 5 phút. Tỉ lệ nội dung chính xác ≥ 95%."              │
│                                                             │
│ Quick Architecture: [x] LLM Feature                         │
│ (Trích xuất & tóm tắt NLP từ dữ liệu lâm sàng có cấu trúc)│
└─────────────────────────────────────────────────────────────┘
```

---

### Quick Problem Card #2 — Vinhomes: Phân loại & Điều hướng phản ánh cư dân

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Phân loại tự động các khiếu nại/phản ánh từ cư   │
│ dân gửi qua App Vinhomes Resident (mất nước, hỏng đèn, ồn  │
│ ào, vi phạm nội quy) và điều hướng đến đúng ban quản lý.   │
│ Công ty thành viên: [x] Vinhomes                            │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Nhân viên CSKH Ban Quản Lý tòa nhà (đọc từng tin phân loại │
│ thủ công) và cư dân (chờ phản hồi lâu, trung bình 12 giờ). │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Cư dân gửi phản ánh qua App/Email                      │
│   ──> 2. NV CSKH đọc và phân loại thủ công (loại sự cố,    │
│          mức độ khẩn cấp, tòa nhà/tầng)                     │
│   ──> 3. Forward đến đúng bộ phận xử lý (kỹ thuật/bảo vệ/  │
│          vệ sinh)                                            │
│   ──> 4. Soạn phản hồi xác nhận gửi lại cư dân              │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Bước 2-3 (⏱ 15 phút/lượt) — phân loại sai sự cố dẫn đến   │
│ forward nhầm bộ phận, phải chuyển tiếp lại mất thêm thời    │
│ gian, tỉ lệ phân loại sai hiện tại ~18%.                    │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ Bước 2-3: Tự động phân loại nội dung phản ánh, xác định     │
│ mức độ khẩn cấp, route đến đúng bộ phận xử lý.              │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ "Giảm thời gian phản hồi từ 12 giờ ──> dưới 1 giờ.          │
│ Tỉ lệ phân loại chính xác đạt ≥ 92%."                       │
│                                                             │
│ Quick Architecture: [x] Rule + LLM                           │
│ (Rule-based router cho các loại phổ biến, LLM cho các case   │
│ mô tả phức tạp/mơ hồ)                                       │
└─────────────────────────────────────────────────────────────┘
```

---

### Quick Problem Card #3 — VinFast: Chẩn đoán lỗi xe từ mô tả tiếng Việt

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: Khách hàng VinFast mô tả lỗi xe bằng tiếng Việt  │
│ tự nhiên, hệ thống cần tự động phân loại mã lỗi kỹ thuật   │
│ ban đầu (DTC code) để rút ngắn thời gian tiếp nhận.        │
│ Công ty thành viên: [x] VinFast                             │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Nhân viên CSKH hotline VinFast (phải tự suy luận mã lỗi    │
│ từ mô tả mơ hồ) và kỹ thuật viên (nhận sai mã lỗi, mất    │
│ thêm thời gian chẩn đoán lại).                              │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Khách gọi hotline mô tả lỗi bằng tiếng Việt            │
│   ──> 2. NV CSKH ghi chú và tra cứu bảng mã lỗi thủ công   │
│   ──> 3. Gán mã lỗi DTC ban đầu dựa trên kinh nghiệm       │
│   ──> 4. Chuyển ticket cho xưởng dịch vụ kèm mã lỗi         │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Bước 2-3 (⏱ 8 phút/lượt) — NV CSKH thiếu chuyên môn kỹ    │
│ thuật, phân loại sai mã lỗi ~25% cases, dẫn đến xưởng phải │
│ chẩn đoán lại từ đầu.                                       │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ Bước 2-3: NLP phân tích mô tả tiếng Việt → map sang bảng   │
│ mã DTC, đề xuất top 3 mã lỗi có xác suất cao nhất.          │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ "Tăng tỉ lệ gán đúng mã lỗi ban đầu từ 75% ──> 90%.        │
│ Giảm thời gian tiếp nhận từ 8 phút ──> dưới 3 phút."        │
│                                                             │
│ Quick Architecture: [x] LLM Feature                         │
│ (NLP phân tích ngôn ngữ tự nhiên tiếng Việt + mapping mã lỗi│
│ có cấu trúc)                                                 │
└─────────────────────────────────────────────────────────────┘
```
