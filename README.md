# Hello Darling, LLC — Shopify Theme

Shopify Rise theme v15.4.0 for [Hello Darling, LLC](https://hellodarlingdesigns.net) — custom apparel and gifts.

## Setup

This theme is connected to Shopify via the [Shopify GitHub integration](https://shopify.dev/docs/storefronts/themes/tools/github). Changes pushed to `main` automatically deploy to the live store.

### Development Workflow

1. `git pull` — always pull first to pick up any Shopify theme editor commits
2. Edit theme files locally
3. `git push origin main` — deploys automatically to Shopify
4. Verify on the live site

### Shopify Theme Editor

Edits made through the Shopify admin theme editor are automatically committed back to `main` on GitHub. Always pull before starting local work.

## Project Structure

```
assets/          CSS, JavaScript, SVG icons, images
config/          Theme settings (settings_data.json, settings_schema.json)
layout/          Global layout templates
locales/         Translation files (25+ languages)
sections/        Editable template sections
snippets/        Reusable Liquid partials
templates/       Page templates
docs/            Design specs (not synced to Shopify)
```

## Theme Details

- **Base Theme**: [Rise](https://themes.shopify.com/themes/rise) v15.4.0 by Shopify
- **Platform**: Shopify (Liquid, CSS, vanilla JS)
- **Build Tools**: None required

## Links

- [Shopify Liquid Docs](https://shopify.dev/docs/storefronts/themes)
- [Shopify GitHub Integration](https://shopify.dev/docs/storefronts/themes/tools/github)
- [Shopify Version Control Best Practices](https://shopify.dev/docs/storefronts/themes/best-practices/version-control)
