---
name: sale-bao-gia
description: Tạo báo giá chuyên nghiệp theo file mẫu báo giá của công ty. Sử dụng khi cần lập báo giá cho khách hàng dựa trên template có sẵn, tính toán giá, chiết khấu, thuế VAT, và xuất file báo giá hoàn chỉnh. Trigger khi user yêu cầu báo giá, lập bảng giá, tạo quotation, hoặc gửi giá cho khách.
---

# Báo giá theo File Mẫu

## Yêu cầu

- File báo giá mẫu (Excel/Word/PDF) từ user
- Thông tin sản phẩm/dịch vụ và bảng giá

## Quy trình

### Bước 1: Đọc file mẫu báo giá

1. Yêu cầu user cung cấp file báo giá mẫu
2. Phân tích cấu trúc mẫu:
   - Header (logo, thông tin công ty, số báo giá)
   - Thông tin khách hàng
   - Bảng chi tiết sản phẩm/dịch vụ
   - Điều khoản (thanh toán, bảo hành, hiệu lực)
   - Footer (chữ ký, con dấu)

### Bước 2: Thu thập thông tin báo giá

Hỏi user:
- **Khách hàng**: Tên công ty, người liên hệ, địa chỉ, MST
- **Sản phẩm/dịch vụ**: Tên, số lượng, đơn giá
- **Chiết khấu**: % hoặc số tiền (nếu có)
- **Thuế VAT**: 8% hoặc 10% (tùy sản phẩm)
- **Điều khoản đặc biệt**: Thời gian giao hàng, thanh toán, bảo hành

### Bước 3: Tính toán

```
Thành tiền = Số lượng × Đơn giá
Chiết khấu = Thành tiền × % chiết khấu
Tiền trước thuế = Thành tiền - Chiết khấu
VAT = Tiền trước thuế × % VAT
Tổng cộng = Tiền trước thuế + VAT
```

Đọc số tiền bằng chữ (VND):
- Ví dụ: 15.500.000 → "Mười lăm triệu năm trăm nghìn đồng"

### Bước 4: Điền vào mẫu

Tạo file báo giá hoàn chỉnh theo đúng format mẫu:
- Số báo giá: `BG-[YYYYMMDD]-[STT]`
- Ngày báo giá: Ngày hiện tại
- Hiệu lực: 15-30 ngày (tùy chính sách)
- Điền đầy đủ thông tin đã thu thập

### Bước 5: Output

1. File báo giá hoàn chỉnh (Excel hoặc theo format mẫu)
2. Bản tóm tắt báo giá (để gửi nhanh qua chat/email)
3. Gợi ý email gửi kèm báo giá

## Format tóm tắt nhanh

```
📋 BÁO GIÁ [Mã BG]
Khách hàng: [Tên]
Ngày: [DD/MM/YYYY]

Sản phẩm/Dịch vụ:
1. [Tên SP] × [SL] = [Thành tiền]
2. ...

Chiết khấu: [Số tiền]
Trước thuế: [Số tiền]
VAT (10%): [Số tiền]
TỔNG CỘNG: [Số tiền]
(Bằng chữ: [Số tiền bằng chữ])

Hiệu lực: [Số ngày] ngày
```

## Lưu ý

- Luôn double-check phép tính
- Giá phải khớp với bảng giá công ty
- Chiết khấu phải trong phạm vi cho phép
- File output cùng format với file mẫu input
