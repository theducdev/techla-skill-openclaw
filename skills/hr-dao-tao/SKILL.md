---
name: hr-dao-tao
description: Hệ thống đào tạo nhân viên theo vị trí dựa trên file đào tạo và mô tả công việc (JD). Sử dụng khi HR cần tạo lộ trình đào tạo, gợi ý tài liệu training, theo dõi tiến độ đào tạo nhân viên mới, hoặc cập nhật chương trình đào tạo theo vị trí. Trigger khi user yêu cầu đào tạo, onboarding nhân viên mới, tạo training plan, hoặc cập nhật tài liệu đào tạo.
---

# Hệ thống Đào tạo theo Vị trí

## Yêu cầu

- File mô tả công việc (JD) theo vị trí
- File/tài liệu đào tạo hiện có
- Danh sách nhân viên cần đào tạo

## Quy trình

### Bước 1: Thiết lập hệ thống đào tạo

Yêu cầu user cung cấp:
1. **JD các vị trí**: File mô tả công việc
2. **Tài liệu đào tạo có sẵn**: File training, video, SOP
3. **Quy trình onboarding hiện tại** (nếu có)

### Bước 2: Phân tích JD và tạo lộ trình

Với mỗi vị trí, phân tích JD để xác định:

**A. Kiến thức cần có:**
- Kiến thức chuyên môn
- Kỹ năng mềm
- Tool/phần mềm cần sử dụng
- Quy trình nội bộ

**B. Tạo lộ trình đào tạo:**

```
📚 LỘ TRÌNH ĐÀO TẠO: [Vị trí]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📅 TUẦN 1: ONBOARDING CƠ BẢN
□ Giới thiệu công ty, văn hóa, nội quy
□ Setup workspace (email, tools, tài khoản)
□ Giới thiệu team và các phòng ban liên quan
□ Tài liệu: [link/file]
□ Mentor: [Tên người hướng dẫn]

📅 TUẦN 2-3: ĐÀO TẠO CHUYÊN MÔN
□ [Module 1]: [Nội dung] - Tài liệu: [file]
□ [Module 2]: [Nội dung] - Tài liệu: [file]
□ Thực hành: [Bài tập/task thực tế]
□ Kiểm tra: [Hình thức đánh giá]

📅 TUẦN 4: THỰC HÀNH VÀ ĐÁNH GIÁ
□ Làm task thực tế dưới sự hướng dẫn
□ Review với mentor
□ Đánh giá cuối onboarding
□ Feedback 2 chiều

📅 THÁNG 2-3: NÂNG CAO
□ [Module nâng cao 1]
□ [Module nâng cao 2]
□ Cross-training với team khác
□ Đánh giá thử việc
```

### Bước 3: Tạo nội dung đào tạo

Với mỗi module:
1. **Mục tiêu học**: Sau module, NV phải biết/làm được gì
2. **Nội dung**: Kiến thức cốt lõi
3. **Tài liệu**: File/link tham khảo
4. **Bài tập**: Thực hành + tiêu chí đánh giá
5. **Thời lượng**: Ước tính thời gian

### Bước 4: Theo dõi tiến độ

```
📊 TIẾN ĐỘ ĐÀO TẠO
Nhân viên: [Tên] | Vị trí: [...]
Ngày bắt đầu: [...] | Mentor: [...]

| Module | Trạng thái | Điểm | Ghi chú |
|--------|-----------|------|---------|
| Onboarding | ✅ Hoàn thành | 8/10 | Tốt |
| Chuyên môn 1 | 🔄 Đang học | - | Cần hỗ trợ thêm |
| Chuyên môn 2 | ⏳ Chưa bắt đầu | - | - |

Tiến độ tổng: [60%] ████████░░░░
```

### Bước 5: Output

1. Lộ trình đào tạo theo vị trí (file markdown/excel)
2. Checklist onboarding cho từng NV
3. Bảng theo dõi tiến độ
4. Template đánh giá sau đào tạo

## Vị trí mẫu

Các vị trí thường có trong công ty:
- **Marketing**: Content, Ads, Design, Social Media
- **Sale**: Tư vấn, Account Manager, Sale Admin
- **Kế toán**: Kế toán tổng hợp, Kế toán thuế, Thủ quỹ
- **HR**: Tuyển dụng, C&B, Đào tạo
- **IT**: Developer, QA, Support

## Lưu ý

- Cá nhân hóa lộ trình theo kinh nghiệm NV (fresher vs experienced)
- Review và cập nhật tài liệu đào tạo định kỳ (6 tháng/lần)
- Thu thập feedback NV sau đào tạo để cải thiện
