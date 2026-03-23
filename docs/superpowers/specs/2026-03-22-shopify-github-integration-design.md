# Shopify GitHub Integration Setup — Design Spec

**Status**: Completed (2026-03-22)

## Context

Hello Darling, LLC runs a Shopify store (hellodarlingdesigns.net) selling custom apparel and gifts using the Rise theme v15.4.0. The theme had been customized via the Shopify theme editor (logo, Murecho font, #c86468 color scheme, social links, cart config). The goal was to establish version-controlled theme development with automatic bidirectional sync between GitHub and Shopify, without overwriting any existing live customizations.

## Decision: Include config/settings_data.json in Git

`config/settings_data.json` is tracked in git. This is required because Shopify's GitHub integration auto-commits theme editor changes back to the connected branch. Excluding it would break the bidirectional sync.

## Architecture

```
Local Dev (C:\Code\Shopify_HelloDarling)
    ↕ git push/pull
GitHub (DustinHannon/Shopify_HelloDarling, main branch)
    ↕ Shopify GitHub integration (bidirectional)
Shopify Live Theme (hellodarlingdesigns.net)
```

- **Push to main** → Shopify auto-updates the published theme
- **Edit in Shopify theme editor** → auto-commits to main on GitHub
- **Local edits** require `git pull` first to pick up any Shopify editor commits

## Safety Model

The setup used the "Connect from GitHub" flow which creates a new unpublished theme. The live site was never at risk during setup:

1. Downloaded theme (exact copy of live) → committed to git
2. Pushed to GitHub
3. Connected from GitHub → created new unpublished theme
4. Previewed connected theme → verified it matched live site
5. Published only after visual confirmation

## .gitignore

```
**/CLAUDE.md
node_modules/
.claude/
.playwright-mcp/
```

## Theme Details

- **Theme**: Shopify Rise v15.4.0
- **Brand**: Hello Darling, LLC / Darling Drink Company (sister brand)
- **Store URL**: hellodarlingdesigns.net
- **GitHub Repo**: https://github.com/DustinHannon/Shopify_HelloDarling (public)
- **Customizations**: HD logo, Murecho font, #c86468 dusty rose color, Facebook/TikTok social links, notification-based cart, announcement bar ("CURRENT PRODUCTION TIME 4-7 BUSINESS DAYS")
- **Product Collections**: Embroidery, Badge Reels/Pop Sockets, Tea Towels, Magnets, Leather Products
- **Structure**: Standard Shopify theme (assets/, config/, layout/, locales/, sections/, snippets/, templates/)
- **Build tools**: None — pure Liquid/Shopify
- **Files**: ~352 theme files, 40+ locale files (25+ languages)

## Ongoing Workflow

1. `git pull` before any local editing
2. Make changes locally
3. `git push origin main` to deploy to Shopify
4. Verify via live site or Shopify admin
5. Theme editor changes sync back automatically — pull before next local edit
