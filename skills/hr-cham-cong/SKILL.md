---
name: hr-cham-cong
description: Quản lý chấm công và theo dõi vi phạm nội quy nhân viên. Sử dụng khi HR cần xử lý dữ liệu chấm công, tính công, thống kê đi trễ/về sớm/vắng, theo dõi vi phạm, tạo báo cáo chấm công tháng. Trigger khi user upload file chấm công, yêu cầu tổng hợp công, kiểm tra vi phạm, hoặc tạo báo cáo chấm công.
---

# Quản lý Chấm Công & Vi phạm

## Yêu cầu

- File chấm công (Excel/CSV từ máy chấm công hoặc hệ thống)
- Nội quy công ty (giờ làm việc, quy định chấm công)

## Quy trình

### Bước 1: Nhận và đọc dữ liệu chấm công

1. Nhận file chấm công từ user
2. Nhận dạng format:
   - Mã NV, Họ tên
   - Ngày, Giờ vào, Giờ ra
   - Loại (chính thức, OT, nghỉ phép, WFH)
3. Nhận thông tin nội quy:
   - Giờ làm: Thường 8:00-17:00 hoặc 8:30-17:30
   - Thời gian chấp nhận trễ: 5-15 phút
   - Số ngày phép/năm
   - Quy định OT

### Bước 2: Tính công

Với mỗi nhân viên, mỗi tháng tính:

```python
# Logic tính công cơ bản
cong_chinh_thuc = 0  # Ngày đi làm đủ
di_tre = 0           # Số lần đi trễ
ve_som = 0           # Số lần về sớm
vang_khong_phep = 0  # Vắng không phép
nghi_phep = 0        # Nghỉ có phép
cong_OT = 0          # Giờ OT

for ngay in du_lieu_thang:
    if ngay.gio_vao and ngay.gio_ra:
        if ngay.gio_vao <= gio_quy_dinh + buffer:
            cong_chinh_thuc += 1
        else:
            di_tre += 1
            cong_chinh_thuc += 1  # vẫn tính công nhưng ghi nhận trễ
        if ngay.gio_ra < gio_ket_thuc - buffer:
            ve_som += 1
    elif ngay.la_nghi_phep:
        nghi_phep += 1
    else:
        vang_khong_phep += 1
```

### Bước 3: Phát hiện vi phạm

Các loại vi phạm:
1. **Đi trễ**: > [X phút] so với giờ quy định
2. **Về sớm**: < [X phút] so với giờ kết thúc
3. **Vắng không phép**: Không chấm công + không có đơn
4. **Quên chấm công**: Chỉ có vào hoặc ra
5. **Đi trễ nhiều lần**: > [N lần/tháng]

Format vi phạm:
```
⚠️ DANH SÁCH VI PHẠM THÁNG [MM/YYYY]

🔴 VI PHẠM NGHIÊM TRỌNG
| NV | Họ tên | Vi phạm | Số lần | Chi tiết |
|----|--------|---------|--------|----------|
| NV001 | ... | Vắng không phép | 3 | 05/03, 12/03, 20/03 |

🟡 VI PHẠM NHẸ
| NV | Họ tên | Vi phạm | Số lần | Chi tiết |
|----|--------|---------|--------|----------|
| NV002 | ... | Đi trễ | 5 | 01/03 (15p), 03/03 (10p)... |
```

### Bước 4: Tạo báo cáo chấm công

```
📊 BÁO CÁO CHẤM CÔNG THÁNG [MM/YYYY]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📈 TỔNG QUAN
- Tổng NV: [N]
- Ngày công chuẩn: [N ngày]
- Tỷ lệ đi làm đầy đủ: [%]
- Tổng giờ OT: [N giờ]

📋 CHI TIẾT TỪNG NHÂN VIÊN
| Mã NV | Họ tên | Công | Trễ | Sớm | Phép | Vắng KP | OT (h) |
|-------|--------|------|-----|-----|------|---------|--------|
| NV001 | ...    | 22   | 1   | 0   | 0    | 0       | 8      |

📊 THỐNG KÊ PHÒNG BAN
| Phòng ban | Tỷ lệ đi đủ | Trễ TB | OT TB |
|-----------|-------------|--------|-------|
| Marketing | 95%         | 0.5    | 4h    |

⚠️ TÓM TẮT VI PHẠM
- Đi trễ: [N] lượt ([N] người)
- Về sớm: [N] lượt
- Vắng KP: [N] lượt
- Top NV vi phạm nhiều nhất: [...]
```

### Bước 5: Output

1. Bảng chấm công tổng hợp (Excel)
2. Báo cáo vi phạm
3. File chấm công chi tiết từng NV
4. Gợi ý xử lý vi phạm theo nội quy

## Lưu ý

- Kiểm tra dữ liệu bất thường (quên chấm công, chấm 2 lần)
- Đối chiếu với đơn xin phép/WFH/công tác
- Tính đúng ngày lễ, ngày nghỉ
- Bảo mật thông tin chấm công
