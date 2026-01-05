# 🚀 MeauxContainer Quick Start

## Setup Complete ✅

CI/CD workflow has been configured for automated deployments to Cloudflare.

---

## ⚡ Quick Commands

```bash
# Navigate to project
cd /Users/samprimeaux/Desktop/meauxcontainer

# Install dependencies
npm install

# Run locally
npm run dev

# Deploy manually
npm run deploy
```

---

## 🔑 Add GitHub Secrets (Required)

**Before pushing, add these secrets to GitHub:**

1. Go to: https://github.com/SamPrimeaux/meauxcontainer/settings/secrets/actions
2. Add:
   - `CLOUDFLARE_API_TOKEN` = `poqrAnK8KcvaLRs7OqixS7KKdkbqm8Ms9ZtUa5n`
   - `CLOUDFLARE_ACCOUNT_ID` = `ede6590ac0d2fb7daf155b35653457b2`

---

## 📤 First Deployment

```bash
git add .
git commit -m "Add CI/CD workflow"
git push origin main
```

Then check: https://github.com/SamPrimeaux/meauxcontainer/actions

---

## 🌐 Live URLs

- **Worker**: https://meauxcontainer.meauxbility.workers.dev
- **Preview**: https://*-meauxcontainer.meauxbility.workers.dev

---

## 📚 Full Documentation

- `GITHUB_ACTIONS_SETUP.md` - Complete setup guide
- `SETUP_COMPLETE.md` - Detailed setup summary

