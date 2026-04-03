---
name: sale-phan-tich-kh
description: Phân tích thông tin khách hàng từ nhiều nguồn (link Facebook, số điện thoại Zalo, thông tin công ty). Sử dụng khi cần research khách hàng tiềm năng, tìm hiểu thông tin trước khi liên hệ, đánh giá mức độ tiềm năng. Trigger khi user cung cấp link Facebook, SĐT, tên công ty và yêu cầu phân tích, tìm hiểu, hoặc research khách hàng.
---

# Phân tích Thông tin Khách hàng

## Quy trình

### Bước 1: Nhận thông tin đầu vào

User cung cấp một hoặc nhiều:
- Link Facebook cá nhân/fanpage
- Số điện thoại (Zalo)
- Tên công ty / MST
- Email
- Website

### Bước 2: Thu thập từ Facebook

Nếu có link Facebook:
1. Truy cập profile/fanpage public
2. Trích xuất:
   - Tên, ảnh đại diện
   - Vị trí công việc, công ty
   - Địa điểm sinh sống
   - Sở thích, hoạt động gần đây
   - Fanpage: ngành nghề, số follow, tần suất đăng bài, nội dung chính

### Bước 3: Thu thập từ thông tin công ty

Nếu có tên công ty hoặc MST:
1. Tìm kiếm trên web thông tin đăng ký kinh doanh
2. Trích xuất:
   - Tên đầy đủ, tên viết tắt
   - MST, ngày thành lập
   - Địa chỉ trụ sở
   - Ngành nghề kinh doanh
   - Người đại diện pháp luật
   - Vốn điều lệ
   - Website, fanpage chính thức

### Bước 4: Phân tích tổng hợp

Đánh giá khách hàng:

```
🎯 HỒ SƠ KHÁCH HÀNG
━━━━━━━━━━━━━━━━━━━

👤 THÔNG TIN CÁ NHÂN
- Họ tên: [...]
- Chức vụ: [...]
- Liên hệ: [SĐT] | [Email]
- Facebook: [Link]

🏢 THÔNG TIN CÔNG TY
- Tên: [...]
- MST: [...]
- Ngành: [...]
- Quy mô: [Nhỏ/Vừa/Lớn]
- Thành lập: [Năm]

📊 ĐÁNH GIÁ TIỀM NĂNG
- Mức độ phù hợp: [Cao/TB/Thấp] - [Lý do]
- Khả năng chi trả: [Ước đoán dựa trên quy mô]
- Nhu cầu dự đoán: [Dựa trên ngành nghề]
- Ưu tiên tiếp cận: [1-5 sao]

💡 GỢI Ý TIẾP CẬN
- Kênh liên hệ phù hợp: [Zalo/FB/Email/Gọi điện]
- Điểm chung/ice-breaker: [...]
- Sản phẩm phù hợp nhất: [...]
- Lưu ý khi tiếp cận: [...]
```

### Bước 5: Output

1. Hồ sơ khách hàng đầy đủ
2. Đánh giá mức độ tiềm năng
3. Gợi ý chiến lược tiếp cận

## Lưu ý

- Chỉ sử dụng thông tin công khai (public)
- Không thu thập dữ liệu nhạy cảm
- Thông tin công ty từ nguồn chính thống
- Đánh giá khách quan, không suy đoán quá mức
