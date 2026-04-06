# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> *Câu trả lời của bạn*

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> *Câu trả lời của bạn*

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Tổng token mỗi ngày: 10.000 × 3 × 350 = 10.500.000 tokens
> Chi phí GPT-4o: (10.500.000 / 1000) × $0.010 = $105/ngày
> Chi phí GPT-4o-mini: (10.500.000 / 1000) × $0.0006 = $6.30/ngày
> GPT-4o đắt hơn khoảng **16.67 lần** so với GPT-4o-mini cho workload này ($105 vs $6.30)

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> **GPT-4o xứng đáng:** Cho các tác vụ yêu cầu lập luận phức tạp, phân tích chuyên sâu hoặc hiểu biết ngữ cảnh cao như phân tích pháp lý, tư vấn kinh doanh, hoặc xử lý các vấn đề có độ phức tạp cao. Chi phí cao hơn là có giá trị vì độ chính xác cao hơn có thể tiết kiệm thời gian hoặc tránh sai lầm tốn kém.
> 
> **GPT-4o-mini là lựa chọn tốt hơn:** Cho các tác vụ đơn giản như phân loại văn bản, trả lời các câu hỏi thường gặp, tóm tắt nội dung cơ bản, hoặc chatbot hỗ trợ khách hàng định tuyến yêu cầu. Vì khối lượng lớn nhưng yêu cầu chi phí thấp, GPT-4o-mini tiết kiệm chi phí đáng kể mà chất lượng vẫn đủ tốt.
Điều này cho thấy với hệ thống scale lớn, việc chọn model có thể tạo ra sự chênh lệch chi phí rất lớn (hơn $98/ngày), tương đương gần $3,000/tháng.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming là rất quan trọng cho các ứng dụng tương tác thời gian thực như chatbots, trợ lý ảo hoặc các công cụ viết (code generation, content creation) nơi người dùng muốn thấy phản hồi xuất hiện từng token với độ trễ tối thiểu, tạo cảm giác tự nhiên và giảm \"waiting time perception\". Ngược lại, non-streaming phù hợp hơn cho các tác vụ xử lý batch (xử lý hàng loạt tài liệu), các API backend nơi toàn bộ response được lưu trữ hoặc xử lý tiếp, hoặc các ứng dụng yêu cầu full response trước khi hiển thị kết quả (như quản lý dự kiến chi phí, báo cáo tổng hợp). Streaming cũng tạo ra overhead kết nối TCP mạnh hơn, vì vậy với response ngắn hoặc network bị giới hạn, non-streaming có thể hiệu quả hơn.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
