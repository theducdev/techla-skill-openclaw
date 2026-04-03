---
name: mkt-viet-bai-fb
description: Viết lại bài đăng Facebook từ link bài viết gốc. Sử dụng khi cần lấy nội dung từ một link Facebook (bài viết, fanpage, group), viết lại nội dung theo phong cách mới, tạo ảnh minh họa mới, và chuẩn bị bài đăng hoàn chỉnh. Trigger khi user cung cấp link Facebook và yêu cầu viết bài, rewrite, đăng lại, hoặc tham khảo nội dung.
---

# Viết bài từ link Facebook

## Quy trình

### Bước 1: Lấy nội dung từ link Facebook

1. Nhận link Facebook từ user
2. Dùng web fetch để truy cập link và trích xuất nội dung bài viết gốc (text, hình ảnh mô tả, hashtag, engagement)
3. Nếu không truy cập được (private post), yêu cầu user copy-paste nội dung

### Bước 2: Phân tích bài viết gốc

Phân tích các yếu tố:
- **Chủ đề chính**: Bài viết nói về gì?
- **Tone of voice**: Chuyên nghiệp, vui vẻ, cảm xúc, bán hàng?
- **CTA (Call to Action)**: Kêu gọi hành động gì?
- **Hashtag**: Các hashtag đang dùng
- **Điểm mạnh/yếu**: Gì hay, gì cần cải thiện?

### Bước 3: Viết lại nội dung

Tạo bài viết mới với các tùy chọn:

1. **Giữ nguyên ý chính** nhưng viết lại phong cách khác
2. **Thêm góc nhìn mới** dựa trên nội dung gốc
3. **Tối ưu cho engagement**: hook mạnh ở dòng đầu, chia đoạn ngắn, emoji phù hợp, CTA rõ ràng

Format bài viết chuẩn:
```
[HOOK - 1-2 dòng thu hút, viết HOA hoặc emoji bắt mắt]

[NỘI DUNG CHÍNH - 3-5 đoạn ngắn, mỗi đoạn 2-3 dòng]

[CTA - Kêu gọi hành động cụ thể]

[HASHTAG - 5-10 hashtag liên quan]
```

### Bước 4: Gợi ý ảnh minh họa

- Mô tả ý tưởng ảnh phù hợp với bài viết
- Nếu có skill tạo ảnh Gemini, gợi ý prompt để tạo ảnh
- Kích thước khuyến nghị: 1200x630 (link share), 1080x1080 (post vuông), 1080x1350 (post dọc)

### Bước 5: Output

Trả về cho user:
1. Bài viết hoàn chỉnh (copy-paste được)
2. Gợi ý ảnh
3. Thời điểm đăng tốt nhất (dựa trên loại nội dung)
4. Lưu file bài viết vào USB nếu user yêu cầu

## Lưu ý

- Luôn hỏi user về tone/style mong muốn nếu chưa rõ
- Không sao chép nguyên văn, luôn viết lại theo cách riêng
- Thêm giá trị mới cho bài viết (insight, data, góc nhìn)
- Tất cả output lưu vào USB theo yêu cầu
