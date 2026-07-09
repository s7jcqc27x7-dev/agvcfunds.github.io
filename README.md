# AGVC Website v2

Static site — no build step. Push to GitHub, connect to Netlify.

## Images to place in /images/

From your folder, add these files exactly as named:
- agvc-logo-white.png      ← nav logo + favicon
- agvc-logo-black.png      ← (optional, unused in current build)
- map-asia-hub.png         ← hero background + presence section map
- justin-tso.jpg           ← team spotlight
- aaisha-bhuiyan.jpg       ← advisor card
- doug-nissinoff.jpg       ← advisor card
- donny-siu.jpg            ← advisor card
- rima-patel.jpg           ← advisor card
- elena-liapounova.jpeg    ← advisor card
- sergei-petukhov.jpeg     ← advisor card
- eric-verdin.jpeg         ← advisor card
- editorial-scmp.png       ← landing service panel logo strip
- editorial-nature.png     ← landing service panel logo strip
- editorial-tvm.png        ← landing service panel logo strip
- editorial-worldbank.png  ← landing service panel logo strip

All images use onerror fallbacks — missing images degrade gracefully.

## Advisor roles to update

- Doug Nissinoff → update title/org when confirmed
- Donny Siu → update title/org when confirmed
- Rima Patel → update title/org when confirmed
- Elena Liapounova → update title/org when confirmed
- Sergei Petukhov → update title/org when confirmed
- Eric Verdin → update title/org when confirmed (CEO, Buck Institute for Research on Aging?)

## Deploy
1. Push folder to GitHub repo
2. Netlify → Import from Git → publish directory: `.` → build command: (blank)
3. Assign agvcfunds.com domain
