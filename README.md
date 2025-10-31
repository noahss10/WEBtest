# West East Bridge — Static Site (GitHub Pages)

This repo hosts a simple static website built with plain **HTML + CSS** (no build tools).
It’s ready for **GitHub Pages**.

## Project structure

```
root/
├─ index.html      # main page
└─ styles.css      # styles for the site
```

> The page references `styles.css` from the same folder. Keep both files in the repo root unless you intentionally change paths.

---

## Quick start (local)

Open `index.html` in a browser, or run a tiny local server:

```bash
# Option A: Python 3
python3 -m http.server 5500

# Option B: Node (if installed)
npx serve . -l 5500
```

Then visit <http://localhost:5500>.

---

## Deploy to GitHub Pages (recommended: main branch / root)

1. Create a **new GitHub repository** (public or private is fine).
2. Add and push the two files:
   ```bash
   git init
   git add index.html styles.css
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-repo>.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**.
4. Under **Build and deployment**:
   - **Source:** *Deploy from a branch*
   - **Branch:** `main` / **root**
5. Save. GitHub will build the page and show the live URL
   (usually `https://<username>.github.io/<repo>/`).

> **Tip:** If you prefer using `docs/` instead of the root, move both files into a `docs` folder and pick **Branch: `main` / `/docs`** in the Pages settings.

---

## Updating the site

Edit `index.html` and/or `styles.css`, then commit + push to `main`.
GitHub Pages re-deploys automatically.

```bash
git add -A
git commit -m "Update copy and styles"
git push
```

---

## Custom domain (optional)

1. Buy a domain (e.g., from Namecheap, Google Domains, GoDaddy).  
2. In **Settings → Pages**, add your custom domain (e.g., `www.example.com`).
3. Create DNS records at your registrar pointing to GitHub Pages:
   - **A** records → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - or **CNAME** for subdomains → `<username>.github.io`
4. Commit a `CNAME` file (no extension) containing your domain:
   ```
   www.example.com
   ```

---

## Assets and images

- The logo in `index.html` uses a remote image URL.  
  If you want to bundle the image in the repo, download it to `assets/` and update the `<img src>` path, e.g.:
  ```html
  <img src="assets/web-logo.png" alt="W.E.B. logo">
  ```
- Keep paths **relative** so GitHub Pages can serve them properly.

---

## Troubleshooting

- **404 / Not Found**: Ensure **Settings → Pages** is set to `main` / **root** (or `docs/` if you moved files).  
- **Old version shows**: Hard refresh (Cmd/Ctrl+Shift+R) or clear cache; Pages may take a minute to update.  
- **Styles not loading**: The `<link rel="stylesheet" href="styles.css">` path must match the file location.  
- **Private repo**: Pages works with private repos too, but ensure it’s enabled under Settings.  
- **Index filename**: It must be `index.html` (lowercase) for Pages to serve as the root page.

---

## License

Choose the license that fits your project (MIT, Apache-2.0, etc.). If unsure, MIT is a permissive default.
