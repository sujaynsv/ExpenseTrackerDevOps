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
3. Run locally: `go run ./cmd/expenseowl`
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
```

## 🤝 Contributing Guidelines

We welcome contributions to **ExpenseOwl**! Whether it’s fixing bugs, adding features, or improving documentation, your help makes the project better.

### 🛠️ How to Contribute
1. **Fork the repository** on GitHub.
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/your-username/ExpenseTrackerDevOps.git
   ```
3. **Create a new branch** for your changes:
   ```bash
   git checkout -b feature/your-feature-name
   ```
4. **Make your changes** (ensure code is formatted with `go fmt`).
5. **Run tests** to confirm everything works:
   ```bash
   go test ./...
   ```
6. **Commit and push** your changes:
   ```bash
   git commit -m "Add: your feature description"
   git push origin feature/your-feature-name
   ```
7. **Open a Pull Request** against the `main` branch.

---

### 📜 License
By contributing, you agree that your contributions will be licensed under the same license as the project (MIT, unless otherwise specified).
