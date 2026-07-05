# Sh1n Chronicles - Setup & Customization Guide

## 🚀 Quick Start

```bash
# Start the dev server (live reload)
hugo server -D

# Build for production
hugo
```

Visit `http://localhost:1313` to see your site live.

---

## 📁 Project Structure

```
content/
├── research/        # Deep research articles
├── writeups/        # CTF & challenge writeups
├── analysis/        # Threat intelligence & analysis
└── about.md         # About page

assets/css/
└── extended.css     # Custom styling (your playground)

themes/PaperMod/     # Theme (don't edit directly)
```

---

## 🎨 Customization Guide

### 1. **Colors & Theme (Easy)**
Edit `assets/css/extended.css`:
```css
:root {
  --primary-color: #00d4ff;      /* Main accent */
  --secondary-color: #ff006e;    /* Hover accent */
  --background: #0a0e27;         /* Page background */
  --surface: #16213e;            /* Card/code background */
  --text-primary: #e0e0e0;       /* Main text */
  --text-secondary: #a0a0a0;     /* Dimmed text */
}
```

### 2. **Header & Footer (Medium)**
To customize header/footer:

**Option A - Via Hugo Config** (Easiest)
Edit `hugo.toml` - adjust these sections:
```toml
[params.profileMode]
# Your homepage hero
subtitle = "Your custom subtitle here"

[menu.main]
# Adjust top menu items
```

**Option B - Custom HTML Templates** (Advanced)
Create these files to override PaperMod defaults:
- `layouts/partials/header.html` - Top navigation
- `layouts/partials/footer.html` - Bottom section
- `layouts/partials/comments.html` - Comments area

Example: `layouts/partials/footer.html`
```html
<footer class="footer">
  <div class="footer-content">
    <p>&copy; 2026 Sh1n Chronicles. Research & Analysis.</p>
    <nav class="footer-links">
      <a href="/">Home</a>
      <a href="/research">Research</a>
      <a href="/about">About</a>
    </nav>
  </div>
</footer>
```

### 3. **Typography (Easy)**
Add to `assets/css/extended.css`:
```css
body {
  font-family: 'Fira Code', monospace;  /* or your font */
  letter-spacing: 0.5px;
}

h1, h2, h3 {
  font-family: 'Space Mono', monospace;
}
```

### 4. **Homepage Layout**
Edit `hugo.toml` - `[params.profileMode]` section:
- Change `subtitle`
- Add/remove buttons
- Adjust images

---

## 📝 Creating Content

### New Research Article
```bash
hugo new research/your-topic.md
```

### New Writeup
```bash
hugo new writeups/htb-machine-name.md
```

### New Analysis Post
```bash
hugo new analysis/threat-analysis.md
```

### Front Matter Template
```yaml
---
title: "Article Title"
date: 2026-07-04
draft: false
tags: ["tag1", "tag2"]
categories: ["Research"]
description: "Short description for SEO"
cover:
  image: "image.jpg"
  alt: "Alt text"
  caption: "Caption"
---
```

---

## 🔧 Advanced Customization

### Custom Shortcodes
Create `layouts/shortcodes/highlight.html`:
```html
<div class="custom-highlight">
  {{ .Inner }}
</div>
```

Use in posts:
```markdown
{{< highlight >}}
Your content here
{{< /highlight >}}
```

### Social Links
Edit `hugo.toml`:
```toml
[[params.socialIcons]]
name = "github"
url = "https://github.com/yourusername"

[[params.socialIcons]]
name = "twitter"
url = "https://twitter.com/yourusername"
```

---

## 🎯 Tips & Tricks

- **Draft posts**: Use `draft: true` in front matter to hide during dev
- **Reading time**: Automatically calculated (configure in `hugo.toml`)
- **Table of Contents**: Automatically generated from headings
- **Search**: Built-in search (customize via `params`)
- **Archives**: Enable with `ShowArchives = true` in `hugo.toml`

---

## 📦 Deployment

### GitHub Pages
1. Set `baseURL` in `hugo.toml` to `https://yourusername.github.io/sh1n-chronicles/`
2. Build: `hugo`
3. Push `public/` folder to your GitHub Pages repo

### Other Hosts
Use `hugo` command to generate static files in `public/` folder.

---

## 🐛 Troubleshooting

**Site looks ugly:**
- Clear cache: `rm -rf resources/` then `hugo server -D`
- Check `hugo.toml` syntax (TOML can be picky)

**Posts not showing:**
- Check they're not `draft: true`
- Verify folder structure matches `content/research/`, `content/writeups/`, etc.

**CSS changes not applying:**
- Restart `hugo server`
- Clear browser cache (Ctrl+Shift+Delete)

---

## 📚 Resources

- **PaperMod Docs**: https://github.com/adityatelange/hugo-PaperMod
- **Hugo Docs**: https://gohugo.io/documentation/
- **Front Matter Reference**: https://gohugo.io/content-management/front-matter/

Happy writing! 🚀
