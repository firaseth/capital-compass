# Capital Compass - Deployment Guide

Complete guide to deploying Capital Compass to various platforms.

---

## 📋 Prerequisites

- Node.js 18+ installed
- Git installed
- GitHub account
- Account on your chosen deployment platform (Vercel/Netlify/GitHub Pages)

---

## 🚀 Quick Deployment Options

### Option 1: Deploy to Vercel (Recommended)

**Why Vercel?**
- Fastest deployment
- Automatic HTTPS
- Global CDN
- Perfect for React apps
- Free tier available

**Steps:**

1. **Push to GitHub first** (see GitHub setup below)

2. **Visit Vercel**
   - Go to [vercel.com](https://vercel.com)
   - Sign up with GitHub

3. **Import Project**
   - Click "Add New Project"
   - Import your `capital-compass` repository
   - Vercel auto-detects Vite settings

4. **Deploy**
   - Click "Deploy"
   - Wait 2-3 minutes
   - Your site is live! 🎉

**Custom Domain (Optional):**
```
Project Settings → Domains → Add Domain
Enter: capitalcompass.com (or your domain)
Follow DNS configuration instructions
```

**Environment Variables:**
```
Project Settings → Environment Variables
Add any needed variables
```

---

### Option 2: Deploy to Netlify

**Why Netlify?**
- Easy drag-and-drop deployment
- Form handling built-in
- Excellent documentation
- Free tier available

**Steps:**

1. **Build Locally**
   ```bash
   npm run build
   ```

2. **Deploy via Netlify CLI**
   ```bash
   # Install Netlify CLI
   npm install -g netlify-cli

   # Login
   netlify login

   # Deploy
   netlify deploy --prod
   ```

3. **Or Deploy via Website**
   - Go to [netlify.com](https://netlify.com)
   - Drag and drop your `dist` folder
   - Done! 🚀

**Continuous Deployment:**
```bash
# Link to GitHub repo
netlify init

# Netlify will auto-deploy on git push
```

---

### Option 3: Deploy to GitHub Pages

**Why GitHub Pages?**
- Free hosting
- Easy integration with GitHub
- Good for open-source projects

**Steps:**

1. **Install gh-pages**
   ```bash
   npm install --save-dev gh-pages
   ```

2. **Update package.json**
   ```json
   {
     "homepage": "https://YOUR-USERNAME.github.io/capital-compass",
     "scripts": {
       "predeploy": "npm run build",
       "deploy": "gh-pages -d dist"
     }
   }
   ```

3. **Update vite.config.js**
   ```javascript
   export default defineConfig({
     base: '/capital-compass/',
     // ... rest of config
   })
   ```

4. **Deploy**
   ```bash
   npm run deploy
   ```

5. **Enable GitHub Pages**
   - Go to repository Settings
   - Pages → Source → gh-pages branch
   - Save

Your site will be live at: `https://YOUR-USERNAME.github.io/capital-compass`

---

### Option 4: Deploy to Cloudflare Pages

**Why Cloudflare Pages?**
- Lightning fast global CDN
- Unlimited bandwidth
- Built-in analytics
- Free tier

**Steps:**

1. **Push to GitHub** (see below)

2. **Go to Cloudflare Pages**
   - Visit [pages.cloudflare.com](https://pages.cloudflare.com)
   - Connect your GitHub account

3. **Create Project**
   - Select your repository
   - Build command: `npm run build`
   - Build output: `dist`
   - Click "Save and Deploy"

---

## 📁 GitHub Repository Setup

### Step 1: Create Repository on GitHub

1. Go to [github.com/new](https://github.com/new)
2. Repository name: `capital-compass`
3. Description: "Professional economic feasibility studies powered by AI"
4. Choose Public or Private
5. **Don't** initialize with README (we have one)
6. Click "Create repository"

---

### Step 2: Prepare Your Local Project

Create this folder structure on your computer:

```
capital-compass/
├── src/
│   ├── App.jsx          (copy from artifact)
│   ├── main.jsx         (from artifacts)
│   └── index.css        (from artifacts)
├── public/
│   └── index.html       (from artifacts)
├── package.json         (from artifacts)
├── vite.config.js       (from artifacts)
├── tailwind.config.js   (from artifacts)
├── postcss.config.js    (from artifacts)
├── .gitignore          (from artifacts)
├── README.md           (from artifacts)
└── DEPLOYMENT.md       (this file)
```

---

### Step 3: Copy Files from Artifacts

I've created all the necessary files as artifacts above. Copy each one:

1. **package.json** - Project dependencies
2. **README.md** - Project documentation
3. **.gitignore** - Git ignore rules
4. **vite.config.js** - Vite configuration
5. **tailwind.config.js** - Tailwind configuration
6. **postcss.config.js** - PostCSS configuration
7. **src/main.jsx** - React entry point
8. **src/index.css** - Global styles
9. **index.html** - HTML template
10. **src/App.jsx** - Main app (from the feasibility_study_platform artifact)

---

### Step 4: Initialize Git and Push

```bash
# Navigate to project folder
cd capital-compass

# Initialize git
git init

# Add all files
git add .

# First commit
git commit -m "Initial commit: Capital Compass platform"

# Add remote (replace YOUR-USERNAME)
git remote add origin https://github.com/YOUR-USERNAME/capital-compass.git

# Push to GitHub
git branch -M main
git push -u origin main
```

---

### Step 5: Verify on GitHub

Visit `https://github.com/YOUR-USERNAME/capital-compass` and you should see all your files!

---

## 🔧 Local Development

### First Time Setup

```bash
# Clone repository
git clone https://github.com/YOUR-USERNAME/capital-compass.git
cd capital-compass

# Install dependencies
npm install

# Start development server
npm run dev
```

Visit `http://localhost:3000` to see your app running locally.

---

### Making Changes

```bash
# Create a new branch
git checkout -b feature/my-new-feature

# Make your changes
# ... edit files ...

# Commit changes
git add .
git commit -m "Add amazing new feature"

# Push to GitHub
git push origin feature/my-new-feature

# Create Pull Request on GitHub
```

---

## 🌐 Custom Domain Setup

### For Vercel

1. Buy domain from Namecheap, GoDaddy, etc.
2. In Vercel: Project Settings → Domains
3. Add your domain
4. Update DNS records at your registrar:
   ```
   Type: CNAME
   Name: @
   Value: cname.vercel-dns.com
   ```

### For Netlify

1. Netlify Dashboard → Domain Settings
2. Add custom domain
3. Update DNS:
   ```
   Type: A
   Name: @
   Value: 75.2.60.5
   ```

### For Cloudflare Pages

1. Already on Cloudflare, so DNS is automatic!
2. Just add domain in Pages dashboard
3. Cloudflare handles the rest

---

## 📊 Analytics Setup

### Google Analytics

1. Get tracking ID from [analytics.google.com](https://analytics.google.com)

2. Add to `index.html` in `<head>`:
   ```html
   <!-- Google Analytics -->
   <script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
   <script>
     window.dataLayer = window.dataLayer || [];
     function gtag(){dataLayer.push(arguments);}
     gtag('js', new Date());
     gtag('config', 'G-XXXXXXXXXX');
   </script>
   ```

---

## 🔐 Environment Variables

If deploying the full version with API keys:

### Vercel
```bash
# In Vercel dashboard
Project Settings → Environment Variables
Add: VITE_ANTHROPIC_API_KEY = your_key_here
```

### Netlify
```bash
# In Netlify dashboard
Site Settings → Environment Variables
Add: VITE_ANTHROPIC_API_KEY = your_key_here
```

### Local Development
```bash
# Create .env file
echo "VITE_ANTHROPIC_API_KEY=your_key_here" > .env
```

---

## 🐛 Troubleshooting

### Build Fails

```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
npm run build
```

### Port Already in Use

```bash
# Kill process on port 3000
# Mac/Linux:
lsof -ti:3000 | xargs kill -9

# Windows:
netstat -ano | findstr :3000
taskkill /PID <PID> /F
```

### Git Push Rejected

```bash
# Pull latest changes first
git pull origin main --rebase
git push origin main
```

---

## 📞 Support

Need help deploying?

- 📧 Email: support@capitalcompass.ai
- 💬 Discord: [Join our community]
- 📖 Docs: [Full documentation]
- 🐛 Issues: [GitHub Issues](https://github.com/YOUR-USERNAME/capital-compass/issues)

---

## ✅ Deployment Checklist

- [ ] All files copied from artifacts
- [ ] `npm install` runs successfully
- [ ] `npm run dev` works locally
- [ ] `npm run build` completes without errors
- [ ] GitHub repository created
- [ ] Code pushed to GitHub
- [ ] Deployment platform chosen
- [ ] Site deployed and accessible
- [ ] Custom domain configured (optional)
- [ ] Analytics added (optional)
- [ ] SSL/HTTPS enabled
- [ ] Test all features on live site

---

**🎉 Congratulations! Your Capital Compass platform is now live!**

Share your link and start helping people navigate their investment future! 🧭
