---
name: sale-chatbot
description: Chatbot tự động trả lời khách hàng qua các kênh (Facebook Messenger, Zalo, website). Sử dụng khi cần thiết lập kịch bản chatbot, tạo câu trả lời tự động, xử lý FAQ, tư vấn sản phẩm tự động, chuyển tiếp cho sale khi cần. Trigger khi user yêu cầu tạo chatbot, thiết lập auto-reply, hoặc xây dựng kịch bản tư vấn tự động.
---

# Chatbot Tư vấn Khách hàng

## Quy trình

### Bước 1: Thu thập thông tin

Yêu cầu user cung cấp:
- Danh sách sản phẩm/dịch vụ (tên, mô tả, giá, USP)
- FAQ thường gặp (câu hỏi + câu trả lời mẫu)
- Quy trình bán hàng hiện tại
- Kênh triển khai (Messenger, Zalo OA, website)
- Giờ làm việc và chính sách phản hồi

### Bước 2: Xây dựng kịch bản (Flow)

Tạo cây kịch bản chatbot:

```
START → Chào hỏi + Hỏi nhu cầu
├── Tìm hiểu sản phẩm → Giới thiệu → Hỏi chi tiết → Báo giá → Chốt
├── Hỏi giá → Hỏi sản phẩm cụ thể → Báo giá → Chốt  
├── Khiếu nại/Hỗ trợ → Thu thập info → Chuyển cho support
├── Hợp tác → Thu thập info → Chuyển cho sale manager
└── Khác → Cố gắng hiểu → Chuyển cho nhân viên
```

### Bước 3: Viết nội dung từng node

Mỗi node cần:
1. **Message**: Tin nhắn gửi khách
2. **Quick replies**: Các lựa chọn nhanh
3. **Condition**: Điều kiện chuyển node tiếp
4. **Fallback**: Khi không hiểu ý khách

Ví dụ:
```
NODE: greeting
Message: "Chào bạn! 👋 Cảm ơn bạn đã liên hệ [Tên công ty].
Mình có thể hỗ trợ bạn về:
1️⃣ Tìm hiểu sản phẩm/dịch vụ
2️⃣ Báo giá
3️⃣ Hỗ trợ kỹ thuật
4️⃣ Hợp tác kinh doanh

Bạn chọn số mấy hoặc nhắn trực tiếp nhu cầu nhé!"

Quick replies: ["Sản phẩm", "Báo giá", "Hỗ trợ", "Hợp tác"]
```

### Bước 4: Tạo knowledge base

Tổng hợp thông tin thành file tham khảo:
- Catalog sản phẩm (tên, giá, mô tả, ưu điểm)
- FAQ database
- Chính sách (bảo hành, đổi trả, thanh toán)
- Script xử lý từ chối/khiếu nại

### Bước 5: Tạo quy tắc chuyển tiếp

Định nghĩa khi nào cần chuyển cho nhân viên thật:
- Khách hỏi vượt scope chatbot
- Khách yêu cầu gặp người thật
- Deal size lớn (> ngưỡng nhất định)
- Khiếu nại nghiêm trọng
- Sau 3 lần không hiểu ý khách

### Bước 6: Output

1. File kịch bản chatbot hoàn chỉnh (JSON/Markdown)
2. Knowledge base
3. Hướng dẫn deploy lên từng kênh
4. Bộ test cases để kiểm tra

## Lưu ý

- Tone chatbot phải nhất quán với brand voice
- Luôn có lựa chọn "gặp nhân viên"
- Response time < 3 giây
- Cá nhân hóa khi có thể (tên khách, lịch sử mua)
