# GitHub Actions CI/CD Setup for MeauxContainer

This document outlines the setup required for automated CI/CD deployment to Cloudflare.

---

## 🔑 Required GitHub Secrets

Add these secrets to your GitHub repository at:
**Settings → Secrets and variables → Actions → New repository secret**

### 1. `CLOUDFLARE_API_TOKEN`
- **Value**: Your Cloudflare API token with Workers edit permissions
- **Current Value**: `poqrNAnK8KcvaLRs7OqixS7KKdkbqm8Ms9ZtUa5n`
- **Note**: You mentioned you'll manually rotate this key after deployment. That's a good security practice!

### 2. `CLOUDFLARE_ACCOUNT_ID`
- **Value**: `ede6590ac0d2fb7daf155b35653457b2`
- **Purpose**: Identifies your Cloudflare account

---

## 📋 Setup Steps

### Step 1: Add GitHub Secrets

1. Go to: https://github.com/SamPrimeaux/meauxcontainer/settings/secrets/actions
2. Click **"New repository secret"**
3. Add each secret:
   - Name: `CLOUDFLARE_API_TOKEN`
   - Value: `poqrNAnK8KcvaLRs7OqixS7KKdkbqm8Ms9ZtUa5n`
   
   - Name: `CLOUDFLARE_ACCOUNT_ID`
   - Value: `ede6590ac0d2fb7daf155b35653457b2`

### Step 2: Verify Workflow

The workflow (`.github/workflows/ci-cd.yml`) will:
- ✅ Build on every push to `main`
- ✅ Run TypeScript type checking
- ✅ Deploy to Cloudflare on successful build
- ✅ Skip deployment on pull requests (only builds)

### Step 3: Test Deployment

1. Make a small change to `src/index.ts` or `README.md`
2. Commit and push:
   ```bash
   git add .
   git commit -m "Test CI/CD deployment"
   git push origin main
   ```
3. Check Actions tab: https://github.com/SamPrimeaux/meauxcontainer/actions
4. Verify deployment at: https://meauxcontainer.meauxbility.workers.dev

---

## 🚀 Manual Deployment (Alternative)

If you prefer to deploy manually:

```bash
cd /Users/samprimeaux/Desktop/meauxcontainer
npm install
npm run deploy
```

**Note**: You'll need to set `CLOUDFLARE_API_TOKEN` in your environment:
```bash
export CLOUDFLARE_API_TOKEN="poqrAnK8KcvaLRs7OqixS7KKdkbqm8Ms9ZtUa5n"
export CLOUDFLARE_ACCOUNT_ID="ede6590ac0d2fb7daf155b35653457b2"
```

---

## 🔒 Security Notes

1. **API Token Rotation**: As you mentioned, rotate the API token after initial setup via Cloudflare Dashboard
2. **Secrets Management**: Never commit API tokens or secrets to the repository
3. **Token Permissions**: Ensure your API token has:
   - Workers: Edit
   - Account: Read
   - Containers: Edit

---

## 📊 Workflow Details

### Build Job
- Runs on: `ubuntu-latest`
- Steps:
  1. Checkout code
  2. Setup Node.js 20
  3. Install dependencies (`npm ci`)
  4. TypeScript type checking
  5. Container build verification

### Deploy Job
- Runs on: `ubuntu-latest`
- Triggers: Only on pushes to `main` branch (not PRs)
- Steps:
  1. Checkout code
  2. Setup Node.js 20
  3. Install dependencies
  4. Deploy to Cloudflare (`npm run deploy`)
  5. Verify deployment

---

## 🐛 Troubleshooting

### Deployment Fails
- Check that secrets are correctly set in GitHub
- Verify API token has correct permissions
- Check Cloudflare Dashboard for error logs

### Build Fails
- Ensure all dependencies are in `package.json`
- Check TypeScript compilation errors
- Verify `wrangler.jsonc` is valid JSON

### Container Build Issues
- Verify Dockerfile is correct
- Check Go module dependencies in `container_src/go.mod`
- Ensure container source compiles locally first

---

## 📚 Resources

- [Cloudflare Containers Documentation](https://developers.cloudflare.com/containers/)
- [Wrangler CLI Documentation](https://developers.cloudflare.com/workers/wrangler/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

---

**Status**: ✅ CI/CD workflow created and ready for deployment

