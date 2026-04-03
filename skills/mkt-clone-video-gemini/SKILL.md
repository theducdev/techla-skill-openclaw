---
name: mkt-clone-video-gemini
description: Clone và tạo lại video bằng Gemini AI. Sử dụng khi cần phân tích video gốc, tạo script mới dựa trên video tham khảo, tạo video mới bằng Gemini. Trigger khi user yêu cầu clone video, tạo video tương tự, remake video, hoặc tạo video từ video mẫu.
---

# Clone Video bằng Gemini

## Yêu cầu

- Gemini API key (model hỗ trợ video: gemini-2.0-flash hoặc mới hơn)
- Video gốc để phân tích (file hoặc link)

## Quy trình

### Bước 1: Nhận video gốc

1. User cung cấp video (file path hoặc link)
2. Nếu là link YouTube/TikTok/Facebook: tải video về local
3. Kiểm tra định dạng và kích thước video

### Bước 2: Phân tích video gốc bằng Gemini

Sử dụng Gemini Vision API để phân tích:

```python
from google import genai

client = genai.Client()  # đọc GEMINI_API_KEY từ env

video_file = client.files.upload(file="video_goc.mp4")

response = client.models.generate_content(
    model='gemini-2.0-flash',
    contents=[
        video_file,
        """Phân tích chi tiết video này:
        1. Cấu trúc video (mở đầu, thân, kết)
        2. Script/lời thoại
        3. Phong cách hình ảnh (màu sắc, góc quay, transition)
        4. Nhạc nền và hiệu ứng âm thanh
        5. Text overlay và caption
        6. Thời lượng từng phần
        7. Hook đầu video
        8. CTA cuối video"""
    ]
)
```

### Bước 3: Tạo script mới

Dựa trên phân tích, tạo script mới:
- Giữ cấu trúc và flow tương tự
- Thay đổi nội dung cho phù hợp với thương hiệu/sản phẩm của user
- Tối ưu hook và CTA

Format script:
```
[00:00-00:03] HOOK: [Nội dung hook]
[00:03-00:10] INTRO: [Giới thiệu vấn đề]
[00:10-00:25] BODY: [Nội dung chính]
[00:25-00:30] CTA: [Kêu gọi hành động]

HƯỚNG DẪN HÌNH ẢNH:
- Cảnh 1: [Mô tả]
- Cảnh 2: [Mô tả]

ÂM THANH: [Gợi ý nhạc nền, voice-over]
TEXT OVERLAY: [Các dòng text cần hiện trên video]
```

### Bước 4: Tạo assets bằng Gemini

Sử dụng Gemini để tạo:
1. **Hình ảnh thumbnail**: Dùng Gemini image generation
2. **Storyboard**: Mô tả từng frame chính
3. **Caption/subtitle**: Tạo phụ đề

### Bước 5: Output

Trả về:
1. Phân tích video gốc
2. Script video mới hoàn chỉnh
3. Storyboard chi tiết
4. Gợi ý assets cần chuẩn bị
5. Lưu tất cả vào USB: `USB/mkt/video/[ten-video]/`

## Lưu ý

- Không sao chép 100% - luôn thêm yếu tố riêng
- Tôn trọng bản quyền nội dung gốc
- Video ngắn (15-60s) phù hợp nhất cho clone
- Hỏi user về sản phẩm/thương hiệu cần lồng ghép
