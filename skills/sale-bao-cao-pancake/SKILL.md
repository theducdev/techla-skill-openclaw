---
name: sale-bao-cao-pancake
description: Báo cáo chăm sóc khách hàng qua Pancake Platform API. Sử dụng khi cần theo dõi tiến độ rep khách, thống kê bỏ lỡ khách, quản lý conversations/messages, xem statistics, quản lý tags và customers trên Pancake CRM. Trigger khi user yêu cầu báo cáo Pancake, kiểm tra inbox, thống kê CSKH, hoặc quản lý hội thoại khách hàng.
---

# pancake-skills

## Muc tieu

Skill nay cung cap kha nang tuong tac voi Pancake Platform API - nen tang quan ly ban hang da kenh. Ho tro day du cac thao tac:

- **Pages**: Liet ke pages, tao page access token
- **Conversations**: Quan ly hoi thoai, gan tags, assign staff, danh dau read/unread
- **Messages**: Lay lich su tin nhan, gui tin nhan (inbox, reply comment, private reply)
- **Customers**: Quan ly khach hang, them/sua/xoa notes
- **Statistics**: Thong ke ads, engagement, page, tags, users
- **Tags**: Liet ke tags cua page
- **Posts**: Liet ke bai viet
- **Users**: Quan ly staff, cau hinh round robin
- **Upload**: Upload media content
- **Chat Plugin**: Gui tin nhan qua chat plugin

## Thiet lap moi truong (bat buoc)

**User API** (endpoints `/api/v1/pages`):
- `USER_ACCESS_TOKEN`: Token ca nhan, lay tu **Account -> Personal Settings**. Co hieu luc 90 ngay.

**Page API** (endpoints `/api/public_api/v1` va `/api/public_api/v2`):
- `PAGE_ACCESS_TOKEN`: Token cua page, lay tu **Settings -> Tools**. Khong het han tru khi xoa/renew.

**Tuy chon**:
- `PANCAKE_BASE_URL`: Mac dinh `https://pages.fm`
- `CONFIRM_WRITE`: Set `YES` de cho phep thao tac ghi (POST/PUT/DELETE)

## Cach goi nhanh

Cac vi du ben duoi dung curl truc tiep. Thay `PAGE_ACCESS_TOKEN` va `page_id` theo thong tin thuc te.

### Vi du GET

```bash
# Liet ke pages (User API)
export USER_ACCESS_TOKEN="***"
bash scripts/pancake.sh pages-list

# Liet ke conversations cua page (Page API)
export PAGE_ACCESS_TOKEN="***"
bash scripts/pancake.sh conversations-list 123456789

# Loc conversations theo tags va type
bash scripts/pancake.sh conversations-list 123456789 "?tags=1,2&type=INBOX"

# Lay tin nhan trong conversation
bash scripts/pancake.sh messages-list 123456789 conv_abc123

# Liet ke tags
bash scripts/pancake.sh tags-list 123456789

# Liet ke staff
bash scripts/pancake.sh users-list 123456789

# Thong ke page (SINCE/UNTIL la Unix timestamp)
bash scripts/pancake.sh stats-page 123456789 1704067200 1706745600
```

### Vi du WRITE

```bash
export PAGE_ACCESS_TOKEN="***"
export CONFIRM_WRITE=YES

# Gui tin nhan inbox
echo '{"action":"reply_inbox","message":"Xin chao!"}' | \
  bash scripts/pancake.sh messages-send 123456789 conv_abc123

# Gui tin nhan voi attachment (dung content_ids tu upload API)
echo '{"action":"reply_inbox","content_ids":["xxx"]}' | \
  bash scripts/pancake.sh messages-send 123456789 conv_abc123

# Reply comment
echo '{"action":"reply_comment","message_id":"comment123","message":"Cam on ban!"}' | \
  bash scripts/pancake.sh messages-send 123456789 conv_abc123

# Private reply tu comment
echo '{"action":"private_replies","post_id":"post123","message_id":"comment123","message":"Inbox nhe!"}' | \
  bash scripts/pancake.sh messages-send 123456789 conv_abc123

# Them tag vao conversation
echo '{"action":"add","tag_id":"123"}' | \
  bash scripts/pancake.sh conversations-tag 123456789 conv_abc123

# Go tag khoi conversation
echo '{"action":"remove","tag_id":"123"}' | \
  bash scripts/pancake.sh conversations-tag 123456789 conv_abc123

# Assign staff vao conversation
echo '{"assignee_ids":["user-uuid-1","user-uuid-2"]}' | \
  bash scripts/pancake.sh conversations-assign 123456789 conv_abc123

# Danh dau conversation da doc
bash scripts/pancake.sh conversations-read 123456789 conv_abc123

# Cap nhat thong tin khach hang
echo '{"changes":{"name":"Nguyen Van A","gender":"male","birthday":"1990-01-15"}}' | \
  bash scripts/pancake.sh customers-update 123456789 customer_uuid

# Them ghi chu cho khach hang
echo '{"message":"Khach hang VIP, uu tien ho tro"}' | \
  bash scripts/pancake.sh customers-add-note 123456789 customer_uuid

# Upload file
bash scripts/pancake.sh upload 123456789 /path/to/image.jpg

# Cap nhat round robin users
echo '{"inbox":["user-uuid-1"],"comment":["user-uuid-2"]}' | \
  bash scripts/pancake.sh users-round-robin 123456789
```

## Guardrails

- Khong ghi du lieu khi chua set `CONFIRM_WRITE=YES`
- Voi thao tac ghi: luon chay 1 lenh GET truoc de xac nhan ID/shape du lieu
- Khong luu access token vao repo
- **QUAN TRONG**: Khi gui message, `message` va `content_ids` la **MUTUALLY EXCLUSIVE** - khong duoc gui ca hai cung luc

## Endpoint thuoc skill nay

### User API (`https://pages.fm/api/v1`)
- `GET /pages` - Liet ke pages
- `POST /pages/{page_id}/generate_page_access_token` - Tao page access token

### Page API v2 (`https://pages.fm/api/public_api/v2`)
- `GET /pages/{page_id}/conversations` - Liet ke conversations

### Page API v1 (`https://pages.fm/api/public_api/v1`)

**Conversations:**
- `POST /pages/{page_id}/conversations/{conversation_id}/tags` - Them/xoa tag
- `POST /pages/{page_id}/conversations/{conversation_id}/assign` - Assign staff
- `POST /pages/{page_id}/conversations/{conversation_id}/read` - Danh dau da doc
- `POST /pages/{page_id}/conversations/{conversation_id}/unread` - Danh dau chua doc

**Messages:**
- `GET /pages/{page_id}/conversations/{conversation_id}/messages` - Lay tin nhan
- `POST /pages/{page_id}/conversations/{conversation_id}/messages` - Gui tin nhan

**Customers:**
- `GET /pages/{page_id}/page_customers` - Liet ke khach hang
- `PUT /pages/{page_id}/page_customers/{page_customer_id}` - Cap nhat khach hang
- `POST /pages/{page_id}/page_customers/{page_customer_id}/notes` - Them ghi chu
- `PUT /pages/{page_id}/page_customers/{page_customer_id}/notes` - Sua ghi chu
- `DELETE /pages/{page_id}/page_customers/{page_customer_id}/notes` - Xoa ghi chu

**Statistics:**
- `GET /pages/{page_id}/statistics/pages_campaigns` - Thong ke chien dich quang cao
- `GET /pages/{page_id}/statistics/ads` - Thong ke quang cao
- `GET /pages/{page_id}/statistics/customer_engagements` - Thong ke tuong tac
- `GET /pages/{page_id}/statistics/pages` - Thong ke page
- `GET /pages/{page_id}/statistics/tags` - Thong ke tags
- `GET /pages/{page_id}/statistics/users` - Thong ke users

**Other:**
- `GET /pages/{page_id}/tags` - Liet ke tags
- `GET /pages/{page_id}/posts` - Liet ke bai viet
- `GET /pages/{page_id}/users` - Liet ke users
- `POST /pages/{page_id}/round_robin_users` - Cap nhat round robin
- `GET /pages/{page_id}/sip_call_logs` - Lay lich su cuoc goi
- `GET /pages/{page_id}/export_data` - Export du lieu
- `POST /pages/{page_id}/upload_contents` - Upload media

### Chat Plugin (`https://pages.fm/api/v1`)
- `POST /pke_chat_plugin/messages` - Gui tin nhan qua chat plugin
- `GET /pke_chat_plugin/messages` - Lay tin nhan chat plugin

## Tham chieu

- Official docs: https://docs.pages.fm/
- Developer portal: https://developer.pancake.biz/
- API base URL: https://pages.fm
