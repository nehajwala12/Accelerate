# CreditSwan — Restricted Document

A single-page, access-controlled diligence document. The report content is
AES-GCM encrypted inside `index.html` and only decrypts in the browser after the
correct access phrase is entered.

**Access phrase:** `creditswan2026`

## Deploy to Vercel

This is a static site — there is no build step.

1. Put `index.html` and `vercel.json` at the **root** of the repo (not inside a folder).
2. In Vercel: **Add New → Project → Import** this GitHub repo.
3. On the configuration screen:
   - **Framework Preset:** Other
   - **Build Command:** leave empty
   - **Output Directory:** `.` (or leave empty)
   - **Root Directory:** `./`
4. Click **Deploy**.

`vercel.json` already sets these, so the defaults should just work.

## Notes

- The unlock gate uses the browser WebCrypto API (`crypto.subtle`), which only
  runs over **https://** or **localhost**. Vercel serves over HTTPS, so the gate
  works once deployed. Opening the file directly from disk (`file://`) will not
  decrypt.
- The page loads three resources from CDNs at runtime: Google Fonts, Chart.js
  (cdnjs), and Mermaid (jsDelivr). These need network access to render fonts and
  charts; the text content still decrypts and displays without them.
