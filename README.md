# Relax & Cruz Spa website

Static site: plain HTML, CSS and one small script. No build step. Booking and payments stay on Square.

## Files

```
index.html        Homepage
css/styles.css    Shared styles for every page (colors, type, layout)
js/main.js        Mobile menu and the price finder (prices live here)
images/           Logo, white logo, favicon
_redirects        Old URLs to new pages (Cloudflare Pages / Netlify)
_headers          Security and caching headers
robots.txt
sitemap.xml
```

## Deploy (Cloudflare Pages)

1. Create a GitHub repo and push this folder to it.
2. In Cloudflare, go to Workers & Pages, then Create, then Pages, then Connect to Git, and pick the repo.
3. Build settings: framework preset **None**, build command **empty**, output directory **/**.
4. Deploy. You get a `*.pages.dev` preview address. Test everything there first.
5. Every push to the main branch redeploys automatically.

Do not use GitHub Pages. It can't do real 301 redirects, and the old URLs need them.

## Before launch

- [ ] Hero photo: replace the placeholder in `index.html` (search `TODO`) with `/images/hero.jpg`
- [ ] Portrait of Crystal: replace the placeholder with `/images/crystal.jpg`
- [ ] Before and after photos: underarm and chin, plus the session counts
- [ ] Crystal's bio in her own words
- [ ] Credentials: license number, laser certification, supervising physician. Fill in or delete each line. Never launch with brackets.
- [ ] "Read the reviews" link: swap in her Google Business Profile reviews link
- [ ] Cherry: link it to her Cherry application page
- [ ] Square: free consult listed first, and prices that match `js/main.js`
- [ ] Build the service pages linked from the homepage (list below), or remove those links
- [ ] Crawl the old site and add any missing old URLs to `_redirects`
- [ ] Test every Book button and the phone link on a real phone

## Pages still to build

All use `css/styles.css`. Each page needs its own title and description.

| URL | Page |
| --- | --- |
| /laser-hair-removal | Laser (keeps its current URL) |
| /electrolysis | Electrolysis (old /permanent-hair-removal redirects here) |
| /ingrown-hair | Ingrown hairs and razor bumps |
| /laser-for-men | Beard line and razor bumps |
| /facials-and-peels | Facials and peels |
| /lymphatic-massage | Lymphatic massage after surgery |
| /massage | Swedish massage (old /massages redirects here) |
| /body-contouring | Body contouring (keeps its current URL) |
| /shop | Post-op recovery and laser aftercare products |
| /contact | Address, hours, map (old /contact-us redirects here) |

Add each page to `sitemap.xml` as it goes live.

## Updating prices

Open `js/main.js`. Prices are in `TIERS`, one line per size. Areas and their $499 eligibility notes are in `AREAS`. The homepage shows Underarms by default, so if Small prices change, also update the matching numbers in the price finder in `index.html`.

## Going live

1. In Cloudflare Pages, add the custom domain `www.relaxandcruzspa.com` (and the bare domain).
2. Update DNS where the domain is registered. If it was bought through Square, confirm you can edit DNS there or transfer it out first.
3. After the switch, update the website and booking links on her Google Business Profile, Yelp, Facebook and Instagram.
4. Submit `sitemap.xml` in Google Search Console.
