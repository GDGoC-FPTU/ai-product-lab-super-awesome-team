# 02-deep-dive-report.md

## Thông tin nhóm
- Tên nhóm: Super Awesome Team
- Thành viên (Họ tên - MSSV):
  - Nguyễn Văn A - 12345678
  - Trần Thị B - 23456789
  - Lê Văn C - 34567890

---

## 1. Quyết định lựa chọn
- Bài toán được chọn: Xanh SM — Intelligent Dispatcher (Tối ưu phân bổ cuốc và reassign khi có sự cố)

## 2. Problem Statement (6-field)
| Field | Nội dung chi tiết |
|---|---|
| Actor / Operator | Dispatcher operations team tại Xanh SM; drivers; customer support. |
| Current Workflow | Hệ thống gợi ý cuốc tự động, dispatcher kiểm tra và chỉnh sửa thủ công, liên hệ lái xe nếu cần, theo dõi trạng thái; nếu lái xe huỷ hoặc trễ, dispatcher tìm driver thay thế thủ công. |
| Bottleneck | Manual reassignment process causes delay (avg 8 minutes), requires human verification and phone calls. |
| Business Impact | High operational cost for dispatchers, increased customer wait times, driver dissatisfaction leading to churn. Estimated cost: 2000+ minutes of human time per week across city operations. |
| Success Metric | Reduce average reassignment time from 8 minutes to under 2 minutes; reduce cancellation rate below 5%; improve driver utilization by 8%. |
| Operational Boundary | AI can suggest reassignments and draft messages but MUST prefix any outgoing instruction with `[DRAFT_ONLY]` and require human approval before automated dispatch; in safety-critical cases (vehicle battery critical or safety), escalate to human immediately. |

---

## 3. Future-State Flow & AI Fit
- AI Fit (tick one): [ ] Rule  [x] LLM Feature  [ ] Agentic Loop
- Future-State Flow (mô tả hoặc text-diagram):

1. Incoming trip request -> 2. LLM scores candidate drivers + proposes optimal assignment -> 3. Dispatcher reviews `[DRAFT_ONLY]` suggestion -> 4. If approved, system confirms with driver and updates status -> 5. Monitor trip and re-run LLM on exceptions.

- Fallback: If LLM confidence < threshold or in edge safety cases, route to human dispatcher for manual handling. All automated suggestions logged for audit.

---

## 4. Evaluate (Checklist & Decision)
- AI Readiness Checklist:
  - [x] Có dữ liệu mẫu/logs (ride logs with timestamps, driver statuses) — dataset available for initial MVP.
  - [x] Rủi ro khi AI sai có nằm trong tầm kiểm soát (HITL + fallback) — human approval required for final actions.
  - [x] Stakeholders sẵn sàng (Operations team agreed to pilot with DAL restrictions).

- Quyết định cuối cùng: [x] GO  [ ] NOT YET  [ ] NO-GO

- Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):
  - Technical: High signal-to-noise in historical data makes ML/LLM-assisted ranking feasible. The task requires natural language short justification and structured outputs for dispatcher which an LLM can produce reliably at MVP scale.
  - Cost: Pilot scoped to a single city zone; engineering effort estimated 2-3 sprints, infra cost minimal using existing dispatch APIs. Benefit: reduced manual load and faster customer recovery.

---

## 5. Workflow Mapping (Current-State)
- Mô tả các bước hiện tại:
  1. System suggests initial assignments
  2. Dispatcher reviews and edits suggestions
  3. Dispatcher contacts driver (call/SMS) if needed
  4. Tracks trip and reassigns on exceptions
- Tổng thời gian trung bình: 8 phút/lượt (reassign cases)
- Bottlenecks (nêu rõ): Manual verification and phone calls; fragmented driver availability view.

*Gợi ý: thay tên thành viên và MSSV bằng thông tin thực tế nhóm trước khi nộp.*