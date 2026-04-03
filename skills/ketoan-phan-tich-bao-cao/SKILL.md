---
name: ketoan-phan-tich-bao-cao
description: Nhận và phân tích báo cáo tài chính, thu chi, hàng hoá, xuất nhập tồn kho, công nợ khách hàng, kế hoạch đặt hàng. Sử dụng khi kế toán cần phân tích số liệu từ file Excel/CSV, tạo báo cáo tổng hợp, phát hiện bất thường, đưa ra nhận xét và đề xuất. Trigger khi user upload file báo cáo tài chính hoặc yêu cầu phân tích thu chi, tồn kho, công nợ.
---

# Phân tích Báo cáo Tài chính & Kế toán

## Loại báo cáo hỗ trợ

1. **Báo cáo thu chi**: Doanh thu, chi phí, lợi nhuận
2. **Báo cáo hàng hoá**: Danh mục, giá vốn, giá bán
3. **Xuất nhập tồn kho**: Nhập kho, xuất kho, tồn cuối kỳ
4. **Công nợ khách hàng**: Phải thu, phải trả, quá hạn
5. **Kế hoạch đặt hàng**: Dự báo nhu cầu, đề xuất đặt hàng
6. **Báo cáo tài chính tổng hợp**: Bảng cân đối, KQKD, lưu chuyển tiền tệ

## Quy trình

### Bước 1: Nhận và đọc file

1. Nhận file từ user (Excel, CSV, PDF)
2. Đọc và nhận dạng loại báo cáo
3. Kiểm tra tính đầy đủ của dữ liệu
4. Xác nhận kỳ báo cáo (tháng/quý/năm)

### Bước 2: Phân tích theo loại

**A. Thu chi:**
```
📊 PHÂN TÍCH THU CHI [Kỳ]
- Tổng doanh thu: [số] | Tăng/giảm: [%] so kỳ trước
- Tổng chi phí: [số] | Tăng/giảm: [%]
- Lợi nhuận gộp: [số] | Biên lợi nhuận: [%]
- Top 5 khoản thu lớn nhất
- Top 5 khoản chi lớn nhất
- Chi phí bất thường (nếu có)
```

**B. Xuất nhập tồn kho:**
```
📦 PHÂN TÍCH TỒN KHO [Kỳ]
- Tổng giá trị tồn kho: [số]
- Hàng tồn > 90 ngày (cảnh báo): [danh sách]
- Hàng sắp hết (cần nhập): [danh sách]
- Tốc độ quay vòng hàng tồn: [số ngày]
- Top hàng bán chạy nhất
- Top hàng tồn lâu nhất
```

**C. Công nợ:**
```
💰 PHÂN TÍCH CÔNG NỢ [Kỳ]
- Tổng phải thu: [số] | Trong hạn: [số] | Quá hạn: [số]
- Tổng phải trả: [số] | Trong hạn: [số] | Quá hạn: [số]
- Khách nợ quá hạn > 30 ngày: [danh sách]
- Khách nợ quá hạn > 90 ngày (cảnh báo đỏ): [danh sách]
- Tỷ lệ thu hồi nợ: [%]
```

**D. Kế hoạch đặt hàng:**
```
📋 ĐỀ XUẤT ĐẶT HÀNG [Kỳ tới]
- Dựa trên tốc độ bán + tồn kho hiện tại
- Hàng cần đặt ngay: [danh sách + số lượng]
- Hàng cần đặt trong 30 ngày: [danh sách]
- Tổng giá trị đặt hàng dự kiến: [số]
```

### Bước 3: Phát hiện bất thường

Kiểm tra tự động:
- Chênh lệch lớn so với kỳ trước (> 20%)
- Khoản mục âm bất thường
- Tỷ lệ chi phí/doanh thu vượt ngưỡng
- Hàng tồn quá lâu
- Công nợ quá hạn lớn

### Bước 4: Output

1. Báo cáo phân tích chi tiết
2. Biểu đồ/bảng tóm tắt (nếu có thể)
3. Danh sách cảnh báo và đề xuất
4. File tổng hợp để gửi qua Gamma (nếu cần)

## Lưu ý

- Số liệu phải chính xác tuyệt đối - double-check mọi phép tính
- Sử dụng đúng thuật ngữ kế toán Việt Nam
- Tuân thủ chuẩn mực kế toán VAS
- Bảo mật thông tin tài chính
