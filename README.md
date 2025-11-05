# ExpenseOwl

A simple, self-hosted expense tracking web app built with Go. Track expenses, incomes, and recurring transactions with a clean UI. No authentication included—use a reverse proxy for security.

## Features
- Dashboard with pie charts for monthly stats
- Table view for detailed expense lists
- Recurring transactions
- CSV import/export
- JSON or Postgres storage backends
- Light/dark theme

## Quick Start (Local)
1. Install Go and Docker.
2. Clone the repo: `git clone https://github.com/sujaynsv/ExpenseTrackerDevOps`
3. Run locally: `go run ./cmd/expenseowl` or use Docker: `docker run -p 8080:8080 tanq16/expenseowl:main`
4. Open `http://localhost:8080` in your browser.

## Deployment
Deployed on Render with GitHub Actions for CI/CD.

### On Render
- Connect your GitHub repo to Render.
- Create a Web Service using the Dockerfile (port 8080).
- Add environment variables for storage (see below).
- Access at your Render URL (e.g., `https://expenseowl.onrender.com`).

### GitHub Actions
The `.github/workflows/deploy.yml` triggers Render deploys on pushes to `main`:
```yaml
name: Deploy to Render
on:
  push:
    branches: [main]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Trigger Render Deploy
        run: curl -X POST ${{ secrets.RENDER_DEPLOY_HOOK }}