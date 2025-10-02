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
