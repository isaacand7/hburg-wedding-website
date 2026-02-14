# Deployment Guide: Cloudflare Pages

This guide will walk you through deploying your wedding videography website to Cloudflare Pages and connecting your domain.

## Prerequisites
- ✅ Domain purchased from Namecheap
- ✅ Domain active on Cloudflare
- ✅ GitHub account
- ✅ All website files created (`index.html`, `faq.html`, `styles.css`, `site-data.json`)

## Step 1: Create a GitHub Repository

1. Go to [github.com](https://github.com) and sign in
2. Click the **"+"** icon in the top right, then select **"New repository"**
3. Name it something like `wedding-videography-website` (or whatever you prefer)
4. Make it **Public** (Cloudflare Pages free tier requires public repos, or you can use Cloudflare's direct upload)
5. **Don't** initialize with README, .gitignore, or license (we already have files)
6. Click **"Create repository"**

## Step 2: Upload Files to GitHub

### Option A: Using GitHub's Web Interface (Easiest)

1. On your new repository page, click **"uploading an existing file"**
2. Drag and drop all your files (`index.html`, `faq.html`, `styles.css`, `site-data.json`) into the upload area
3. Scroll down, add a commit message like "Initial website files"
4. Click **"Commit changes"**

### Option B: Using Git Command Line (If you have Git installed)

Open Terminal and run:

```bash
cd /Users/isaac/IdeaProjects/VideoWebsite
git init
git add .
git commit -m "Initial website files"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git push -u origin main
```

(Replace `YOUR_USERNAME` and `YOUR_REPO_NAME` with your actual GitHub username and repository name)

## Step 3: Deploy to Cloudflare Pages

1. Go to [dash.cloudflare.com](https://dash.cloudflare.com) and sign in
2. In the left sidebar, click **"Workers & Pages"**
3. Click **"Create application"**
4. Click **"Pages"** tab, then **"Connect to Git"**
5. Authorize Cloudflare to access your GitHub account (if prompted)
6. Select your repository (`wedding-videography-website` or whatever you named it)
7. Click **"Begin setup"**
8. Configure the build:
   - **Project name**: `isaac-andreas-weddings` (or your preference)
   - **Production branch**: `main` (or `master` if that's what you used)
   - **Build command**: Leave empty (we're using static HTML, no build needed)
   - **Build output directory**: `/` (root directory)
9. Click **"Save and Deploy"**

Cloudflare will deploy your site and give you a URL like `isaac-andreas-weddings.pages.dev`

## Step 4: Connect Your Custom Domain

1. In Cloudflare Pages, click on your project
2. Go to the **"Custom domains"** tab
3. Click **"Set up a custom domain"**
4. Enter your domain (e.g., `isaacandreasweddings.com` or `www.isaacandreasweddings.com`)
5. Cloudflare will automatically configure DNS records
6. Wait a few minutes for DNS to propagate (usually 5-15 minutes)

## Step 5: Add Your Images and Videos

1. Create an `assets` folder in your project
2. Add your images:
   - `assets/hero-still.jpg` - Hero section image (recommended: 1920x1080px)
   - `assets/blue-ridge-thumb.jpg` - Thumbnail for video 1 (recommended: 1280x720px)
   - `assets/harrisonburg-loft-thumb.jpg` - Thumbnail for video 2
   - `assets/shenandoah-barn-thumb.jpg` - Thumbnail for video 3
3. Update `index.html` with your actual video URLs:
   - Replace `https://your-video-link-1` with your YouTube/Vimeo links
   - Replace `https://your-video-link-2` with your second video
   - Replace `https://your-video-link-3` with your third video
4. Commit and push these changes to GitHub
5. Cloudflare Pages will automatically redeploy (usually takes 1-2 minutes)

## Step 6: Update Your Content

Edit these files to customize:
- **`index.html`**: Update video links, descriptions, pricing ranges
- **`faq.html`**: Adjust answers to match your exact policies
- **`site-data.json`**: Update social media links, pricing notes, etc.

After editing, commit and push to GitHub, and Cloudflare will automatically redeploy.

## How to update your site (Git + Cloudflare)

After your site is already deployed, use these steps whenever you change files and want the live site to update.

### Option A: Using GitHub’s website (no Git installed)

1. Go to your repo on GitHub (e.g. `https://github.com/isaacand7/hburg-wedding-website`).
2. Open the file you want to edit and click the **pencil icon** (Edit).
3. Make your changes, then scroll down and click **Commit changes**.
4. Cloudflare Pages will pick up the new commit and redeploy (usually 1–2 minutes). Check **Workers & Pages → your project → Deployments** to see status.

To add or change multiple files: use **Add file → Upload files**, then commit.

### Option B: Using Git on your computer

1. **Open Terminal** and go to your project folder:
   ```bash
   cd /Users/isaac/IdeaProjects/VideoWebsite
   ```

2. **If this folder isn’t a Git repo yet**, set it up and link GitHub:
   ```bash
   git init
   git add .
   git commit -m "Initial website"
   git branch -M main
   git remote add origin https://github.com/isaacand7/hburg-wedding-website.git
   git push -u origin main
   ```
   (Use your real repo URL if it’s different.)

3. **When you’ve made changes** and want to update the live site:
   ```bash
   cd /Users/isaac/IdeaProjects/VideoWebsite
   git add .
   git status
   git commit -m "Describe your change (e.g. Light grey borders, fix alignment)"
   git push
   ```

4. Cloudflare will automatically build and deploy. Wait 1–2 minutes, then refresh your site.

**Useful commands:**
- `git status` — see which files changed
- `git add .` — stage all changes (or use `git add path/to/file` for one file)
- `git push` — send commits to GitHub (Cloudflare deploys from GitHub)

## Troubleshooting

- **Domain not working?** Check DNS settings in Cloudflare dashboard. Make sure the domain is pointing to your Pages project.
- **Images not showing?** Make sure image paths match exactly (case-sensitive). Check that files are in the `assets/` folder.
- **Changes not appearing?** Wait 1-2 minutes for Cloudflare to rebuild, or check the "Deployments" tab for build status.

## Need Help?

If you run into issues, check:
- Cloudflare Pages documentation: https://developers.cloudflare.com/pages/
- GitHub documentation: https://docs.github.com

Your site should now be live at your custom domain! 🎉
