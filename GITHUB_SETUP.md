# GitHub Setup Guide for chores-utils

## Step 1: Create GitHub Repository

1. Go to https://github.com/new
2. Repository name: `chores-utils`
3. Description: `A collection of utility functions to automate common programming chores`
4. Choose: **Public**
5. **DO NOT** initialize with README (we already have one)
6. Click "Create repository"

## Step 2: Replace YOUR_USERNAME in Files

Replace `YOUR_USERNAME` with your actual GitHub username in these files:
- `package.json` (3 places)
- `README.md` (multiple badges and links)
- `CONTRIBUTING.md` (1 place)
- `.github/FUNDING.yml`

You can do this with:
```bash
# Replace YOUR_USERNAME with your actual username
find . -type f \( -name "*.json" -o -name "*.md" -o -name "*.yml" \) -exec sed -i 's/YOUR_USERNAME/your-actual-username/g' {} +
```

## Step 3: Push to GitHub

```bash
cd /home/levi/home/Enclave/algorithm/utils-npm

# Add all files
git add .

# Commit
git commit -m "Initial commit: chores-utils v1.0.0"

# Add remote (replace YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/chores-utils.git

# Push
git branch -M main
git push -u origin main
```

## Step 4: Enable GitHub Sponsors (Optional)

1. Go to https://github.com/sponsors
2. Click "Join the waitlist" or "Set up GitHub Sponsors"
3. Follow the setup process
4. Once approved, your sponsor button will appear on your repo

Alternative: Use Ko-fi, Patreon, or Buy Me a Coffee
- Ko-fi: https://ko-fi.com
- Patreon: https://www.patreon.com
- Buy Me a Coffee: https://www.buymeacoffee.com

## Step 5: Update FUNDING.yml

Edit `.github/FUNDING.yml` and add your sponsor links:

```yaml
# Example for GitHub Sponsors
github: [your-username]

# Or Ko-fi
ko_fi: your-username

# Or Buy Me a Coffee
custom: ['https://www.buymeacoffee.com/your-username']
```

## Step 6: Update npm Package

After pushing to GitHub, update your npm package:

```bash
# Update version
npm version patch

# Publish with updated links
npm publish --otp=XXXXXX
```

## Step 7: Enable Repository Features

On GitHub, go to your repository settings and enable:

1. **Issues** - for bug reports and feature requests
2. **Discussions** (optional) - for community Q&A
3. **Sponsorships** - once GitHub Sponsors is set up

## What You'll Get

✅ **GitHub Repository** with full source code
✅ **Contributing Guidelines** for open source contributors
✅ **Sponsor Button** on GitHub and npm
✅ **Issue Tracking** for bugs and features
✅ **MIT License** clearly displayed
✅ **Professional Badges** showing stats
✅ **Funding Options** for supporters

## Quick Replace Command

Replace YOUR_USERNAME with your actual GitHub username:

```bash
# For Linux/Mac
sed -i 's/YOUR_USERNAME/levihack/g' package.json
sed -i 's/YOUR_USERNAME/levihack/g' README.md
sed -i 's/YOUR_USERNAME/levihack/g' CONTRIBUTING.md
sed -i 's/YOUR_USERNAME/levihack/g' .github/FUNDING.yml
```

Then rebuild and republish:
```bash
npm run build
npm version patch
npm publish --otp=XXXXXX
```
