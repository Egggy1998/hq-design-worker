# 3D Vietnam Cloudflare Worker

Webhook relay worker cho hệ thống marketing 3D Vietnam.

## 🌐 Giới thiệu

Worker nhận request từ OpenClaw và forward đến n8n webhook, đảm bảo 100% uptime.

## 🚀 Deploy

### 1. Cài Wrangler CLI

```bash
npm install -g wrangler
wrangler login
```

### 2. Deploy

```bash
wrangler deploy
```

### 3. Set Environment Variables

Trên Cloudflare Dashboard:
1. Workers & Pages → `3d-vietnam-worker`
2. Settings → Variables
3. Add:

| Variable | Value |
|----------|-------|
| `N8N_WEBHOOK_URL` | `https://jqqpar.ezn8n.com` |
| `N8N_WEBHOOK_ID` | `c662501d-1d03-48c3-9bc2-4ad0e8e2b2a2` |
| `BASEROW_TABLE_ID` | `916632` |

### 4. Set Secret

```bash
wrangler secret put BASEROW_TOKEN
# Nhập: k3h0ecJo2awlsDTc2cctP1H5EhNMs4yo
```

### 5. Lấy URL

```bash
wrangler subdomain
# Kết quả: https://3d-vietnam-worker.YOUR_SUBDOMAIN.workers.dev
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

## 🔧 Tuỳ chỉnh

Chỉnh sửa `wrangler.toml` để đổi subdomain:

```toml
name = "your-worker-name"
```

## 📚 Tham khảo

- https://developers.cloudflare.com/workers/
- https://developers.cloudflare.com/workers/wrangler/
