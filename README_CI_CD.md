# Mphongo CD Pipeline

This directory contains GitHub Actions CD workflows for each Mphongo repository. Push to `main` will trigger deployment for supported services (Render, Firebase, GitHub Pages, etc.).

Each workflow assumes:
- Python 3.11
- A `requirements.txt` file (for backend repos)
- Secrets like `RENDER_DEPLOY_HOOK` or `PROD_API_KEY` are configured per repo

To deploy all workflows:
```
bash deploy-all.sh

```
# 🚀 CI/CD Strategy for Mphongo Network AI

## ✅ GitHub Actions Workflows

Each repo has `.github/workflows/ci.yml` configured for:

- Linting & Testing
- Docker build (if needed)
- Push to container registry or NPM/PyPI (if applicable)

## 🔐 Required Secrets

See [`secrets.md`](./secrets.md) for environment secrets needed by workflows.

## 🧪 Sample Workflow Overview (`ci.yml`)

```yaml
name: CI Pipeline

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: npm ci
      - run: npm run test


