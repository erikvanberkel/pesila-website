# Google Reviews Setup Guide

## 🎯 Quick Summary

Your website now has live Google Reviews integration! Follow these steps to activate it.

---

## 📋 Step-by-Step Setup

### Step 1: Get Your Google API Key

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project (or select existing):
   - Click "**Select a project**" → "**NEW PROJECT**"
   - Name: "Pesila Website"
   - Click "**CREATE**"

3. Enable the Places API:
   - Go to "**APIs & Services**" → "**Library**"
   - Search for "**Places API**"
   - Click "**ENABLE**"

4. Create API credentials:
   - Go to "**APIs & Services**" → "**Credentials**"
   - Click "**+ CREATE CREDENTIALS**" → "**API Key**"
   - **COPY THE API KEY** (you'll need this!)

5. **IMPORTANT:** Secure your API key:
   - Click the pencil icon to edit the key
   - Under "**Application restrictions**":
     - Select "**HTTP referrers (websites)**"
     - Click "**ADD AN ITEM**"
     - Add: `https://www.pesila.nl/*`
     - Add: `https://pesila.nl/*`
     - Add: `http://localhost:*` (for testing)
   - Under "**API restrictions**":
     - Select "**Restrict key**"
     - Check "**Places API**"
   - Click "**SAVE**"

### Step 2: Find Your Google Place ID

**Option A: Use Place ID Finder**
1. Go to [Google Place ID Finder](https://developers.google.com/maps/documentation/javascript/examples/places-placeid-finder)
2. Search for "**Pesila Thai Massage Rotterdam**"
3. Copy the **Place ID** (starts with `ChIJ...`)

**Option B: Search Manually**
1. Search Google for your business: "Pesila Thai Massage Rotterdam"
2. Look at the URL - the Place ID is in the URL parameters
3. Or use this tool: https://placeId.com/

### Step 3: ✅ Credentials Already Added!

**Good news!** Your API credentials are already configured:

- ✅ **API Key**: Added to the Google Maps script tag (line 14)
- ✅ **Place ID**: `ChIJayy_TwM1xEcRGWhh99q1o48` (line 1262)

The system is ready to fetch reviews!

### Step 4: ✅ CORS Issue - FIXED!

**Good news!** The implementation now uses the **Google Maps JavaScript API** which has no CORS issues.

The script is already added to your `<head>` section:
```html
<script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&libraries=places&loading=async"></script>
```

This official API:
- ✅ No CORS problems
- ✅ More reliable than proxies
- ✅ Better performance
- ✅ Google's recommended approach

---

## 🧪 Testing

1. Open your website in a browser
2. Navigate to the "Recensies" section
3. Open browser console (F12)
4. Look for messages starting with "Google Reviews:"
   - ✅ "Google Maps API loaded, fetching reviews..." = API loaded successfully
   - ✅ "Fetched fresh data from API" = Working perfectly!
   - ℹ️ "Using cached data" = Using cache (efficient!)
   - ❌ "Failed to fetch" = Check API key restrictions or Place ID

---

## 🎨 What's Included

✅ **Automatic caching** - Reviews cached for 24 hours to minimize API calls
✅ **Fallback support** - Shows static reviews if API fails
✅ **Star ratings** - Visual star ratings for each review
✅ **Relative dates** - Shows "2 maanden geleden" etc.
✅ **Only positive reviews** - Filters to show 4+ star reviews only
✅ **Top 8 reviews** - Displays best reviews sorted by rating
✅ **Link to Google** - Button to see all reviews and write new ones
✅ **Responsive design** - Matches your existing card layout

---

## 💰 Pricing & Limits

**Google Places API Free Tier:**
- 28,000 requests/month FREE
- $0.017 per request after that

**Your estimated usage:**
- With 24-hour caching: ~30 requests/month
- Well within free tier! ✅

---

## 🔧 Troubleshooting

### Reviews not showing?
1. Check browser console for error messages
2. Verify API key is correct
3. Verify Place ID is correct
4. Check API key restrictions allow your domain
5. Make sure Places API is enabled in Google Cloud

### CORS errors?
- ✅ **FIXED!** Now using Google Maps JavaScript API (no CORS issues)

### Want to customize?
- **Number of reviews**: Change `slice(0, 8)` on line 1385
- **Minimum rating**: Change `filter(review => review.rating >= 4)` on line 1383
- **Cache duration**: Change `CACHE_DURATION` on line 1265
- **Styling**: Modify CSS classes starting at line 296

---

## 🚀 Status: READY TO GO! ✅

Your Google Reviews integration is **fully configured and ready**!

### What's Already Done:
- ✅ API key configured (in script tag, line 14)
- ✅ Place ID configured (ChIJayy_TwM1xEcRGWhh99q1o48)
- ✅ Google Maps JavaScript API integrated
- ✅ CORS issue fixed
- ✅ 24-hour caching enabled
- ✅ Fallback to static reviews

### What You Need to Do:
1. **Verify API key restrictions** in Google Cloud Console:
   - Make sure `https://www.pesila.nl/*` is added to HTTP referrers
   - Make sure Places API is enabled
2. **Test the website**: Open in browser and check console for success messages
3. **Deploy to production**: Push to GitHub and watch it go live!
4. **Monitor**: Check console logs first few times to ensure it's working

---

## 🆘 Need Help?

If you run into issues:
- Check the browser console for detailed error messages
- Verify API key restrictions in Google Cloud Console
- Make sure Places API is enabled
- Clear browser cache and localStorage
- Check that your API key hasn't expired or been rate-limited

Still stuck? Check these console messages for clues:
- "Google Maps API not loaded" = Script tag issue
- "Failed to fetch" = API restrictions or invalid Place ID
- No messages = JavaScript error (check console for red errors)

---

**Generated by Claude Code on 2025-12-02**
**Last updated: 2025-12-02 - CORS issue fixed, fully configured**
