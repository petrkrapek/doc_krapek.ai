# doc.krapek.ai

Statický web s právními dokumenty Křápek.ai (Netlify) — zásady zpracování osobních údajů a všeobecné obchodní podmínky.

## Struktura

- `index.html` — rozcestník právních dokumentů
- `zasady-zpracovani-osobnich-udaju/index.html` — zásady zpracování osobních údajů
- `obchodni-podminky/index.html` — všeobecné obchodní podmínky
- `assets/style.css` — sdílené styly (bez buildů a závislostí)
- `netlify.toml` — publish adresář, bezpečnostní hlavičky, cache pro assets

## Nasazení na Netlify

**Varianta A — drag & drop:** app.netlify.com → Sites → „Add new site → Deploy manually" → přetáhnout celou složku.

**Varianta B — přes Git (doporučeno):**
1. Push do repozitáře (GitHub/GitLab).
2. Netlify → „Add new site → Import an existing project" → vybrat repozitář.
3. Build command nechat prázdný, publish directory `.` (bere se z `netlify.toml`).

## Vlastní doména

1. Site settings → Domain management → „Add a domain" → `doc.krapek.ai`.
2. V Cloudflare DNS přidat záznam:

   | Typ   | Název | Obsah                       | Proxy |
   |-------|-------|-----------------------------|-------|
   | CNAME | doc   | `<nazev-site>.netlify.app`  | DNS only (šedý mráček) |

3. Počkat na vydání Let's Encrypt certifikátu (Domain management → HTTPS), poté ověřit, že vše běží přes HTTPS.

Pozn.: Nechte záznam v režimu **DNS only** — Netlify má vlastní CDN i certifikáty; dvojité proxy přes Cloudflare komplikuje vydání certifikátu a nic nepřidává.
