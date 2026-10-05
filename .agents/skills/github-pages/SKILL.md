---
name: github-pages
description: Use this skill when deploying static sites, front-end web apps, or documentation to GitHub Pages. It outlines the modern Actions-based deployment strategy.
---

# GitHub Pages Deployment Skill

GitHub Pages is a static site hosting service that takes HTML, CSS, and JavaScript files straight from a repository and publishes a website.

## Legacy vs. Modern Deployment

1. **Legacy Branch Deployment:** 
   - Uses the GitHub UI (`Settings -> Pages`) to point to a specific branch (like `main`) and folder (like `/root`).
   - GitHub runs a hidden deployment action in the background.
   - **Warning:** This shared background queue can occasionally experience severe delays (5–20 minutes) during peak hours.

2. **Modern Actions Deployment (Preferred):**
   - Completely bypasses the legacy queue by explicitly using GitHub Actions.
   - Requires setting `Settings -> Pages -> Build and deployment -> Source` to **GitHub Actions**.
   - Requires a dedicated workflow file at `.github/workflows/pages.yml`.

## Standard Static HTML Deployment Workflow (`pages.yml`)

Whenever asked to deploy a static HTML site to GitHub pages, default to creating this explicit workflow file:

```yaml
name: Deploy static content to Pages

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Pages
        uses: actions/configure-pages@v4
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

### Protocol for Agents:
- Write the workflow to `.github/workflows/pages.yml`.
- Make sure to warn the user if macOS keychain limitations will block you from running `git push`.
- The URL will automatically be `https://<username>.github.io/<repo-name>/`.
