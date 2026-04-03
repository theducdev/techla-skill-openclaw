# techla-skill-openclaw

Bo skill OpenClaw cho cac phong ban cua Techla. Tong cong 21 skill cho 4 phong ban.

## Cau truc

```
skills/
├── MKT (8 skill)
│   ├── mkt-viet-bai-fb/         Viet bai tu link Facebook
│   ├── mkt-theo-doi-fb/         Theo doi hoi nhom, tin tuc FB
│   ├── mkt-chay-qc-fb/          Chay quang cao Facebook (Meta Ads)
│   ├── mkt-goi-y-chu-de/        Goi y chu de content cho kenh
│   ├── mkt-bao-cao-gamma/       Tao bao cao bang Gamma.app
│   ├── mkt-tao-anh-gemini/      Tao anh bang Google Gemini
│   ├── mkt-clone-video-gemini/  Clone video bang Gemini
│   └── mkt-quang-cao-google/    Chay quang cao Google Ads
│
├── Sale (7 skill)
│   ├── sale-chatbot/            Chatbot tu van khach hang
│   ├── sale-bao-gia/            Bao gia theo file mau
│   ├── sale-phan-tich-kh/       Phan tich thong tin khach hang
│   ├── sale-bao-cao-excel/      Tao bao cao tu file Excel
│   ├── sale-gui-gmail/          Gui bao cao qua Gmail
│   ├── sale-phan-tich-ghi-am/   Phan tich ghi am cuoc goi KH
│   └── sale-bao-cao-pancake/    Bao cao CSKH tren Pancake CRM
│
├── Ke toan (3 skill)
│   ├── ketoan-phan-tich-bao-cao/  Phan tich bao cao tai chinh
│   ├── ketoan-cap-nhat-luat/      Cap nhat thong tu, nghi dinh thue
│   └── ketoan-bao-cao-gamma/      Gui bao cao tai chinh bang Gamma
│
└── HR (3 skill)
    ├── hr-truy-van-ho-so/       Truy van ho so nhan su
    ├── hr-dao-tao/              He thong dao tao theo vi tri
    └── hr-cham-cong/            Quan ly cham cong, vi pham
```

## Nguon goc skill

| Nguon | So luong | Ghi chu |
|-------|---------|---------|
| Tu tao | 12 | Tuy chinh cho Techla |
| Tai ve & chinh sua | 9 | Tu OpenClaw, GitHub repos |

### Skill tai ve tu:
- [BrianRWagner/ai-marketing-claude-code-skills](https://github.com/BrianRWagner/ai-marketing-claude-code-skills) - content-idea-generator
- [OpenClaudia/openclaudia-skills](https://github.com/OpenClaudia/openclaudia-skills) - google-ads
- [zubair-trabzada/ai-marketing-claude](https://github.com/zubair-trabzada/ai-marketing-claude) - market-ads (FB)
- [guinacio/claude-image-gen](https://github.com/guinacio/claude-image-gen) - image-generation (Gemini)
- [OpenClaw Registry](https://github.com/VoltAgent/awesome-openclaw-skills) - gamma, gmail
- [Anthropic Official](https://github.com/anthropics/skills) - xlsx
- [suminhthanh/pancake-skills](https://github.com/suminhthanh/pancake-skills) - Pancake CRM API

## File mau (assets)

Cac skill can input deu co san file mau trong thu muc `assets/`:

| Skill | File mau |
|-------|---------|
| sale-bao-gia | `mau-bao-gia.xlsx` - Template bao gia cong ty |
| sale-bao-cao-excel | `du-lieu-ban-hang-mau.xlsx` - 50 dong du lieu ban hang |
| sale-chatbot | `san-pham-faq.xlsx` - San pham + FAQ + Chinh sach |
| ketoan-phan-tich-bao-cao | `bao-cao-tai-chinh-mau.xlsx` - Thu chi, Ton kho, Cong no |
| hr-truy-van-ho-so | `ho-so-nhan-su.xlsx` - 25 nhan vien 5 phong ban |
| hr-dao-tao | `jd-va-dao-tao.xlsx` - JD 6 vi tri + 8 module dao tao |
| hr-cham-cong | `cham-cong-thang3-2026.xlsx` - Du lieu cham cong + Noi quy |

## API Keys can thiet

| Skill | Key/Tool |
|-------|---------|
| mkt-bao-cao-gamma, ketoan-bao-cao-gamma | `GAMMA_API_KEY` |
| mkt-tao-anh-gemini, mkt-clone-video-gemini | `GEMINI_API_KEY` |
| sale-gui-gmail | `gog` CLI + `GMAIL_ACCOUNT` |
| sale-bao-cao-pancake | Pancake `PAGE_ACCESS_TOKEN` |
