# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

### 📝 List bài toán của tôi:
| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | **Vinhomes** | Lặp lại | Phân loạt và điều phối yêu cầu sửa chữa của cư dân. |
| 2 | **Vinmec** | Tốn thời gian | Bác sĩ đọc lại toàn bộ lịch sử bệnh án (đôi khi 30+ trang PDF scan) trước khi gặp bệnh nhân tái khám. Không có công cụ tóm tắt tự động. |
| 3 | **VinFast** | AI-upgrade | Hiện tại cảnh báo pin chỉ dựa trên ngưỡng cứng (SOH < 70%). Không có mô hình dự đoán sớm dựa trên pattern sạc/xả. Khách hàng bị bất ngờ khi xe hỏng pin. |
| 4 | **VinFast** | Lặp lại | Kỹ thuật viên đại lý gọi hotline kỹ thuật VinFast để hỏi quy trình sửa chữa. ~60% câu hỏi là câu hỏi lặp lại đã có trong tài liệu kỹ thuật nội bộ. |
| 5 | **Xanh SM** | Lặp lại | Bộ phận CSKH phải đọc từng khiếu nại, phân loại (hành vi tài xế / sự cố xe / thanh toán / ứng dụng), và chuyển đúng team xử lý. ~500 khiếu nại/ngày. |
| 6 | **Xanh SM** | Stakeholder Pain | Hệ thống dispatch hiện tại dựa trên khoảng cách gần nhất, bỏ qua tắc đường, thời tiết, và các sự kiện lớn. Tài xế phàn nàn về điểm đón không hợp lý. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Top 3 từ danh sách SCAN: **#2 (Vinmec tóm tắt hồ sơ bệnh án), #3 (VinFast dự đoán suy giảm pin), #6 (Xanh SM dispatch chuyến xe không tối ưu giờ cao điểm).**

## Quick Problem Card #2 — Vinmec Tóm tắt hồ sơ bệnh án

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Bác sĩ phải đọc lại toàn bộ lịch sử bệnh án       │
│ (thường là 30+ trang PDF scan) trước mỗi buổi tái khám.     │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes │
│                     [x] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Bác sĩ chuyên khoa / bác sĩ tái khám   │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Nhận hồ sơ giấy/PDF scan từ hệ thống bệnh án           │
│   2. Đọc từng trang để tìm triệu chứng, thuốc, xét nghiệm    │
│   3. Ghi chú lại các mốc quan trọng cho buổi khám tiếp theo │
│   4. Soạn tóm tắt ngắn trước khi gặp bệnh nhân               │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-3                   │
│ (⏱ 20-30 phút/lượt)                                         │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-4              │
│ (OCR + trích xuất dữ kiện + draft tóm tắt có cấu trúc)      │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                      │
│ Giảm thời gian chuẩn bị hồ sơ tái khám từ 25 phút xuống <5  │
│ phút, và trích xuất đúng ít nhất 90% thông tin quan trọng.  │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent│
└─────────────────────────────────────────────────────────────┘
```

## Quick Problem Card #3 — VinFast Dự đoán suy giảm pin

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: Cảnh báo pin hiện tại chỉ dựa trên ngưỡng cứng    │
│ (SOH < 70%), chưa dự đoán sớm theo pattern sạc/xả.          │
│ Công ty thành viên: [x] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Kỹ sư bảo hành / service advisor       │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Xem dashboard pin và ngưỡng SOH hiện tại               │
│   2. So sánh log sạc/xả gần đây với kinh nghiệm kỹ thuật    │
│   3. Gọi điện cho chủ xe khi đã có cảnh báo muộn             │
│   4. Sắp lịch kiểm tra hoặc thay pin khi xe đã bắt đầu lỗi   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-3                   │
│ (⏱ 15-20 phút/lượt, dễ bỏ sót mẫu bất thường)                │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2                │
│ (phân tích pattern, xếp hạng rủi ro, draft cảnh báo sớm)    │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                      │
│ Phát hiện sớm ít nhất 80% trường hợp pin suy giảm trước      │
│ 2 tuần so với ngưỡng cứng, và giảm 30% số ca hỏng pin bất ngờ│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent│
└─────────────────────────────────────────────────────────────┘
```

## Quick Problem Card #6 — Xanh SM Dispatch chuyến xe giờ cao điểm

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #6                                       │
│                                                             │
│ Bài toán: Dispatch hiện tại ưu tiên khoảng cách gần nhất,   │
│ nhưng bỏ qua tắc đường, thời tiết, và sự kiện lớn.          │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Điều phối viên Xanh SM / tài xế        │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Nhận cuốc xe và vị trí khách đặt                        │
│   2. Kiểm tra danh sách tài xế gần nhất trên bản đồ          │
│   3. So sánh nhanh với tình trạng kẹt xe / thời tiết         │
│   4. Chọn tài xế và gửi lệnh điều xe                         │
│   5. Theo dõi phản hồi/hủy chuyến nếu ETA thực tế quá cao    │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-4                   │
│ (⏱ 3-5 phút/lượt, dễ chọn nhầm tài xế trong giờ cao điểm)    │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-4              │
│ (xếp hạng cuốc xe, tính ETA, draft quyết định điều xe)      │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                      │
│ Giảm thời gian ra quyết định dispatch từ 5 phút xuống <30s, │
│ tăng tỷ lệ cuốc xe được gán đúng trong giờ cao điểm lên 90%.│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘
```