# 🚀 AUTOMATIC JEWELRY PRICING SYSTEM
## Complete Setup Guide for Client Handover

---

## 🎯 What This System Does

Your client will have a **fully automatic** pricing system:

### Client's Experience:
1. Client opens Shopify admin
2. Client goes to: Content → Metaobjects → Metal Price
3. Client updates "Price Per Gram" for any metal
4. Client clicks Save
5. **🎉 ALL PRODUCTS UPDATE AUTOMATICALLY (within 30 seconds)**

**No scripts to run!**
**No technical knowledge needed!**
**Completely automatic!**

---

## 🏗️ System Architecture

```
Client Updates Metal Rate in Shopify
         ↓
Shopify Webhook Triggered
         ↓
Your Server Receives Notification
         ↓
Server Calculates New Prices Automatically
         ↓
Server Updates All Products
         ↓
Done! (All Automatic - 20-30 seconds)
```

---

## 📋 What You Need

### 1. Hosting (Pick One):

**Option A: Heroku (Easiest - Recommended)**
- Cost: $7/month
- Setup: 15 minutes
- Perfect for beginners
- One-click deploy

**Option B: DigitalOcean**
- Cost: $6/month
- Setup: 30 minutes
- More control
- Good performance

**Option C: Railway.app**
- Cost: $5/month
- Setup: 10 minutes
- Modern platform
- Very easy

**Option D: Render**
- Cost: $7/month
- Setup: 15 minutes
- Free tier available
- Good for startups

---

## 🚀 DEPLOYMENT GUIDE

I'll show you **Heroku** (easiest) and **DigitalOcean** (more control)

---

## 📦 OPTION 1: DEPLOY TO HEROKU (RECOMMENDED)

### Step 1: Create Heroku Account (5 min)

1. Go to https://heroku.com
2. Click "Sign Up"
3. Create free account
4. Verify email

### Step 2: Install Heroku CLI (2 min)

**On Windows:**
- Download from: https://devcenter.heroku.com/articles/heroku-cli
- Run installer

**On Mac:**
```bash
brew tap heroku/brew && brew install heroku
```

### Step 3: Prepare Your Code (2 min)

1. Extract the `automatic-pricing-system` folder
2. Open terminal in that folder
3. Initialize git:

```bash
cd automatic-pricing-system
git init
git add .
git commit -m "Initial commit"
```

### Step 4: Create Heroku App (3 min)

```bash
# Login to Heroku
heroku login

# Create new app
heroku create your-jewelry-pricing-system

# Add buildpack
heroku buildpacks:set heroku/nodejs
```

### Step 5: Configure Environment Variables (5 min)

```bash
# Set Shopify credentials
heroku config:set SHOPIFY_SHOP=f0a486-rn.myshopify.com
heroku config:set SHOPIFY_ACCESS_TOKEN=your_token_here
heroku config:set SHOPIFY_WEBHOOK_SECRET=your_webhook_secret_here
heroku config:set API_KEY=your_secure_random_key_here
```

### Step 6: Deploy! (2 min)

```bash
git push heroku master
```

**Your app is now live!**
- URL: `https://your-jewelry-pricing-system.herokuapp.com`

### Step 7: Configure Shopify Webhook (5 min)

1. Go to Shopify Admin
2. Settings → Notifications → Webhooks
3. Click "Create webhook"
4. Configure:
   - Event: **Metaobject update**
   - Format: **JSON**
   - URL: `https://your-jewelry-pricing-system.herokuapp.com/webhooks/metaobject-update`
   - API version: **2024-01**
5. Click "Save"

### Step 8: Get Webhook Secret

1. After creating webhook, click on it
2. Copy the **Webhook signing secret**
3. Update Heroku config:

```bash
heroku config:set SHOPIFY_WEBHOOK_SECRET=whsec_xxxxxxxxxxxxx
```

### Step 9: Test It! (2 min)

1. Go to Shopify: Content → Metaobjects → Metal Price
2. Click any metal (e.g., Gold 24K)
3. Change "Price Per Gram" (e.g., 65.50 → 66.00)
4. Click Save
5. Wait 30 seconds
6. Check a product → Price should be updated!

✅ **System is live and automatic!**

---

## 💻 OPTION 2: DEPLOY TO DIGITALOCEAN

### Step 1: Create DigitalOcean Account

1. Go to https://digitalocean.com
2. Sign up
3. Add payment method

### Step 2: Create Droplet

1. Click "Create" → "Droplets"
2. Choose:
   - Ubuntu 22.04 LTS
   - Basic plan: $6/month
   - Datacenter: Closest to you
3. Add SSH key (or use password)
4. Click "Create Droplet"

### Step 3: Connect to Server

```bash
ssh root@your_droplet_ip
```

### Step 4: Install Node.js

```bash
# Update system
apt update && apt upgrade -y

# Install Node.js
curl -fsSL https://deb.nodesource.com/setup_18.x | bash -
apt install -y nodejs

# Verify
node --version
npm --version
```

### Step 5: Install PM2 (Process Manager)

```bash
npm install -g pm2
```

### Step 6: Upload Your Code

**Option A: Using Git**
```bash
cd /var/www
git clone your_repository_url automatic-pricing-system
cd automatic-pricing-system
npm install
```

**Option B: Using SCP**
```bash
# On your computer
scp -r automatic-pricing-system root@your_droplet_ip:/var/www/
```

### Step 7: Configure Environment

```bash
cd /var/www/automatic-pricing-system
nano .env
```

Add:
```
SHOPIFY_SHOP=f0a486-rn.myshopify.com
SHOPIFY_ACCESS_TOKEN=your_token
SHOPIFY_WEBHOOK_SECRET=your_webhook_secret
API_KEY=your_api_key
PORT=3000
```

Save: Ctrl+X, Y, Enter

### Step 8: Start with PM2

```bash
pm2 start server.js --name jewelry-pricing
pm2 save
pm2 startup
```

### Step 9: Install Nginx (Reverse Proxy)

```bash
apt install -y nginx

# Configure Nginx
nano /etc/nginx/sites-available/default
```

Replace content with:
```nginx
server {
    listen 80;
    server_name your_droplet_ip;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

```bash
# Restart Nginx
systemctl restart nginx
```

### Step 10: Configure Shopify Webhook

Same as Heroku Step 7, but use:
- URL: `http://your_droplet_ip/webhooks/metaobject-update`

✅ **System is live!**

---

## 📊 CLIENT INSTRUCTIONS

### For Your Client (Super Simple):

**Daily Workflow:**

1. **Morning: Update Metal Rates (2 minutes)**
   ```
   1. Open Shopify Admin
   2. Click "Content"
   3. Click "Metaobjects"
   4. Click "Metal Price"
   5. Click on any metal (e.g., "Gold 24K")
   6. Update "Price Per Gram" field
   7. Click "Save"
   8. Done! Products update automatically!
   ```

2. **Wait 30 seconds**
   - System processes automatically
   - All products update

3. **Verify (optional)**
   - Check 1-2 products
   - Prices should be updated

**That's it! No scripts, no coding, no terminal!**

---

## 🎯 What Client Sees

### Before (Manual):
```
❌ Update metal rate
❌ Calculate each product price manually
❌ Update each product individually
❌ Takes 30-60 minutes
❌ Risk of errors
```

### After (Automatic):
```
✅ Update metal rate in one place
✅ Click Save
✅ Wait 30 seconds
✅ All products updated automatically
✅ Takes 2 minutes total
✅ Zero errors
```

---

## 🔍 MONITORING & MAINTENANCE

### Check System Status

**Dashboard:**
Visit: `https://your-app-url.herokuapp.com`

Shows:
- System status
- Last update time
- Active webhooks

**Logs (Heroku):**
```bash
heroku logs --tail
```

**Logs (DigitalOcean):**
```bash
pm2 logs jewelry-pricing
```

### Health Check

Visit: `https://your-app-url.herokuapp.com/health`

Should show:
```json
{
  "status": "ok",
  "service": "Automatic Jewelry Pricing System",
  "timestamp": "2025-11-05T10:30:00.000Z"
}
```

---

## 🛠️ TROUBLESHOOTING

### Products Not Updating?

**Check 1: Webhook Status**
```
Shopify Admin
  → Settings
  → Notifications
  → Webhooks
  → Check last delivery status
```

**Check 2: Server Running**
```bash
# Heroku
heroku ps

# DigitalOcean
pm2 status
```

**Check 3: Logs**
```bash
# Heroku
heroku logs --tail

# DigitalOcean
pm2 logs jewelry-pricing
```

### Manual Trigger (Backup)

If automatic updates fail, use manual API:

```bash
curl -X POST https://your-app-url.herokuapp.com/api/update-prices \
  -H "X-API-Key: your_api_key_here"
```

---

## 💰 COSTS

### Monthly Hosting Costs:

| Platform | Cost | Features |
|----------|------|----------|
| **Heroku** | $7/mo | Easiest, auto-scaling |
| **DigitalOcean** | $6/mo | More control |
| **Railway** | $5/mo | Modern, simple |
| **Render** | $7/mo | Free tier available |

**Recommended for Client: Heroku ($7/month)**
- Easiest to maintain
- Automatic updates
- Good support
- Professional

---

## 📋 HANDOVER CHECKLIST

Before handing to client:

- ✅ System deployed and running
- ✅ Webhooks configured in Shopify
- ✅ Test completed (update rate → products update)
- ✅ Client instructions document created
- ✅ Monitor dashboard accessible
- ✅ Backup manual trigger configured
- ✅ Client trained on updating metal rates
- ✅ Support contact info provided

---

## 📞 CLIENT SUPPORT

### If Client Has Issues:

**Problem: Products not updating**
1. Check webhook deliveries in Shopify
2. Check server logs
3. Try manual trigger
4. Contact support

**Problem: Wrong prices**
1. Verify metal rates in Shopify
2. Check product metafields
3. Rerun update manually
4. Review calculation formula

---

## 🎓 TRAINING YOUR CLIENT

### 15-Minute Training Session:

**Minute 1-3: Show Current System**
- Where metal rates are stored
- Where products are

**Minute 4-8: Demonstrate Update**
- Update one metal rate
- Show it saves
- Wait 30 seconds
- Show product price changed

**Minute 9-12: Let Client Try**
- Client updates a rate
- Client saves
- Client verifies update

**Minute 13-15: Q&A**
- Answer questions
- Show monitoring dashboard
- Provide support contact

---

## ✅ SUCCESS CRITERIA

System is ready for client when:

- ✅ Client can update metal rates easily
- ✅ Products update automatically within 30 seconds
- ✅ No manual scripts needed
- ✅ System runs 24/7 reliably
- ✅ Monitoring dashboard works
- ✅ Client understands the process
- ✅ Backup manual trigger available

---

## 🎉 FINAL NOTES

**For Client:**
- System is professional and automatic
- No technical knowledge required
- Works 24/7
- Updates in 30 seconds
- Reliable and tested

**For You:**
- Easy to deploy (15-30 min)
- Low maintenance
- Professional solution
- Client will love it!

---

## 📦 FILES INCLUDED

1. `server.js` - Main application with webhook handling
2. `.env.example` - Configuration template
3. `package.json` - Dependencies
4. This deployment guide

---

**Ready to deploy? Start with Heroku (easiest) or DigitalOcean (more control)!**

Need help with deployment? Let me know! 🚀
