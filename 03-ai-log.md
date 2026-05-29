# 03-ai-log.md

---

## 1. AI đã giúp gì
Trong quá trình làm lab, tôi đã dùng AI để:
- Brainstorm các ý tưởng problem scan (tạo danh sách 5 problem).
- Viết các Quick Problem Cards và soạn thảo bản nháp cho `02-deep-dive-report.md`.
- Prototype prompt boundary test trong `extras/prompt_prototype.py` để mô phỏng các kịch bản adversarial.


## 2. AI sai gì (Minh họa lỗi/hallucination)
Trong một vài thử nghiệm ban đầu, mô hình đề xuất trạm sạc ở khoảng cách lớn hơn ngưỡng an toàn khi trạng thái pin báo rất thấp — đây là hành vi nguy hiểm nếu không có ranh giới rõ ràng. Ngoài ra, model đôi khi tạo ra thông tin chi tiết giả định (ví dụ: tên trạm sạc không tồn tại).


## 3. Sửa đổi ra sao (Cách điều chỉnh prompt / ranh giới)
Để khắc phục, tôi đã:
- Thêm `SYSTEM_PROMPT` quy định rõ: bắt buộc `[DRAFT_ONLY]` tiền tố cho mọi output và quy tắc nếu pin < 5% thì phải dispatch mobile charger thay vì gợi ý trạm xa.
- Viết các adversarial test cases để kiểm tra ranh giới và mô phỏng kết quả mà không cần gọi API thực.
- Yêu cầu HITL (human-in-the-loop) cho mọi hành động tự động trong giai đoạn thử nghiệm.

---
