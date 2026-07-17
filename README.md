# Rivalista.io — static site (migrated off Squarespace)

Plain HTML/CSS clone of the live Squarespace site. No build step, no framework.

## Scope (locked)
- Homepage + Bill Tsapalas + Rakesh David bios only
- No Duke, no Ben, no merchandise store (killed, not migrated)
- 1:1 clone of the live design

## Status: DONE
- All Squarespace CDN assets downloaded at full resolution into `assets/img/`
  (17 images/gifs + favicon), verified against the live pages
- Sh*t-Talking Santa background video pulled from Squarespace's video CDN and
  remuxed to `assets/video/santa-opening.mp4` (1356x1080, 1:19, with audio) —
  it would otherwise die with the subscription
- The ATTI presentation video is a YouTube embed (`kggogvC1zd4`) — YouTube-hosted,
  survives cancellation; rebuilt as a click-to-play poster (no YouTube JS until click)
- Typeface: the live site uses Adobe "Tablet Gothic Condensed" licensed through
  Squarespace (dies with the plan). Replaced with self-hosted **Barlow Condensed**
  (OFL license, `assets/fonts/`), the closest free match incl. 800 italic
- Desktop layout mirrors the Squarespace fluid grid: block positions/sizes were
  measured on the live site (1265px reference canvas) and verified to the pixel;
  font sizes use the exact vw formulas recovered from the live CSS
  (h1 `calc(16px + 5.4vw)`, h2 `+4.2vw`, h3 `+3vw`, h4 `+1.8vw`, body `+0.12vw`)
- Below 900px the layout stacks (equivalent of Squarespace's separate mobile layout)
- Footer year set to ©2026 (live still says ©2025); team section intentionally
  trimmed to Bill + Rakesh

## Local preview
```
python3 -m http.server 4173
# open http://127.0.0.1:4173/
```

## Deploy (free, ~10 min)
1. Repo: https://github.com/btsapalas/rivalista-site
2. Connect the repo to Cloudflare Pages (pages.cloudflare.com) — free tier,
   no build step needed since this is plain HTML/CSS
3. In Cloudflare Pages, add custom domain: rivalista.io + www.rivalista.io
4. At GoDaddy (your registrar), update DNS per Cloudflare's instructions —
   typically an A record + CNAME, or switch nameservers to Cloudflare's if
   you want Cloudflare managing DNS entirely (also free, adds CDN + SSL)
5. Wait for DNS propagation (up to 24-48hrs, usually faster), confirm
   rivalista.io loads the new site
6. Cancel Squarespace subscription (after confirming you've exported the
   merchandise product data and asset library, in case you want it later)
