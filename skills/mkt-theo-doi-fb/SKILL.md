---
name: mkt-theo-doi-fb
description: Theo dõi hội nhóm và tin tức trên Facebook. Sử dụng khi cần monitor các group Facebook, fanpage, theo dõi trending topics, thu thập tin tức ngành, phân tích xu hướng thảo luận. Trigger khi user yêu cầu theo dõi, cập nhật tin tức, tổng hợp thông tin từ Facebook groups hoặc pages.
---

# Theo dõi hội nhóm & tin tức Facebook

## Quy trình

### Bước 1: Thiết lập danh sách theo dõi

Yêu cầu user cung cấp:
- Danh sách group/fanpage cần theo dõi (link hoặc tên)
- Lĩnh vực/ngành quan tâm
- Từ khóa cần tracking
- Tần suất báo cáo mong muốn (hàng ngày, hàng tuần)

### Bước 2: Thu thập thông tin

Với mỗi group/fanpage:
1. Truy cập link và lấy các bài viết mới nhất
2. Trích xuất: tiêu đề, nội dung tóm tắt, lượt tương tác, bình luận nổi bật
3. Lọc theo từ khóa user quan tâm
4. Đánh giá mức độ viral (engagement rate)

### Bước 3: Phân tích xu hướng

- **Trending topics**: Chủ đề đang được bàn luận nhiều nhất
- **Sentiment**: Tích cực/tiêu cực/trung lập
- **Key insights**: Thông tin quan trọng, thay đổi ngành
- **Cơ hội content**: Chủ đề có thể khai thác cho kênh của mình

### Bước 4: Tạo báo cáo

Format báo cáo:
```
📊 BÁO CÁO THEO DÕI FACEBOOK
Ngày: [date]
Nguồn: [danh sách group/page]

🔥 TOP TRENDING
1. [Chủ đề] - [Tóm tắt] - [Engagement]
2. ...

📰 TIN TỨC NGÀNH
- [Tin 1]: [Tóm tắt + link]
- [Tin 2]: [Tóm tắt + link]

💡 CƠ HỘI CONTENT
- [Gợi ý 1]: [Lý do + cách triển khai]
- [Gợi ý 2]: ...

⚠️ LƯU Ý
- [Thông tin quan trọng cần action]
```

### Bước 5: Lưu trữ

- Xuất báo cáo dạng markdown hoặc text
- Lưu vào USB theo cấu trúc: `USB/mkt/theo-doi-fb/[ngay].md`

## Lưu ý

- Chỉ theo dõi thông tin public, không thu thập thông tin cá nhân
- Ưu tiên chất lượng hơn số lượng - lọc thông tin nhiễu
- Gắn link gốc để user có thể verify
