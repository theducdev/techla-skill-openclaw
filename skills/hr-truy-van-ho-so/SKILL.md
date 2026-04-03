---
name: hr-truy-van-ho-so
description: Truy vấn và quản lý hồ sơ nhân sự. Sử dụng khi HR cần tra cứu thông tin nhân viên, tìm kiếm theo tiêu chí (phòng ban, vị trí, ngày vào), tổng hợp thống kê nhân sự, hoặc cập nhật hồ sơ. Trigger khi user hỏi về thông tin nhân viên, danh sách nhân sự, hoặc yêu cầu tra cứu hồ sơ.
---

# Truy vấn Hồ sơ Nhân sự

## Yêu cầu

- File dữ liệu nhân sự (Excel/CSV/Google Sheets)
- Hoặc hệ thống HRMS có API

## Quy trình

### Bước 1: Kết nối dữ liệu

1. Nhận file dữ liệu nhân sự từ user
2. Đọc và nhận dạng các cột dữ liệu:
   - Mã NV, Họ tên, Ngày sinh, CCCD/CMND
   - Phòng ban, Vị trí, Cấp bậc
   - Ngày vào làm, Loại hợp đồng, Ngày hết HĐ
   - SĐT, Email, Địa chỉ
   - Lương cơ bản, Phụ cấp
   - Trạng thái (đang làm, nghỉ phép, đã nghỉ)

### Bước 2: Xử lý truy vấn

Các loại truy vấn hỗ trợ:

**Tra cứu cá nhân:**
- "Thông tin nhân viên Nguyễn Văn A"
- "Ai có mã NV là NV001?"
- "Nhân viên có SĐT 0901234567"

**Tra cứu theo tiêu chí:**
- "Danh sách nhân viên phòng Marketing"
- "Ai vào công ty năm 2024?"
- "Nhân viên có HĐ sắp hết hạn trong 3 tháng tới"
- "Danh sách nhân viên thử việc"

**Thống kê:**
- "Tổng số nhân viên hiện tại"
- "Phân bố nhân sự theo phòng ban"
- "Tỷ lệ nam/nữ"
- "Thâm niên trung bình"
- "Tỷ lệ turnover"

### Bước 3: Trả kết quả

**Tra cứu cá nhân:**
```
👤 HỒ SƠ NHÂN VIÊN
━━━━━━━━━━━━━━━━━
Mã NV: [...]
Họ tên: [...]
Ngày sinh: [...] | Giới tính: [...]
CCCD: [...]
Phòng ban: [...] | Vị trí: [...]
Ngày vào: [...] | Thâm niên: [... năm ... tháng]
HĐ: [...] | Hết hạn: [...]
SĐT: [...] | Email: [...]
Trạng thái: [Đang làm việc]
```

**Danh sách:**
```
📋 DANH SÁCH NHÂN VIÊN [Tiêu chí]
Tổng: [N] người

| STT | Mã NV | Họ tên | Phòng ban | Vị trí | Ngày vào |
|-----|-------|--------|-----------|--------|----------|
| 1   | ...   | ...    | ...       | ...    | ...      |
```

**Thống kê:**
```
📊 THỐNG KÊ NHÂN SỰ
Tổng nhân viên: [N]
- Chính thức: [N] | Thử việc: [N] | Part-time: [N]

Theo phòng ban:
- Marketing: [N] ([%])
- Sales: [N] ([%])
- Kế toán: [N] ([%])
- ...

Giới tính: Nam [N] ([%]) | Nữ [N] ([%])
Tuổi TB: [...] | Thâm niên TB: [...]
```

### Bước 4: Cảnh báo tự động

Kiểm tra và báo:
- HĐ sắp hết hạn (trong 30/60/90 ngày)
- Nhân viên sinh nhật tháng này
- Nhân viên đến hạn đánh giá
- Nhân viên thử việc sắp hết hạn

## Lưu ý

- Bảo mật thông tin nhân sự (đặc biệt lương, CCCD)
- Chỉ trả về thông tin user có quyền xem
- Không tiết lộ thông tin nhạy cảm khi không cần thiết
