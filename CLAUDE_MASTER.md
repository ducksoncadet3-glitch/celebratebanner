# CelebrateBanner — Master Platform Guide

## Who I am
- **Founder & CEO:** Duckson Cadet
- **Email:** ducksoncadet3@gmail.com | info@celebratebanner.com
- **Phone:** +1 772-834-9060
- **Business:** CDN4 LLC (DBA CelebrateBanner)
- **Address:** 211 Old Okeechobee Road, Bay 2 #1058, West Palm Beach, FL 33401

---

## All Active Projects & CLAUDE.md Locations

| Project | Launch Date | CLAUDE.md |
|---------|-------------|-----------|
| BannerCraft (core platform) | Live | `bannercraft/CLAUDE.md` |
| America250 | July 4, 2026 | `america-250/CLAUDE.md` |
| Haitian Flag Day | May 18, 2026 | `haitian-flag-day/CLAUDE.md` |
| World Cup 2026 | June 12, 2026 | `worldcup2026/CLAUDE.md` |

> **Always read the relevant project CLAUDE.md before starting work.**

---

## Platform Overview

CelebrateBanner is a **direct-to-consumer custom photo banner builder** that lets users:
1. Pick a milestone theme
2. Upload up to 50 photos, select a hero image
3. Customize text, colors, and size
4. Pay via Stripe → receive print-ready files by email or printed banner by mail

---

## Full Infrastructure

| Service | Purpose | Provider |
|---------|---------|----------|
| Marketing site | celebratebanner.com | Webflow |
| Builder app | app.celebratebanner.com | Vercel |
| API / backend | api.celebratebanner.com | Railway |
| Admin panel | admin.celebratebanner.com | Vercel |
| Source code | All repos | GitHub: ducksoncadet3-glitch |
| DNS | All domains | Namecheap |
| Photo uploads | Cloudinary (djqxuvkk0) | Cloudinary |
| Final renders | S3 + CloudFront | AWS |
| Payments | Stripe Checkout | Stripe |
| Print fulfillment | Blind dropship | Printmoz (Dom Smith, dom@printmoz.com) |
| Email | SendGrid | Twilio SendGrid |
| AI API | Claude API | Anthropic Console ("CelebrateBanner" key) |
| Queue | Bull + Redis | Railway |

---

## Deploy Workflow (for every project)
```
1. Edit files in Claude Code or locally
2. Open GitHub web editor → ducksoncadet3-glitch/<repo>
3. Navigate to file → Edit → Select All → Paste → Commit
4. Vercel auto-deploys (frontend) / Railway auto-deploys (backend)
```

> ⚠️ Always deliver **complete, ready-to-paste files** — never partial snippets or diffs.

---

## Shared Output Specs (non-negotiable across ALL themes)
- Sizes: **24×36 in** ($49) and **18×24 in** ($39)
- Resolution: **300 DPI**
- Color mode: **CMYK**
- Formats: **PDF** (print-ready + bleed) **+ JPG** (digital)
- Bleed: **0.125 in** on all sides
- Safe margin: **0.25 in** from trim edge

---

## Pricing (DO NOT CHANGE without Printmoz confirmation)
| Product | Price |
|---------|-------|
| Digital Download | $19 |
| Printed Banner (24×36) | $49 |
| Printed Banner (18×24) | $39 |

Printmoz contact: **Dom Smith — dom@printmoz.com**
Florida Resale Certificate (DR-13) submitted. Awaiting reseller pricing confirmation.

---

## Platform-Wide Pending Items
- [ ] Fix live site footer — still shows Fort Pierce and © 2025 (should be West Palm Beach, © 2026)
- [ ] Confirm Printmoz reseller pricing → update pricing across all assets
- [ ] Add ANTHROPIC_API_KEY to Railway Variables (key name: "CelebrateBanner")
- [ ] Add ALLOWED_ORIGINS to Railway Variables
- [ ] Deploy orderAgent.js after Printmoz partnership confirmed
- [ ] Upload updated index.html with America250 THEMES patch to builder

---

## Campaign Calendar

| Date | Campaign | Status |
|------|----------|--------|
| Now | BannerCraft core platform | 🔄 Active |
| May 1, 2026 | Haitian Flag Day pre-launch ads | ⏳ |
| **May 18, 2026** | **Haitian Flag Day** | ⏳ |
| June 1, 2026 | World Cup urgency push | ⏳ |
| **June 12, 2026** | **World Cup 2026 opens** | ⏳ |
| **July 4, 2026** | **America250 main launch** | ⏳ |
| July 19, 2026 | World Cup ends | ⏳ |

---

## Global Rules for Claude Code

1. **Never change pricing** without Printmoz reseller confirmation
2. **Always deliver complete files** — no partial snippets or diffs
3. **No licensed logos, crests, or player likenesses** in any template
4. **CMYK + 300 DPI** is non-negotiable for all print outputs
5. **themeConfig.json is the single source of truth** — always update it first when adding themes
6. **Stripe webhook** must use raw body — never move webhook route below `express.json()`
7. **Test before committing** — run `npm run dev` and verify frontend + backend start cleanly
8. **Bilingual (French + Haitian Creole)** required for all Haitian Flag Day assets
9. **Deploy via GitHub web editor** — Duckson's preferred workflow
10. **Read the project-specific CLAUDE.md** before starting any work on that campaign

---

## Environment Variables Quick Reference

### Railway (Backend)
```
PORT=4000
STRIPE_SECRET_KEY=sk_live_...
STRIPE_WEBHOOK_SECRET=whsec_...
FRONTEND_URL=https://app.celebratebanner.com
CLOUDINARY_CLOUD_NAME=djqxuvkk0
CLOUDINARY_API_KEY=...
CLOUDINARY_API_SECRET=...
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_KEY=...
AWS_REGION=us-east-1
S3_BUCKET=bannercraft-renders
REDIS_URL=redis://...
SENDGRID_API_KEY=SG....
EMAIL_FROM=orders@celebratebanner.com
ANTHROPIC_API_KEY=...
ALLOWED_ORIGINS=https://app.celebratebanner.com,https://celebratebanner.com
ADMIN_SECRET=...
```

### Vercel (Frontend)
```
VITE_API_URL=https://api.celebratebanner.com
VITE_STRIPE_PUBLISHABLE_KEY=pk_live_...
VITE_GA4_MEASUREMENT_ID=G-...
VITE_META_PIXEL_ID=...
```

---

## Quick Start Commands
```bash
# Install all dependencies
npm run install:all

# Start everything (frontend + backend)
npm run dev

# Backend only
cd backend && npm run dev

# Frontend only
cd frontend && npm run dev

# Render worker
cd backend && npm run worker
```
