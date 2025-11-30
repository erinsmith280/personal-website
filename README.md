# Erin's Personal Website

A minimal, fast personal website built with Zola.

## Setup

### 1. Install Zola

**macOS:**
```bash
brew install zola
```

**Windows:**
```bash
scoop install zola
```

**Linux:**
```bash
# Download from https://github.com/getzola/zola/releases
```

Or visit [Zola's installation guide](https://www.getzola.org/documentation/getting-started/installation/).

### 2. Run Locally

```bash
cd erin-website
zola serve
```

Your site will be available at `http://127.0.0.1:1111`

The site will automatically reload when you make changes!

### 3. Build for Production

```bash
zola build
```

This creates a `public/` folder with your static site.

## Deployment Options

### Option 1: Netlify (Recommended - Free & Easy)

1. Push this folder to GitHub
2. Go to [Netlify](https://www.netlify.com/)
3. Click "Add new site" → "Import an existing project"
4. Connect your GitHub repo
5. Build settings:
   - **Build command:** `zola build`
   - **Publish directory:** `public`
6. Click "Deploy"

Your site will be live in minutes! Netlify gives you a free `.netlify.app` domain and you can add a custom domain.

### Option 2: Vercel (Also Free & Fast)

1. Push to GitHub
2. Go to [Vercel](https://vercel.com/)
3. Import your repository
4. Vercel auto-detects Zola and configures everything
5. Deploy!

### Option 3: GitHub Pages

1. Add this to your repo as `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: shalzz/zola-deploy-action@v0.17.2
        env:
          PAGES_BRANCH: gh-pages
          TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

2. Push to GitHub
3. Enable GitHub Pages in your repo settings (use `gh-pages` branch)

### Option 4: Cloudflare Pages

1. Push to GitHub
2. Go to [Cloudflare Pages](https://pages.cloudflare.com/)
3. Connect your repo
4. Build command: `zola build`
5. Output directory: `public`
6. Deploy!

## Customization

### Update Content

Edit `content/_index.md` to change the text on your homepage.

### Change Colors

Edit `static/style.css`:
- Links: Change `#0066cc` to your preferred color
- Text: Change `#1a1a1a` for body text
- Background: Change `#ffffff` for page background

### Add Your Domain

In `config.toml`, update:
```toml
base_url = "https://yourdomain.com"
```

### Add Analytics (Optional)

Add to `templates/base.html` before `</head>`:

**Plausible (privacy-friendly):**
```html
<script defer data-domain="yourdomain.com" src="https://plausible.io/js/script.js"></script>
```

**Google Analytics:**
```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

## Structure

```
erin-website/
├── config.toml           # Site configuration
├── content/
│   └── _index.md        # Homepage content
├── templates/
│   ├── base.html        # Base template
│   └── index.html       # Homepage template
├── static/
│   └── style.css        # Styles
└── README.md            # This file
```

## Adding New Pages

To add a new page (like "Writing" or "Projects"):

1. Create `content/writing.md`:
```markdown
+++
title = "Writing"
+++

# My Writing

Content here...
```

2. It will be available at `/writing/`

## Support

- [Zola Documentation](https://www.getzola.org/documentation/)
- [Zola Community Forum](https://zola.discourse.group/)

## License

Feel free to use this as a template for your own site!
