

---

## 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | Xanh SM | Repetitive | Hệ thống dispatch chuyến đi chỉ dựa trên khoảng cách Euclidean, bỏ qua tắc đường giờ cao điểm → tài xế phàn nàn, ETA sai, cancellation rate cao |
| 2 | Vinhomes | Time-consuming | Nhân viên CSKH mất 8–12 phút/ticket soạn thủ công phản hồi khiếu nại cư dân (hỏng thang máy, rò rỉ nước...) — ước tính ~200 ticket/ngày/khu đô thị lớn |
| 3 | VinFast | AI-upgrade | Quy trình kiểm tra lỗi ngoại thất xe trên dây chuyền còn dùng mắt người → tỉ lệ bỏ sót ~2–3%, mỗi xe recall tốn ~50–200 triệu VND |
| 4 | Vinmec | Stakeholder Pain | Bác sĩ mất 15–20 phút/ca gõ tay tóm tắt hồ sơ bệnh nhân trước khi hội chẩn — với 300+ ca/ngày toàn hệ thống là bottleneck rõ ràng |
| 5 | Xanh SM | AI-upgrade | Chatbot đặt xe hiện chỉ hiểu lệnh cứng nhắc, không xử lý được tiếng Việt địa phương hay câu nói mơ hồ ("đón ở chỗ quen đó") → drop-off rate cuộc hội thoại ~40% |

---

## 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #___                                     │
│                                                             │
│ Bài toán (1 câu): ________________________________________  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? ______________________________________ │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. ___ ──> 2. ___ ──> 3. ___ ──> 4. ___                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? ___ (⏱ ___ phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? _____________________ │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? ______________________ │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

Tôi chọn bài toán **#1, #2, #5** vì cover đủ 3 domain khác nhau và đều sát với tech stack của VinSmart Future.

---

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Hệ thống gợi ý điểm đón & dispatch tài xế        │
│ Xanh SM không tối ưu theo context thực tế (thời gian,       │
│ traffic, hành vi tài xế), dẫn đến ETA sai & hủy chuyến.    │
│                                                             │
│ Công ty thành viên: [x] Xanh SM                             │
│                                                             │
│ Ai đang đau?                                                │
│  - Tài xế: nhận chuyến xa, chờ lâu, thu nhập giảm          │
│  - Khách: ETA sai, hủy chuyến, trải nghiệm kém              │
│  - Ops team: manual override liên tục                        │
│                                                             │
│ Workflow thủ công hiện tại:                                  │
│  1. Khách đặt xe (app)                                      │
│  2. Hệ thống tìm tài xế gần nhất (khoảng cách thẳng)       │
│  3. Gửi thông báo → tài xế accept/reject                    │
│  4. Nếu reject, vòng lại bước 2 thủ công                    │
│  5. ETA hiển thị = distance / speed_avg (cứng)              │
│                                                             │
│ Bước tốn thời gian/lỗi nhất?                                │
│  Bước 2 & 5 — ETA sai trung bình 4–7 phút giờ cao điểm     │
│                                                             │
│ AI nhảy vào ở bước nào?                                     │
│  Bước 2: ML ranking model (tài xế × context features)       │
│  Bước 5: Deep learning ETA prediction (graph + time-series) │
│                                                             │
│ Metric thành công:                                           │
│  - ETA error: 6 min → dưới 2 min (giờ cao điểm)            │
│  - Cancellation rate: -25%                                   │
│  - Dispatch acceptance rate: +15%                            │
│                                                             │
│ Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent/ML    │
│  → Hybrid: GNN (road graph) + LightGBM ranking              │
└─────────────────────────────────────────────────────────────┘
```

---

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Nhân viên CSKH Vinhomes soạn thủ công phản hồi   │
│ khiếu nại cư dân, mỗi ticket mất 8–12 phút, không nhất     │
│ quán về tone và giải pháp đề xuất.                          │
│                                                             │
│ Công ty thành viên: [x] Vinhomes                            │
│                                                             │
│ Ai đang đau?                                                │
│  - Nhân viên CSKH: overload, burnout với ticket lặp lại     │
│  - Cư dân: chờ phản hồi 2–4 tiếng, chất lượng không đều    │
│  - Quản lý: khó audit, không có insight về loại khiếu nại   │
│                                                             │
│ Workflow thủ công hiện tại:                                  │
│  1. Cư dân gửi khiếu nại (app/hotline)                      │
│  2. Agent đọc, phân loại (kỹ thuật/dịch vụ/an ninh...)     │
│  3. Tra cứu SOP nội bộ để tìm hướng xử lý                   │
│  4. Soạn email/tin nhắn phản hồi thủ công                   │
│  5. Escalate lên bộ phận kỹ thuật nếu cần                   │
│                                                             │
│ Bước tốn thời gian/lỗi nhất?                                │
│  Bước 3 + 4 — tra SOP + soạn thảo: ~7 phút/ticket          │
│                                                             │
│ AI nhảy vào ở bước nào?                                     │
│  Bước 2: Auto-classify ticket (LLM + few-shot)              │
│  Bước 3: RAG trên SOP nội bộ → draft giải pháp              │
│  Bước 4: LLM draft phản hồi → agent review 1 click         │
│                                                             │
│ Metric thành công:                                           │
│  - Thời gian xử lý/ticket: 10 min → dưới 2 min             │
│  - First response time: 3 giờ → dưới 30 phút               │
│  - CSAT score cư dân: +20%                                   │
│  - Agent capacity: xử lý gấp 3x volume hiện tại             │
│                                                             │
│ Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent       │
│  → RAG pipeline: embedding SOP + LLM draft + human-in-loop  │
└─────────────────────────────────────────────────────────────┘
```

---

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: Chatbot đặt xe Xanh SM không hiểu tiếng Việt     │
│ tự nhiên/địa phương, drop conversation khi gặp input        │
│ mơ hồ hoặc ngoài script → mất khách ngay trên app.         │
│                                                             │
│ Công ty thành viên: [x] Xanh SM                             │
│                                                             │
│ Ai đang đau?                                                │
│  - Khách hàng: thất vọng khi chatbot "không hiểu mình"      │
│  - Product team: conversion rate thấp qua kênh chat         │
│  - Call center: bị overflow từ khách chuyển sang hotline    │
│                                                             │
│ Workflow thủ công hiện tại:                                  │
│  1. Khách nhắn tin đặt xe (câu tự nhiên)                    │
│  2. Rule-based bot match keyword cứng                        │
│  3. Nếu không match → "Xin lỗi, tôi không hiểu" → loop     │
│  4. Khách bỏ cuộc hoặc gọi hotline                          │
│  5. Agent hotline xử lý từ đầu (tốn 3–5 phút/cuộc)         │
│                                                             │
│ Bước tốn thời gian/lỗi nhất?                                │
│  Bước 2 → 3: failure loop, drop rate ~40% conversation      │
│                                                             │
│ AI nhảy vào ở bước nào?                                     │
│  Bước 2: LLM-powered NLU — hiểu intent dù câu mơ hồ        │
│  + slot filling thông minh (điểm đón mơ hồ → clarify)      │
│  + memory ngắn hạn ("chỗ quen" → lưu địa chỉ hay dùng)     │
│                                                             │
│ Metric thành công:                                           │
│  - Conversation completion rate: 60% → trên 90%             │
│  - Hotline overflow: giảm 35%                               │
│  - Booking thành công qua chat: tăng 2x                      │
│  - Intent recognition accuracy: trên 95% trên test set VN   │
│                                                             │
│ Architecture: [ ] No AI  [ ] Rule  [x] LLM  [x] Agent       │
│  → LLM Agent + slot-filling + memory + fallback graceful    │
└─────────────────────────────────────────────────────────────┘
```

