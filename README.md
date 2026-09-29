# Dmytro — Personal Portfolio Site

A minimal, fast personal portfolio website built with [Jekyll](https://jekyllrb.com/) and the [Minima](https://github.com/jekyll/minima) theme. Deployed on GitHub Pages.

## Features

- Single-page portfolio layout
- Responsive design (mobile-friendly)
- Hero section with social links
- Skills organized by category
- Project showcase cards
- Contact section
- SEO optimized with jekyll-seo-tag
- No JavaScript required

## Quick Start

### Prerequisites

- Ruby 3.0+
- Bundler (`gem install bundler`)

### Local Development

```bash
# Install dependencies
bundle install

# Start development server with live reload
bundle exec jekyll serve --livereload
```

Visit `http://localhost:4000`

### Build for Production

```bash
bundle exec jekyll build
```

Output in `_site/` directory.

## Project Structure

```
├── _config.yml          # Site configuration
├── index.md             # Main portfolio page
├── _layouts/
│   └── default.html     # Base layout (no theme header/footer)
├── assets/
│   └── main.scss        # Custom styles
├── Gemfile              # Ruby dependencies
└── _site/               # Generated site (gitignored)
```

## Customization

Edit these files to personalize:

| File | Purpose |
|------|---------|
| `_config.yml` | Site title, description, social links |
| `index.md` | Hero, about, skills, projects, contact |
| `assets/main.scss` | Custom styles |

## Deploy to GitHub Pages

1. Push to a repository named `username.github.io`
2. Enable GitHub Pages in Settings → Pages
3. Select "Deploy from branch" → `main` → `/(root)`
4. Site will be live at `https://username.github.io`

Or use a custom domain by adding a `CNAME` file to the root.

## License

MIT — feel free to use as a template for your own portfolio.