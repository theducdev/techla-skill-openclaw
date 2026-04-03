---
name: ketoan-cap-nhat-luat
description: Tự động cập nhật và tra cứu thông tư, nghị định mới về thuế và kế toán Việt Nam. Sử dụng khi kế toán cần biết quy định mới nhất, tra cứu luật thuế, kiểm tra thay đổi chính sách thuế GTGT/TNDN/TNCN, hoặc cần tóm tắt văn bản pháp luật. Trigger khi user hỏi về luật thuế, thông tư, nghị định, hoặc yêu cầu cập nhật quy định kế toán mới.
---

# Cập nhật Thông tư Nghị định Thuế & Kế toán

## Nguồn thông tin chính thức

1. **Tổng cục Thuế**: https://www.gdt.gov.vn
2. **Bộ Tài chính**: https://www.mof.gov.vn
3. **Thư viện pháp luật**: https://thuvienphapluat.vn
4. **Hệ thống văn bản QPPL**: https://vanban.chinhphu.vn

## Quy trình

### Bước 1: Xác định phạm vi tra cứu

Hỏi user cần tra cứu về:
- **Loại thuế**: GTGT, TNDN, TNCN, thuế XNK, thuế TTĐB
- **Loại văn bản**: Thông tư, Nghị định, Công văn, Quyết định
- **Lĩnh vực cụ thể**: Hóa đơn điện tử, khấu trừ thuế, kê khai, hoàn thuế
- **Thời gian**: Mới nhất hoặc thời điểm cụ thể

### Bước 2: Tìm kiếm văn bản

1. Tìm trên web các văn bản mới nhất liên quan
2. Trích xuất thông tin chính:
   - Số hiệu văn bản
   - Ngày ban hành / Ngày hiệu lực
   - Cơ quan ban hành
   - Nội dung chính
   - Văn bản thay thế/sửa đổi (nếu có)

### Bước 3: Tóm tắt và phân tích

Format:
```
📜 CẬP NHẬT VĂN BẢN PHÁP LUẬT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📄 [SỐ HIỆU VĂN BẢN]
Ban hành: [Ngày] | Hiệu lực: [Ngày]
Cơ quan: [Tên]

📌 NỘI DUNG CHÍNH
[Tóm tắt 3-5 điểm quan trọng nhất]

🔄 THAY ĐỔI SO VỚI QUY ĐỊNH CŨ
- Trước: [Quy định cũ]
- Sau: [Quy định mới]
- Ảnh hưởng: [Tác động đến doanh nghiệp]

⚠️ LƯU Ý QUAN TRỌNG
- Deadline áp dụng: [Ngày]
- Đối tượng áp dụng: [...]
- Điều khoản chuyển tiếp: [...]

✅ VIỆC CẦN LÀM
1. [Action item 1]
2. [Action item 2]
```

### Bước 4: Các chủ đề thường cần cập nhật

**Thuế GTGT:**
- Thuế suất (0%, 5%, 8%, 10%)
- Điều kiện khấu trừ thuế đầu vào
- Hoàn thuế GTGT
- Hóa đơn điện tử

**Thuế TNDN:**
- Thuế suất (20%, ưu đãi)
- Chi phí được trừ / không được trừ
- Ưu đãi thuế theo vùng/ngành
- Chuyển lỗ

**Thuế TNCN:**
- Biểu thuế lũy tiến
- Giảm trừ gia cảnh
- Thu nhập miễn thuế
- Quyết toán thuế TNCN

**Kế toán:**
- Chuẩn mực kế toán VAS
- Chế độ kế toán doanh nghiệp
- Báo cáo tài chính
- Hóa đơn điện tử

### Bước 5: Output

1. Bản tóm tắt văn bản pháp luật
2. So sánh thay đổi (cũ vs mới)
3. Action items cho kế toán
4. Lưu vào thư mục tham khảo

## Lưu ý

- Luôn ghi rõ nguồn và số hiệu văn bản
- Kiểm tra ngày hiệu lực trước khi áp dụng
- Khuyến nghị tham vấn chuyên gia thuế cho trường hợp phức tạp
- Thông tin chỉ mang tính tham khảo, không thay thế tư vấn pháp lý
