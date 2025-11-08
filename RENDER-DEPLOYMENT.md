# 🚀 DEPLOY TO RENDER.COM (FREE)
## 5-Minute Deployment Guide

---

## ✅ Why Render.com?

- 🆓 **100% FREE forever** (no credit card needed)
- ✅ Easy 5-minute setup
- ✅ Auto-deploys from GitHub
- ✅ HTTPS included
- ✅ Perfect for development & small production

**Note:** Free tier sleeps after 15 min inactivity (wakes in ~30 sec). Fine for this use case!

---

## 📋 STEP-BY-STEP DEPLOYMENT

### Step 1: Create Render Account (2 min)

1. Go to https://render.com
2. Click **"Get Started for Free"**
3. Sign up with GitHub (recommended) or email
4. Verify your email
5. ✅ Account created!

---

### Step 2: Prepare Your Code (3 min)

#### Option A: Using GitHub (Recommended)

1. Create a GitHub account (if you don't have one): https://github.com
2. Create a new repository: **jewelry-pricing-system**
3. Upload your files:
   - `server.js`
   - `package.json`
   - `.env.example` (rename to `.env` later)

4. Push to GitHub

#### Option B: Direct Upload

You can connect Render to your GitHub repo for automatic deployments.

---

### Step 3: Create Web Service (3 min)

1. In Render Dashboard, click **"New +"**
2. Select **"Web Service"**
3. Connect your GitHub repo (or paste Git URL)
4. Configure:

```
Name: jewelry-pricing-system
Environment: Node
Build Command: npm install
Start Command: node server.js
Plan: Free
```

5. Click **"Create Web Service"**

---

### Step 4: Add Environment Variables (2 min)

1. In your web service dashboard, go to **"Environment"**
2. Click **"Add Environment Variable"**
3. Add these:

```
SHOPIFY_SHOP = f0a486-rn.myshopify.com
SHOPIFY_ACCESS_TOKEN = your_access_token_here
SHOPIFY_WEBHOOK_SECRET = your_webhook_secret_here
API_KEY = your_secure_random_key
PORT = 10000
NODE_ENV = production
```

4. Click **"Save Changes"**

---

### Step 5: Get Your URL (1 min)

After deployment completes, you'll get a URL like:
```
https://jewelry-pricing-system.onrender.com
```

✅ **Your server is now LIVE!**

---

### Step 6: Configure Shopify Webhook (3 min)

1. Go to Shopify Admin
2. **Settings** → **Notifications** → **Webhooks**
3. Click **"Create webhook"**
4. Configure:

```
Event: Metaobject update
Format: JSON
URL: https://jewelry-pricing-system.onrender.com/webhooks/metaobject-update
API version: 2024-01
```

5. Click **"Save"**

---

### Step 7: Get Webhook Secret

1. Click on the webhook you just created
2. Copy the **"Webhook signing secret"** (starts with `whsec_`)
3. Go back to Render
4. Update environment variable:
   ```
   SHOPIFY_WEBHOOK_SECRET = whsec_xxxxxxxxxxxxx
   ```
5. Service will auto-redeploy

---

### Step 8: Test It! (2 min)

1. Visit: `https://your-app.onrender.com/health`
   - Should show: `{ "status": "ok" }`

2. Update a metal rate in Shopify
   - Content → Metaobjects → Metal Price
   - Change any price
   - Click Save

3. Wait 30-60 seconds (first wake-up might take 30 sec)

4. Check a product → Price should be updated!

✅ **IT'S WORKING!**

---

## 🎯 Important Notes

### About Free Tier Sleep Mode:

**What happens:**
- After 15 minutes of no requests, server sleeps
- First webhook after sleep takes ~30 seconds to wake
- Subsequent updates are instant

**Is this a problem?**
- ❌ NO! Because:
  - Client updates rates once per day (morning)
  - First update wakes server (30 sec)
  - Products update normally
  - Perfect for this use case!

**How to avoid sleep (optional):**
- Add a cron job to ping server every 14 minutes
- Keeps server awake 24/7
- I can show you how if needed

---

## 📊 Monitoring

### View Logs:

1. Go to Render Dashboard
2. Click your service
3. Click **"Logs"** tab
4. See real-time activity

### Check Health:

Visit: `https://your-app.onrender.com/health`

---

## 🔄 Auto-Deployment

**GitHub Integration:**
- Push to GitHub → Render auto-deploys
- No manual steps needed
- Changes live in 1-2 minutes

---

## 💰 Cost

**Free tier includes:**
- ✅ 750 hours/month free
- ✅ Unlimited deploys
- ✅ HTTPS/SSL
- ✅ Custom domains
- ✅ No credit card required

**Upgrade later (optional):**
- $7/month for always-on
- No sleep mode
- More resources

---

## ⚡ Quick Commands

### View Dashboard:
```
https://dashboard.render.com
```

### View Logs:
```
Dashboard → Your Service → Logs
```

### Manual Deploy:
```
Dashboard → Your Service → Manual Deploy
```

---

## 🎉 You're Done!

**What you have:**
- ✅ Free hosting (forever!)
- ✅ Automatic deployments
- ✅ HTTPS included
- ✅ Professional URL
- ✅ Easy to maintain

**Total time:** 15 minutes
**Total cost:** $0 ✅

---

## 🆙 Upgrade to Paid (Optional)

When ready for production:
- $7/month for always-on
- No sleep mode
- Better performance
- Still cheaper than competitors!

---

**Your jewelry pricing system is now LIVE and FREE!** 🎊
