# Nhật ký chiêm nghiệm về việc tương tác với AI

## 1. AI giúp gì

Trong buổi học này, tôi dùng AI như một người đồng hành để brainstorm bài toán vận hành, chọn top 3 quick cards, và thử xây prompt prototype cho Gemini. AI hỗ trợ tốt ở phần mở rộng ý tưởng: gợi ý cách mô tả workflow thủ công, nhắc tôi phải viết metric có số, và giúp tôi nghĩ ra các prompt tấn công để kiểm tra ranh giới an toàn. Tôi cũng dùng AI để rà lại logic của các thẻ bài toán, xem bài nào phù hợp với LLM hơn và bài nào thực ra chỉ cần rule-based là đủ.

## 2. AI sai gì

Tuy vậy, AI không phải lúc nào cũng đúng. Có lúc nó đề xuất giải pháp quá “tham”, ví dụ muốn dùng agent cho những quy trình vốn khá cố định, trong khi rule-based hoặc một LLM feature đơn giản đã đủ. Nếu không kiểm tra kỹ, AI còn có thể trả lời quá chung chung, metric mơ hồ, hoặc viết prompt vượt ranh giới an toàn theo kiểu nghe hợp lý nhưng không đúng với yêu cầu vận hành. Điều đó khiến tôi nhận ra AI rất hữu ích để tăng tốc suy nghĩ, nhưng không thể thay thế việc tự đánh giá rủi ro và tính thực tế của bài toán.

## 3. Tôi sửa đổi ra sao

Sau những lần thử đó, tôi đã chỉnh prompt theo hướng chặt hơn: viết rõ vai trò của hệ thống, thêm ranh giới bắt buộc như `[DRAFT_ONLY]`, quy định rõ trường hợp pin dưới 5% thì phải dispatch mobile charger thay vì đề xuất trạm xa, và ép output về dạng rõ ràng hơn để dễ kiểm tra. Tôi cũng bổ sung các adversarial input cố tình bypass rule để xem AI có phá rào hay không. Cách làm này giúp kết quả ổn định hơn và cho tôi một bài học rõ ràng: muốn AI hữu ích trong môi trường vận hành thật, prompt phải có ranh giới cụ thể, metric phải đo được, và luôn cần người kiểm tra cuối cùng.
