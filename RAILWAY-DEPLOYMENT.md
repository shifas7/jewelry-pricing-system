# 🚂 DEPLOY TO RAILWAY.APP (FREE $5/month)
## 10-Minute Deployment Guide

---

## ✅ Why Railway.app?

- 🆓 **$5 free credit/month** (enough for small apps)
- ✅ Super easy (10 minutes)
- ✅ **Always-on** (no sleep mode!)
- ✅ Modern platform
- ✅ GitHub integration
- ✅ Perfect for production

**Better than Render for:** Always-on, no sleep delays

---

## 📋 STEP-BY-STEP DEPLOYMENT

### Step 1: Create Railway Account (2 min)

1. Go to https://railway.app
2. Click **"Start a New Project"**
3. Sign up with GitHub (recommended)
4. ✅ Account created!

**Note:** You get $5 credit free each month!

---

### Step 2: Create New Project (1 min)

1. Click **"New Project"**
2. Select **"Deploy from GitHub repo"**
3. Connect your GitHub account
4. Select your repository

**OR**

1. Click **"Empty Project"**
2. Add service manually

---

### Step 3: Deploy (2 min)

#### Option A: From GitHub

1. Select **"Deploy from GitHub repo"**
2. Choose: `jewelry-pricing-system`
3. Railway auto-detects Node.js
4. Click **"Deploy"**

#### Option B: From CLI

```bash
# Install Railway CLI
npm install -g @railway/cli

# Login
railway login

# Initialize
railway init

# Deploy
railway up
```

---

### Step 4: Add Environment Variables (3 min)

1. Click your service
2. Go to **"Variables"** tab
3. Click **"New Variable"**
4. Add these:

```
SHOPIFY_SHOP=f0a486-rn.myshopify.com
SHOPIFY_ACCESS_TOKEN=your_access_token_here
SHOPIFY_WEBHOOK_SECRET=your_webhook_secret_here
API_KEY=your_secure_random_key
PORT=3000
NODE_ENV=production
```

**Or use Railway CLI:**
```bash
railway variables set SHOPIFY_SHOP=f0a486-rn.myshopify.com
railway variables set SHOPIFY_ACCESS_TOKEN=your_token
railway variables set SHOPIFY_WEBHOOK_SECRET=your_secret
railway variables set API_KEY=your_key
```

---

### Step 5: Generate Domain (1 min)

1. Go to **"Settings"** tab
2. Click **"Generate Domain"**
3. You'll get: `https://your-app.up.railway.app`

✅ **Your URL is ready!**

---

### Step 6: Configure Shopify Webhook (3 min)

1. Shopify Admin → Settings → Notifications → Webhooks
2. Click **"Create webhook"**
3. Configure:

```
Event: Metaobject update
Format: JSON
URL: https://your-app.up.railway.app/webhooks/metaobject-update
API version: 2024-01
```

4. Click **"Save"**
5. Copy webhook secret
6. Update Railway variable: `SHOPIFY_WEBHOOK_SECRET`

---

### Step 7: Test (2 min)

1. Visit: `https://your-app.up.railway.app/health`
   - Should show: `{ "status": "ok" }`

2. Update metal rate in Shopify
3. Wait 10-20 seconds
4. Check product → Updated! ✅

---

## 🎯 Key Benefits

### Always-On:
- ✅ NO sleep mode
- ✅ Instant responses
- ✅ No wake-up delays
- ✅ Professional performance

### Auto-Scaling:
- ✅ Handles traffic spikes
- ✅ Reliable uptime
- ✅ Fast deployments

---

## 📊 Monitoring

### View Logs:
```bash
railway logs
```

**Or in Dashboard:**
1. Click your service
2. Go to **"Deployments"** tab
3. Click **"View Logs"**

### Check Metrics:
1. Dashboard → Your service
2. See CPU, memory, bandwidth usage

---

## 💰 Pricing

### Free Tier:
- ✅ $5 credit/month
- ✅ ~150 hours uptime
- ✅ Good for development

**Typical usage:**
- Small app: $3-5/month
- Your app likely: $2-3/month
- FREE with $5 monthly credit! ✅

### After Free Credit:
- Pay only for what you use
- ~$5/month for always-on
- No surprise bills
- Cancel anytime

---

## 🔄 Auto-Deployment

**From GitHub:**
```
Push to main branch
  ↓
Railway auto-detects
  ↓
Builds & deploys automatically
  ↓
Live in 1-2 minutes!
```

---

## ⚡ Railway CLI Commands

### Deploy:
```bash
railway up
```

### View Logs:
```bash
railway logs
```

### Open Dashboard:
```bash
railway open
```

### Run Locally:
```bash
railway run node server.js
```

---

## 🎯 Best Practices

### 1. Use GitHub Integration
- Automatic deploys
- Version control
- Easy rollbacks

### 2. Monitor Usage
- Check dashboard monthly
- Stay within free credit
- Optimize if needed

### 3. Set Alerts
- Railway email notifications
- Monitor uptime
- Track deployments

---

## 🆙 When to Upgrade

**Stay free if:**
- ✅ One client
- ✅ Low traffic
- ✅ Usage < $5/month

**Upgrade to paid if:**
- ⬆️ Multiple clients
- ⬆️ High traffic
- ⬆️ Need guarantees

---

## 🎉 Comparison

| Feature | Render Free | Railway Free |
|---------|-------------|--------------|
| **Cost** | FREE | $5 credit/mo |
| **Sleep mode** | YES (15 min) | NO ✅ |
| **Wake time** | ~30 sec | Instant |
| **Always-on** | NO | YES ✅ |
| **Best for** | Dev/hobby | Production |

---

## 🔧 Troubleshooting

### Deployment Failed?
```bash
railway logs
# Check for errors
```

### Need More Credit?
- Add payment method
- Get $10 free trial
- Only charged after credit used

### Variable Not Working?
```bash
railway variables
# Verify all variables set
```

---

## ✅ Success Checklist

- [ ] Railway account created
- [ ] Project deployed
- [ ] Variables configured
- [ ] Domain generated
- [ ] Webhook configured in Shopify
- [ ] Health check passes
- [ ] Test update successful
- [ ] Monitoring set up

---

## 🎊 You're Live!

**What you have:**
- ✅ Always-on server (no sleep!)
- ✅ $5 free credit/month
- ✅ Professional platform
- ✅ Auto-deployments
- ✅ Production-ready

**Total cost:** $0-5/month ✅

---

**Railway.app is PERFECT for your jewelry pricing system!** 🚂✨
