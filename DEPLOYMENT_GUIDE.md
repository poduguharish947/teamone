# Deployment Guide

This guide provides step-by-step instructions for deploying the Course Management System to GitHub and various hosting platforms.

## 📦 Prerequisites

1. **Git installed** - Download from [git-scm.com](https://git-scm.com/)
2. **GitHub account** - Sign up at [github.com](https://github.com/)
3. **Node.js** (for full-stack deployment) - Download from [nodejs.org](https://nodejs.org/)

## 🚀 GitHub Deployment

### Step 1: Install Git (if not already installed)

Download and install Git from [git-scm.com](https://git-scm.com/download/win)

After installation, verify by opening PowerShell and running:
```powershell
git --version
```

### Step 2: Configure Git

```powershell
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Step 3: Initialize Git Repository

```powershell
cd "c:\Users\Harish\OneDrive\Desktop"
git init
```

### Step 4: Stage Files

```powershell
git add .
```

### Step 5: Create Initial Commit

```powershell
git commit -m "Initial commit: Course Management System"
```

### Step 6: Create GitHub Repository

1. Go to [github.com](https://github.com) and log in
2. Click the "+" icon in the top right corner
3. Select "New repository"
4. Enter repository name: `course-management-system`
5. Add description: "A comprehensive full-stack course management system"
6. Choose "Public" or "Private"
7. **DO NOT** initialize with README (we already have one)
8. Click "Create repository"

### Step 7: Link Local Repository to GitHub

Replace `YOUR_USERNAME` with your actual GitHub username:

```powershell
git remote add origin https://github.com/YOUR_USERNAME/course-management-system.git
git branch -M main
git push -u origin main
```

### Step 8: Verify Deployment

Visit your repository at:
```
https://github.com/YOUR_USERNAME/course-management-system
```

## 🌐 Hosting Options

### Option 1: GitHub Pages (Standalone Version Only)

**Best for**: Demonstrating the frontend without backend

1. Go to your repository settings on GitHub
2. Navigate to "Pages" section
3. Select source: `main` branch
4. Choose root folder
5. Click "Save"
6. Your site will be available at: `https://YOUR_USERNAME.github.io/course-management-system/Project-Modern-Standalone.html`

**Note**: GitHub Pages only hosts static files. Use the standalone version (`Project-Modern-Standalone.html`).

### Option 2: Render (Full-Stack with Backend)

**Best for**: Full production deployment with database

1. **Push code to GitHub** (completed above)

2. **Deploy Backend on Render**:
   - Go to [render.com](https://render.com) and sign up
   - Click "New +" → "Web Service"
   - Connect your GitHub repository
   - Configure:
     - **Name**: course-management-backend
     - **Environment**: Node
     - **Build Command**: `cd backend && npm install`
     - **Start Command**: `cd backend && node server.js`
     - **Add Environment Variables**:
       - `PORT`: 3000
       - `MONGODB_URI`: (your MongoDB Atlas connection string)
   - Click "Create Web Service"

3. **Set up MongoDB Atlas**:
   - Go to [mongodb.com/atlas](https://www.mongodb.com/atlas)
   - Create free cluster
   - Create database user
   - Whitelist IP: `0.0.0.0/0` (allow all for Render)
   - Get connection string and add to Render environment variables

4. **Deploy Frontend**:
   - Use Render Static Site or GitHub Pages
   - Update API endpoints in frontend files to point to Render backend URL

### Option 3: Vercel (Frontend) + MongoDB Atlas (Database)

**Best for**: Fast frontend deployment with serverless backend

1. **Deploy to Vercel**:
   ```powershell
   npm install -g vercel
   vercel login
   vercel
   ```

2. **Configure**:
   - Follow prompts to link GitHub repository
   - Select root directory
   - Deploy standalone version or configure API routes

### Option 4: Heroku (Full-Stack)

**Best for**: Traditional full-stack deployment

1. **Install Heroku CLI**:
   - Download from [devcenter.heroku.com](https://devcenter.heroku.com/articles/heroku-cli)

2. **Deploy Backend**:
   ```powershell
   heroku login
   heroku create course-mgmt-backend
   git subtree push --prefix backend heroku main
   ```

3. **Configure MongoDB**:
   ```powershell
   heroku config:set MONGODB_URI="your-mongodb-atlas-uri"
   ```

## 🔧 Post-Deployment Configuration

### Update API Endpoints in Frontend

After deploying backend, update the API base URL in frontend files:

**Files to update**:
- `dashboard-modern.html`
- `dashboard-advanced.js`

**Change**:
```javascript
const API_BASE_URL = 'http://localhost:3000';
```

**To**:
```javascript
const API_BASE_URL = 'https://your-backend-url.onrender.com';
```

## 📱 Mobile/Responsive Testing

After deployment, test on:
- Desktop browsers (Chrome, Firefox, Edge, Safari)
- Mobile devices (iOS Safari, Chrome Mobile)
- Different screen sizes using browser DevTools

## 🔒 Security Considerations

1. **Never commit `.env` files** - Already in `.gitignore`
2. **Use environment variables** for sensitive data
3. **Enable HTTPS** - Most hosting platforms provide this
4. **Secure MongoDB** - Use MongoDB Atlas with proper authentication
5. **Update CORS settings** - Allow only your frontend domain in production

## 🐛 Troubleshooting

### Issue: Git push fails
**Solution**: Check authentication. Use Personal Access Token instead of password:
```powershell
git remote set-url origin https://YOUR_TOKEN@github.com/YOUR_USERNAME/course-management-system.git
```

### Issue: Backend not connecting to MongoDB
**Solution**: 
- Check MongoDB Atlas whitelist includes Render/Heroku IPs
- Verify connection string format
- Check environment variables are set correctly

### Issue: CORS errors
**Solution**: Update CORS configuration in `backend/server.js`:
```javascript
app.use(cors({
    origin: 'https://your-frontend-domain.com'
}));
```

## 📊 Monitoring

### Backend Health Check
Add to `backend/server.js`:
```javascript
app.get('/health', (req, res) => {
    res.json({ status: 'OK', timestamp: new Date() });
});
```

### Frontend Analytics
Consider adding:
- Google Analytics
- Sentry for error tracking
- LogRocket for session replay

## 🔄 Continuous Deployment

For automatic deployments on push to GitHub:

1. **Enable auto-deploy** in Render/Vercel/Netlify dashboard
2. Connect to GitHub repository
3. Select branch (usually `main`)
4. Configure build settings
5. Every push will trigger automatic deployment

## 📝 Maintenance

### Regular Updates
```powershell
# Update dependencies
cd backend
npm update

# Commit changes
git add .
git commit -m "Update dependencies"
git push origin main
```

### Backup Database
```powershell
# MongoDB Atlas provides automatic backups
# Or use mongodump for manual backups
mongodump --uri="your-mongodb-uri"
```

## 🎉 Success!

Your Course Management System is now deployed and accessible to the world!

**Next Steps**:
1. Share your repository link
2. Add demo credentials to README
3. Create GitHub Issues for feature requests
4. Set up GitHub Discussions for community
5. Add badges to README (build status, license, etc.)

---

For questions or issues, open a GitHub Issue in your repository.
