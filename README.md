# BARBELITH ✦ K-VOID — Tuning Console

A fast, on-brand landing page that funnels TikTok → streaming → (soon) 24/7 radio.

## Tech Stack

- **Static HTML/CSS/JS** (no build process)
- **Tailwind CDN** for styling
- **Cloudflare Web Analytics** for tracking
- **TikTok Pixel** for conversion tracking
- **GitHub Pages** for hosting

## Project Structure

```
/
├── index.html          # Main landing page
├── config.json         # Content configuration (non-devs can edit)
├── CNAME              # GitHub Pages custom domain (tune.kvoid.net)
├── robots.txt         # SEO configuration
├── sitemap.xml        # Site structure for search engines
├── site.webmanifest   # PWA configuration
├── favicon.svg        # Site favicon
├── og-image.svg       # OpenGraph image template
├── og.jpg.README      # Instructions for creating og.jpg
└── favicon.ico.README # Instructions for creating favicon.ico
```

## Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/kvoid-tune.git
   cd kvoid-tune
   ```

2. **Update config.json** with your actual links and content
   - Replace placeholder URLs with real streaming platform links
   - Add your analytics tokens
   - Customize the branding if needed

3. **Create the required images**
   - Generate `og.jpg` (1200×630) using the template in `og-image.svg`
   - Create `favicon.ico` using the specifications in `favicon.ico.README`

4. **Deploy to GitHub Pages**
   - Push to your GitHub repository
   - Enable Pages in repository settings
   - Set source to main branch
   - Add the custom domain in CNAME

## Configuration

All content is managed through `config.json`:

- **Brand**: Title, subtitle, and glyph
- **Featured Track**: Currently highlighted song with streaming links
- **Artist Pages**: Links to Spotify, Apple Music, YouTube, Bandcamp
- **Radio**: 24/7 station configuration and status
- **Social**: Instagram, X (Twitter), and email links
- **Analytics**: Cloudflare and TikTok Pixel tokens
- **Theme**: Color scheme customization

## Features

### ✅ Completed
- [x] Static HTML/CSS/JS with no build step
- [x] Tailwind CDN integration
- [x] Config-driven content management
- [x] UTM parameter injection for all outbound links
- [x] Cloudflare Web Analytics integration
- [x] TikTok Pixel integration with event tracking
- [x] SEO optimization (meta tags, OpenGraph, Twitter Cards)
- [x] Accessibility features (ARIA, keyboard navigation, WCAG AA contrast)
- [x] Mobile-first responsive design
- [x] PWA-ready with web manifest
- [x] Radio status functionality with live badge
- [x] GitHub Pages hosting setup

### 🚀 Future Enhancements
- [ ] Audio player for radio (when live)
- [ ] Releases section for singles/EPs
- [ ] Email capture integration
- [ ] Advanced radio controls

## Performance

- **Target**: <200ms TTFB on desktop
- **Lighthouse**: Performance ≥95, Accessibility ≥95, SEO ≥90
- **Bundle Size**: Minimal (HTML + CSS + JS only)

## Analytics & Tracking

### UTM Parameters
All outbound links automatically receive:
```
?utm_source=tiktok&utm_medium=bio&utm_campaign=launch
```

### TikTok Pixel Events
- `ViewContent` on page load
- `ClickButton` on outbound link clicks

### Cloudflare Analytics
Page view tracking when token is configured.

## Deployment Checklist

- [ ] Update all placeholder URLs in `config.json`
- [ ] Add Cloudflare Analytics token
- [ ] Configure TikTok Pixel ID (if using)
- [ ] Generate and add `og.jpg` (1200×630)
- [ ] Create and add `favicon.ico`
- [ ] Test all links function with UTM parameters
- [ ] Verify mobile responsiveness
- [ ] Run Lighthouse audit
- [ ] Enable GitHub Pages with custom domain `tune.kvoid.net`
- [ ] Configure DNS in Cloudflare (CNAME flattening, redirects)

## Development

### Local Testing
```bash
# Serve locally (requires Python)
python -m http.server 8000

# Or use any static file server
npx serve .
```

### Updating Content
1. Edit `config.json`
2. Test changes locally
3. Commit and push to deploy

## Security

- Content Security Policy ready
- All external scripts from trusted CDNs
- Analytics tokens stored in config (not hardcoded)

## Contributing

This project is designed to be maintainable by non-developers through `config.json` updates.

For code changes:
1. Fork the repository
2. Make changes
3. Test thoroughly
4. Submit a pull request

## License

© 2024 BARBELITH ✦ K-VOID

*"Every man and woman is a star."*
