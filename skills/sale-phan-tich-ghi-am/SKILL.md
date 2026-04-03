---
name: sale-phan-tich-ghi-am
description: Nhập file ghi âm cuộc gọi/cuộc họp với khách hàng, chuyển thành text và phân tích nhu cầu, tâm lý khách hàng. Sử dụng khi cần phân tích cuộc gọi sale, đánh giá cảm xúc khách, trích xuất action items, xác định pain points. Trigger khi user upload file ghi âm (mp3, wav, m4a, ogg) hoặc yêu cầu phân tích cuộc gọi khách hàng.
---

# Phân tích Ghi âm Khách hàng

## Yêu cầu

- File ghi âm (mp3, wav, m4a, ogg)
- Whisper hoặc dịch vụ speech-to-text (AssemblyAI, Google Speech)

## Quy trình

### Bước 1: Chuyển đổi âm thanh thành text

Sử dụng Whisper (local) hoặc API:

```python
import whisper

model = whisper.load_model("medium")
result = model.transcribe("cuoc-goi.mp3", language="vi")
transcript = result["text"]
```

Nếu có nhiều người nói, dùng diarization để phân biệt:
- Speaker 1 (Sale): "..."
- Speaker 2 (Khách): "..."

### Bước 2: Phân tích nội dung

Từ transcript, phân tích:

**A. Nhu cầu khách hàng:**
- Sản phẩm/dịch vụ quan tâm
- Vấn đề đang gặp (pain points)
- Mong muốn cụ thể
- Budget dự kiến
- Timeline mong muốn

**B. Tâm lý khách hàng:**
- Mức độ quan tâm: Rất quan tâm / Quan tâm / Bình thường / Không quan tâm
- Trạng thái cảm xúc: Hài lòng / Trung lập / Khó chịu / Tức giận
- Sẵn sàng mua: Sẵn sàng / Cần thêm thời gian / Đang so sánh / Từ chối
- Mối lo ngại chính: Giá / Chất lượng / Thời gian / Uy tín

**C. Đánh giá cuộc gọi:**
- Sale có đặt đúng câu hỏi không?
- Có lắng nghe khách không?
- Có giải quyết objection tốt không?
- Có CTA rõ ràng không?

### Bước 3: Trích xuất Action Items

```
✅ ACTION ITEMS SAU CUỘC GỌI
1. [Việc cần làm] - Deadline: [ngày] - Người phụ trách: [ai]
2. ...

📞 LỊCH FOLLOW-UP
- Thời gian: [ngày giờ]
- Nội dung cần chuẩn bị: [...]
- Tài liệu gửi trước: [...]
```

### Bước 4: Output

```
📞 BÁO CÁO PHÂN TÍCH CUỘC GỌI
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📅 Ngày: [date] | ⏱ Thời lượng: [xx phút]
👤 Khách hàng: [Tên]
📱 Sale: [Tên nhân viên]

📝 TÓM TẮT
[2-3 câu tóm tắt nội dung chính]

🎯 NHU CẦU KHÁCH HÀNG
- Pain point chính: [...]
- Sản phẩm quan tâm: [...]
- Budget: [...]
- Timeline: [...]

🧠 PHÂN TÍCH TÂM LÝ
- Mức độ quan tâm: [⭐⭐⭐⭐☆]
- Sẵn sàng mua: [Mức đánh giá]
- Mối lo ngại: [...]
- Yếu tố quyết định: [...]

💡 GỢI Ý CHIẾN LƯỢC
- Bước tiếp theo: [...]
- Cách xử lý objection: [...]
- Tài liệu nên gửi: [...]

✅ ACTION ITEMS
[Danh sách]
```

## Lưu ý

- Bảo mật file ghi âm - không chia sẻ ra ngoài
- Cần có sự đồng ý của khách khi ghi âm
- Phân tích khách quan, không thiên vị
