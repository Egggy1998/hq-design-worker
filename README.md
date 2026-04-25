# HQ Design Cloudflare Worker

Webhook relay worker cho hệ thống marketing.

## 🌐 Giới thiệu

Worker nhận request từ OpenClaw và forward đến n8n webhook, đảm bảo 100% uptime.

## 🚀 Deploy từ GitHub

1. Vào https://dash.cloudflare.com → Workers & Pages
2. "Create a Worker" → "Deploy from GitHub"
3. Connect repo: `Egggy1998/hq-design-worker`
4. Done!

## 🔧 Cấu hình (set trên Cloudflare Dashboard)

| Variable | Value |
|----------|-------|
| `N8N_WEBHOOK_URL` | URL n8n instance của bạn |
| `N8N_WEBHOOK_ID` | Webhook ID từ n8n workflow |
| `BASEROW_TABLE_ID` | Baserow table ID |

## 🔐 Secrets (set riêng - KHÔNG push lên git)

```bash
wrangler secret put BASEROW_TOKEN
# Nhập: Baserow API token của bạn
```

## 📡 API

```
POST https://YOUR_SUBDOMAIN.workers.dev
Content-Type: application/json

{
  "row_id": 297,
  "baserow_row_id": 297,
  "content": "Content...",
  "product_image_url": "https://...",
  "product_name": "Product Name"
}
```

## 📚 Tham khảo

- https://developers.cloudflare.com/workers/
- https://developers.cloudflare.com/workers/wrangler/
