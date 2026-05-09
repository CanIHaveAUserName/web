# malachitevr.win — Portfolio Site

Personal portfolio hosted on **GitHub Pages** with a custom domain via **Cloudflare**.

---

## 🚀 Setup Guide

### 1. Create a GitHub Repository

1. Go to [github.com/new](https://github.com/new)
2. Name it **exactly**: `<your-username>.github.io`  
   *(e.g. `malachitevr.github.io`)*
3. Set it to **Public**
4. Click **Create repository**

### 2. Push These Files

```bash
git init
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-username>.github.io.git
git push -u origin main
```

### 3. Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages**
2. Under **Source**, select **Deploy from a branch**
3. Choose `main` branch, `/ (root)` folder → **Save**
4. Under **Custom domain**, enter `malachitevr.win` → **Save**
5. ✅ Check **Enforce HTTPS** (after DNS propagates)

---

## 🌐 Cloudflare DNS Setup

In your Cloudflare dashboard for `malachitevr.win`, go to **DNS → Records** and add:

| Type  | Name  | Content                  | Proxy status |
|-------|-------|--------------------------|--------------|
| A     | @     | 185.199.108.153          | **DNS only** ☁️→🔒 |
| A     | @     | 185.199.109.153          | **DNS only** |
| A     | @     | 185.199.110.153          | **DNS only** |
| A     | @     | 185.199.111.153          | **DNS only** |
| CNAME | www   | `<your-username>.github.io` | **DNS only** |

> ⚠️ **Important**: Set all records to **DNS only** (grey cloud), NOT proxied (orange cloud).  
> GitHub Pages handles HTTPS itself via Let's Encrypt. Proxying through Cloudflare can break certificate verification.

---

## ✏️ Editing the Site

All content is in **`index.html`**. Look for the `<!-- Edit ... -->` comments:

- **Hero text** — your tagline and description
- **About bio** — your background
- **Skills** — your tech stack
- **Stats** — numbers that represent you
- **Projects** — add/remove `.project-card` blocks with your work
- **Contact links** — your email, GitHub, socials

### Adding a Project

Copy this block inside `.projects-grid` in `index.html`:

```html
<a href="YOUR_PROJECT_URL" class="project-card reveal">
  <div class="project-num">04</div>
  <div class="project-title">Your Project Name</div>
  <div class="project-desc">What it does and why it's cool.</div>
  <div class="project-tags">
    <span class="tag">Tech</span>
    <span class="tag">Stack</span>
  </div>
  <div class="project-arrow">↗</div>
</a>
```

---

## 📁 File Structure

```
/
├── index.html   ← Main site (edit this)
├── CNAME        ← Custom domain (do not delete)
└── README.md    ← This file
```

You can add more pages (e.g. `projects.html`, `blog/index.html`) and link to them from the nav.

---

## ⏱️ DNS Propagation

Changes can take **a few minutes to 48 hours** to propagate. Use [dnschecker.org](https://dnschecker.org) to verify your records are live.
