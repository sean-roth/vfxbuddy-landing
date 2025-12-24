# VFX Buddy Landing Page

> Marketing site for VFX Buddy - AI-powered rotoscoping for wedding videographers.

**Live:** https://vfxbuddy.ai / https://www.vfxbuddy.ai

---

## Architecture

This is a simple static landing page that:
1. Serves the marketing content at the root
2. Proxies `/app` and `/app/*` to the main React app (vfxbuddy.vercel.app)

```
vfxbuddy.ai/           → index.html (this repo)
vfxbuddy.ai/app        → vfxbuddy.vercel.app (main app repo)
vfxbuddy.ai/app/*      → vfxbuddy.vercel.app/* (main app repo)
```

---

## Structure

```
vfxbuddy-landing/
├── index.html          # Single-page landing (HTML + Tailwind CDN)
├── vercel.json         # Proxy config for /app routes
├── images/
│   ├── favicon.ico     # Amber film strip icon
│   └── VB_*.jpg/png    # Demo/preview images
└── README.md
```

---

## Key Sections (index.html)

- **Hero** - "Professional selections in minutes, not hours"
- **Problem Statement** - Why manual rotoscoping is a bottleneck
- **How It Works** - Upload → Describe → Get masks
- **Use Cases** - 6 preset cards (isolate couple, remove person, etc.)
- **Pricing** - 3 tiers (Starter $49, Pro $149, Studio $299)
- **CTA** - "When the client wants the impossible, call your buddy"

---

## Vercel Configuration

The `vercel.json` proxies app routes:

```json
{
  "rewrites": [
    {
      "source": "/app",
      "destination": "https://vfxbuddy.vercel.app/"
    },
    {
      "source": "/app/:path*",
      "destination": "https://vfxbuddy.vercel.app/:path*"
    }
  ]
}
```

---

## Design System

**Colors:**
- Background: `cream` (#FDF8F3)
- Primary: `amber` (#F59E0B)
- Header: `header-dark` (#1a1a1a)

**Typography:**
- Tailwind defaults via CDN
- Custom config in `<script>` tag

---

## Related Repository

**Main App:** https://github.com/sean-roth/vfxbuddy

See `CLAUDE_HANDOFF.md` in the main repo for full project context.

---

## Deployment

Push to main → Vercel auto-deploys

**Custom Domain Setup:**
1. Add `vfxbuddy.ai` in Vercel project settings
2. Configure DNS at registrar:
   - A record: 76.76.21.21
   - CNAME www: cname.vercel-dns.com

---

## Local Development

Just open `index.html` in a browser. No build step needed.

For the /app proxy to work locally, you'd need to run a local server or just test on Vercel preview deployments.

---

## Known Issues

- **Favicon not displaying** - File exists at `images/favicon.ico` and is referenced in HTML, but may have caching/serving issues. Try hard refresh or check Network tab.

---

*Last updated: December 24, 2025*
