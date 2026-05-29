
---

## 1. AI Giúp Gì Trong Buổi Học?

Buổi học hôm nay tôi dùng Claude như một *thought-partner* xuyên suốt cả hai phase của worksheet, không phải để "copy đáp án" mà để tăng tốc độ khám phá và kiểm tra logic của bản thân.

### Phase 1 — Brainstorm bài toán (SCAN)

Tôi bắt đầu bằng cách hỏi Claude về các công ty công nghệ trong hệ sinh thái Vingroup để định vị ngữ cảnh trước khi brainstorm. Claude đã cung cấp danh sách tương đối đầy đủ từ VinAI, VinBigData đến các công ty mới như VinRobotics, VinMotion, VinDynamics, VinSmart Future, VinSurgical — giúp tôi nắm bức tranh toàn cảnh nhanh hơn nhiều so với tự tra Google.

Khi vào Phase 1, tôi không dùng prompt mẫu trong worksheet mà tự đặt câu hỏi theo từng lens:

> *"Trong hệ sinh thái Vingroup, quy trình nào tại Xanh SM đang gây ra cancellation rate cao nhất, và AI có thể can thiệp ở điểm nào?"*

Claude phản hồi theo hướng phân tích dispatch system, ETA prediction, và driver-rider matching — đúng với những gì tôi đang tìm kiếm. Từ đó tôi tự hình thành được 5 bài toán trong bảng Phase 1.

### Phase 2 — Điền Quick Problem Cards

Tôi dùng Claude để:
- **Ước lượng con số thực tế** (VD: agent xử lý bao nhiêu ticket/ngày, ETA error trung bình là bao nhiêu phút) vì bản thân không có dữ liệu nội bộ Vingroup.
- **Gợi ý architecture phù hợp** — sau khi tôi đã tự điền xong workflow thủ công, tôi hỏi Claude nên dùng LLM, Agent, hay Rule-based ở từng bước, và tại sao.
- **Viết metric cụ thể** — tôi có xu hướng viết metric mơ hồ ("phản hồi nhanh hơn"), Claude giúp tôi chuyển thành dạng có số đo được ("10 phút → dưới 2 phút").

---

## 2. AI Sai Gì? — Điểm Hallucination Ghi Nhận

### Lỗi #1: Bịa số liệu thống kê

Khi tôi hỏi:

> *"Tỉ lệ hủy chuyến trung bình của Xanh SM hiện tại là bao nhiêu %?"*

Claude trả lời một cách tự tin:

> *"Cancellation rate của Xanh SM ước tính khoảng 18–22% vào giờ cao điểm, dựa trên các benchmark của ride-hailing tương đương tại Đông Nam Á như Grab và Gojek."*

**Vấn đề:** Xanh SM là công ty non-public, không có dữ liệu open-source về cancellation rate. Con số "18–22%" là hallucination — Claude đã tự suy diễn từ benchmark của Grab/Gojek và trình bày như một con số có căn cứ của Xanh SM, điều này hoàn toàn không chính xác.

Nếu đưa con số này vào Problem Card mà không kiểm chứng, tôi sẽ trình bày một bài toán dựa trên dữ liệu bịa — rất nguy hiểm trong context thực tế.

### Lỗi #2: Đề xuất architecture quá phức tạp so với bài toán

Với bài toán chatbot Xanh SM (Card #3), lần đầu Claude đề xuất:

> *"Xây dựng multi-agent system với một Orchestrator Agent điều phối 4 sub-agents: Intent Agent, Slot-filling Agent, Memory Agent, và Fallback Agent, chạy song song với message queue Kafka."*

**Vấn đề:** Đây là over-engineering rõ ràng. Với một chatbot đặt xe đơn giản (chỉ cần hiểu điểm đón + điểm đến + thời gian), một LLM đơn với function calling và conversation memory là đủ. Đề xuất multi-agent + Kafka làm tăng độ phức tạp vận hành mà không tương xứng với lợi ích, đặc biệt ở giai đoạn MVP.

---

## 3. Sửa Đổi Ra Sao?

### Cách xử lý Lỗi #1 — Hallucination con số

Tôi học được một nguyên tắc quan trọng: **không bao giờ hỏi AI con số của một công ty private.** Thay vào đó, tôi điều chỉnh cách đặt câu hỏi:

**Prompt cũ (dễ hallucinate):**
> *"Cancellation rate của Xanh SM là bao nhiêu?"*

**Prompt mới (buộc AI khai báo nguồn):**
> *"Hãy cho tôi benchmark cancellation rate của các ride-hailing app tại Đông Nam Á từ các nguồn công khai (báo cáo Grab, Gojek, Be). Đánh dấu rõ đây là benchmark ngành, KHÔNG phải số liệu của Xanh SM."*

Kết quả Claude trả về lần này rõ ràng hơn nhiều — phân biệt rõ "ngành benchmark" vs "ước tính", và tôi tự ghi chú vào Problem Card là *"~20% cancellation rate — benchmark ride-hailing SEA, cần validate với Xanh SM ops team"*.

Bài học: **AI không biết dữ liệu nội bộ của bất kỳ công ty nào — mọi con số về Vingroup từ AI đều là ước tính, cần label rõ trong tài liệu.**

### Cách xử lý Lỗi #2 — Over-engineering

Tôi thêm một ràng buộc rõ ràng vào prompt:

**Prompt bổ sung constraint:**
> *"Hãy đề xuất lại architecture cho chatbot này với ràng buộc: team 2 engineer, timeline 3 tháng, phải ship MVP trước. Ưu tiên simplicity. Nếu LLM đơn đủ giải quyết, đừng thêm agent."*

Claude ngay lập tức điều chỉnh về hướng đơn giản hơn: *"Với constraint đó, dùng single LLM (GPT-4o mini hoặc Gemini Flash) + function calling cho slot-filling + Redis lưu conversation memory là đủ cho MVP."* — đúng hơn nhiều so với đề xuất ban đầu.

Bài học: **AI mặc định đề xuất theo hướng "impressive" và "comprehensive", không phải theo hướng "đủ dùng". Cần luôn thêm constraint về team size, timeline, và budget vào prompt.**

---
