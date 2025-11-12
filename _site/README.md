# Deploying M43 Site to GitHub Pages

## Step-by-Step Setup

### 1. Create the GitHub Actions Workflow

Create this file in your repository:
```
.github/workflows/jekyll.yml
```

(Use the content from the "GitHub Actions - Jekyll Deploy" artifact)

### 2. Push to GitHub

```bash
git add .
git commit -m "Add GitHub Actions workflow"
git push origin main
```

### 3. Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings**
3. Click **Pages** in the left sidebar
4. Under "Build and deployment":
   - **Source**: Select "GitHub Actions"
5. Save (if needed)

### 4. Wait for Build

- Go to the **Actions** tab in your repository
- Watch the workflow run
- Should complete in 1-2 minutes

### 5. Access Your Site

Your site will be live at:
```
https://[your-username].github.io/[repository-name]
```

For example: `https://rhett.github.io/m43`

## Making Updates

After initial setup, just push changes:

```bash
# Add a new lens
git add _lenses/new-lens.md
git commit -m "Add new lens"
git push

# Site automatically rebuilds and deploys!
```

## Using a Custom Domain (Optional)

1. Add a file named `CNAME` in your repository root
2. Put your domain in it: `m43.yourdomain.com`
3. Configure DNS with your domain registrar:
   - Add CNAME record pointing to `[username].github.io`
4. In GitHub Settings → Pages, add your custom domain

## Troubleshooting

### Build Failed?
- Check the Actions tab for error messages
- Common issues:
  - Missing front matter in content files
  - YAML syntax errors
  - Missing layout files

### Site Not Updating?
- Check Actions tab - build should run after each push
- Hard refresh browser (Ctrl+F5)
- Can take 1-2 minutes to deploy

### Wrong URL/Links Broken?
Update `_config.yml`:
```yaml
baseurl: "/your-repo-name"  # If using github.io/repo-name
url: "https://username.github.io"
```

## Benefits of GitHub Actions

✅ No local Ruby/Jekyll setup needed to contribute
✅ Automatic builds on every push
✅ Preview builds for pull requests
✅ Free hosting on GitHub Pages
✅ SSL certificate included
✅ Community members can contribute via web interface

## Contributing Without Code

Contributors can add content directly on GitHub.com:

1. Navigate to `_lenses/` folder
2. Click "Add file" → "Create new file"
3. Name it: `my-lens.md`
4. Paste the template and fill it out
5. Scroll down and click "Commit changes"
6. Create pull request

No git, no command line, no Ruby needed!