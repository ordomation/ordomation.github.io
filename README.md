# Ordomation Website

Landing page for [ordomation.com](https://ordomation.com) - Intelligent business automation for Danish small businesses.

## Tech Stack

- **Framework:** [Astro](https://astro.build/)
- **Styling:** Vanilla CSS
- **Hosting:** GitHub Pages
- **Domain:** ordomation.com

## Development

```bash
# Install dependencies
npm install

# Start dev server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Deployment

Automatic deployment via GitHub Actions on push to `main` branch.

### DNS Configuration

Configure these records at your domain registrar:

| Type | Name | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | ordomation.github.io |

## Structure

```
src/
├── layouts/
│   └── Layout.astro       # Base HTML layout
├── components/
│   ├── Nav.astro          # Navigation bar
│   ├── Hero.astro         # Hero section
│   ├── Features.astro     # Feature cards
│   ├── Project.astro      # Current project
│   ├── Team.astro         # Team section
│   ├── OpenSource.astro   # Open source repos
│   └── Footer.astro       # Footer
├── pages/
│   └── index.astro        # Home page
└── styles/
    └── global.css         # Global styles
```

## License

MIT
