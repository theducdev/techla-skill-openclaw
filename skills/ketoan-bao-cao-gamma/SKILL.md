---
name: ketoan-bao-cao-gamma
description: Tạo và gửi báo cáo phân tích kế toán/tài chính bằng Gamma (gamma.app). Sử dụng khi kế toán cần trình bày báo cáo tài chính dưới dạng slide/presentation đẹp mắt qua Gamma, tạo dashboard tài chính, hoặc gửi báo cáo cho ban lãnh đạo. Trigger khi user yêu cầu tạo báo cáo Gamma, trình bày số liệu tài chính dạng slide, hoặc gửi báo cáo kế toán cho sếp.
---

# Báo cáo Tài chính bằng Gamma

## Yêu cầu

- Tài khoản Gamma (gamma.app)
- Gamma API key hoặc Gamma MCP server
- Dữ liệu tài chính đã phân tích

## Quy trình

### Bước 1: Chuẩn bị dữ liệu

Từ kết quả phân tích báo cáo (skill `ketoan-phan-tich-bao-cao`), tổng hợp:
- Số liệu chính (doanh thu, chi phí, lợi nhuận)
- So sánh kỳ trước
- Biểu đồ và bảng
- Cảnh báo và đề xuất

### Bước 2: Tạo outline báo cáo

Structure slide Gamma:
```
Slide 1: Trang bìa
- Tiêu đề: "Báo cáo Tài chính [Kỳ]"
- Đơn vị: [Tên công ty]
- Ngày: [Date]

Slide 2: Tổng quan
- Doanh thu | Chi phí | Lợi nhuận
- So sánh với kỳ trước (%)
- Highlight: Điểm nổi bật

Slide 3: Chi tiết Doanh thu
- Doanh thu theo sản phẩm/dịch vụ
- Doanh thu theo kênh
- Trend tăng trưởng

Slide 4: Chi tiết Chi phí
- Chi phí theo loại
- Chi phí bất thường
- Tỷ lệ chi phí/doanh thu

Slide 5: Tồn kho & Hàng hoá
- Giá trị tồn kho
- Hàng tồn lâu (cảnh báo)
- Đề xuất đặt hàng

Slide 6: Công nợ
- Phải thu / Phải trả
- Công nợ quá hạn
- Kế hoạch thu hồi

Slide 7: Đề xuất & Kế hoạch
- Action items
- Dự báo kỳ tới
- Kiến nghị

Slide 8: Q&A
```

### Bước 3: Tạo trên Gamma

Sử dụng Gamma API/MCP:
1. Tạo presentation mới với outline trên
2. Chọn template phù hợp (professional/corporate)
3. Điền dữ liệu vào từng slide
4. Cài đặt: Tiếng Việt, tone chuyên nghiệp

### Bước 4: Output

1. Link Gamma presentation
2. File PDF export (nếu cần)
3. Bản tóm tắt kèm link để gửi email

## Template gợi ý cho từng loại báo cáo

- **Báo cáo tháng**: 5-7 slides, focus số liệu tháng + so sánh
- **Báo cáo quý**: 8-12 slides, có trend 3 tháng + dự báo
- **Báo cáo năm**: 12-15 slides, tổng kết + kế hoạch năm sau

## Lưu ý

- Số liệu trên slide phải khớp với file gốc
- Dùng biểu đồ thay vì bảng số dài
- Highlight bằng màu: xanh (tốt), đỏ (cảnh báo), vàng (lưu ý)
- Bảo mật - chỉ share cho người có quyền
