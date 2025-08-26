# Cloudflare Setup for kvoid.net

## 1) DNS (CNAME flattening)

Zone: kvoid.net

- @ → CNAME → username.github.io (Proxy ON)
- www → CNAME → kvoid.net (Proxy ON)
- tune → CNAME → username.github.io (Proxy ON)
- radio → CNAME → your-stream-host.example.com (Proxy ON or OFF depending on host)
- (optional) img, cdn → your asset host

Zone: kvoid.online

- @ → A → 192.0.2.1 (dummy) (Proxy ON) — or skip and use Redirect Rules only

## 2) Redirect Rules (ordered top→bottom)

1. Always use HTTPS
   - If Hostname matches `kvoid.net`
   - Redirect to `https://kvoid.net/$1` (301)

2. www → apex
   - If Hostname equals `www.kvoid.net`
   - Redirect to `https://kvoid.net/$1` (301)

3. kvoid.online → kvoid.net
   - If Hostname matches `kvoid.online` or `www.kvoid.online`
   - Redirect to `https://kvoid.net/$1` (301)

Alternatively, use a single list-based rule in the new Redirect Rules product.

## 3) Security Headers (Transform Rule → HTTP Response headers)

Add the following headers on `kvoid.net`:

- Strict-Transport-Security: `max-age=31536000; includeSubDomains; preload`
- Content-Security-Policy:
  ```
  default-src 'self'; img-src 'self' data: https:; style-src 'self' 'unsafe-inline';
  script-src 'self' https://static.cloudflareinsights.com https://analytics.tiktok.com;
  connect-src 'self'; font-src 'self' data:; frame-ancestors 'none'
  ```
- X-Content-Type-Options: `nosniff`
- X-Frame-Options: `DENY`
- Referrer-Policy: `strict-origin-when-cross-origin`
- Permissions-Policy: `camera=(), microphone=(), geolocation=()`

If you self-host CSS and skip pixels, you can set `script-src 'self'` only.

## 4) Email Routing

Create forwards for `hello@kvoid.net`, `press@kvoid.net`, `booking@kvoid.net`.

Suggested DNS records:
- SPF (TXT @): `v=spf1 include:_spf.google.com include:spf.improvmx.com ~all`
- DMARC (TXT _dmarc): `v=DMARC1; p=quarantine; rua=mailto:dmarc@kvoid.net; fo=1; pct=100; sp=quarantine`
- DKIM: add keys provided by your sender (Google/SES/etc.)

## 5) Analytics

- Cloudflare Web Analytics on `kvoid.net` (token configured in `config.json`)
- TikTok Pixel only on `tune.kvoid.net` (scoped in `index.html`)

## 6) Canonical + SEO

- Canonical: `https://kvoid.net/` for apex, `https://tune.kvoid.net/` for console
- robots.txt allows all, sitemap at `https://kvoid.net/sitemap.xml`
- Verify `kvoid.net` with Google/Bing via DNS

