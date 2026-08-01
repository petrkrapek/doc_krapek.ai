# doc.krapek.ai

Statická dokumentační stránka Křápek.ai (GitHub Pages) — zásady zpracování osobních údajů.

## Nasazení

1. Vytvořte repozitář (např. `doc-krapek-ai`) a nahrajte obsah této složky:
   ```bash
   git init && git add . && git commit -m "Zásady zpracování osobních údajů"
   git branch -M main
   git remote add origin git@github.com:<uzivatel>/doc-krapek-ai.git
   git push -u origin main
   ```
2. V repozitáři: **Settings → Pages → Source: Deploy from a branch → main / (root)**.
3. Do pole **Custom domain** zadejte `doc.krapek.ai` (soubor `CNAME` už je v repu) a zaškrtněte **Enforce HTTPS**, jakmile se vydá certifikát.

## DNS (Cloudflare)

Přidejte záznam:

| Typ   | Název | Obsah                    | Proxy |
|-------|-------|--------------------------|-------|
| CNAME | doc   | `<uzivatel>.github.io`   | DNS only (šedý mráček) |

Pozn.: Při prvním ověření domény a vydání certifikátu nechte záznam v režimu **DNS only**; proxy lze případně zapnout až poté. Doporučené je také ověření domény v GitHub **Settings → Pages → Verified domains**, aby ji nemohl obsadit nikdo jiný.

## Struktura

- `index.html` — kompletní stránka (HTML + CSS v jednom souboru, bez buildů a závislostí)
- `CNAME` — vlastní doména pro GitHub Pages
- `.nojekyll` — vypnutí Jekyll zpracování
