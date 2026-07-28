# After each new desktop export from Claude Design

Your site is a single `index.html` exported from Claude Design. Anything added
*outside* Claude Design gets overwritten when you upload a fresh export. Two
buckets:

- **Mobile styling** → lives in `deploy/mobile.css` (a separate file). It is
  **never** overwritten by a re-export. You only need to keep it *linked*.
- **SEO / social tags, favicon, privacy fix** → these MUST live in the HTML
  `<head>`/`<body>`, so a re-export wipes them. Re-paste the block below.

Vercel serves the site from the **`deploy/`** folder, so put the new export
there as `deploy/index.html`.

---

## Do these 2 things after uploading a new `index.html`

### 1. Re-add the head block
Paste this inside `<head>` (near the top, before `<script src="./support.js">`):

```html
<title>LeadRefinery — The revenue engine for business lending</title>
<meta name="description" content="Purpose-built AI voice agents for business lending. LeadRefinery works the pipeline your floor never reaches — aged files, declines, renewals, cold inbound — and delivers submission-ready packages, not phone lists.">
<link rel="canonical" href="https://leadrefinery.ai/">
<meta name="theme-color" content="#FBF8F2">
<meta name="robots" content="index, follow">
<link rel="icon" href="/favicon.svg" type="image/svg+xml">

<!-- Open Graph -->
<meta property="og:type" content="website">
<meta property="og:site_name" content="LeadRefinery">
<meta property="og:title" content="LeadRefinery — The revenue engine for business lending">
<meta property="og:description" content="Purpose-built AI voice agents that work every record you own — aged files, declines, renewals, cold inbound — and hand your closers submission-ready packages, not phone lists.">
<meta property="og:url" content="https://leadrefinery.ai/">
<meta property="og:image" content="https://leadrefinery.ai/og-image.png">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">

<!-- Twitter -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="LeadRefinery — The revenue engine for business lending">
<meta name="twitter:description" content="Purpose-built AI voice agents that work every record you own — and hand your closers submission-ready packages, not phone lists.">
<meta name="twitter:image" content="https://leadrefinery.ai/og-image.png">

<!-- Mobile adaptations live in mobile.css so desktop re-exports don't wipe them -->
<link rel="stylesheet" href="mobile.css">
```

Also set the opening tag to `<html lang="en">` (helps SEO/accessibility).

### 2. That's it for mobile
As long as `<link rel="stylesheet" href="mobile.css">` (last line above) is
present, all mobile behavior comes back automatically. Don't edit
`deploy/mobile.css` unless you want to change mobile styling.

---

## Easier option
Instead of doing the above by hand, just tell me you've uploaded a new export
(or paste it to me) and I'll re-apply the head block + confirm the mobile link
and push it — one step, nothing to remember.

## What mobile.css currently handles (≤760px)
- Hero headline shrinks so the call-to-action sits above the fold
- The 4-column comparison table becomes stacked per-row cards (no sideways swipe)
- The console disposition table collapses from 4 cramped columns to a clean 2×2
