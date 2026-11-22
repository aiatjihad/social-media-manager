# 🌐 SocialHub - Multi-Platform Social Media Manager

**একটি ওয়েবসাইটে YouTube, Instagram ও TikTok একসাথে ম্যানেজ করুন।**

---

## ✨ ফিচারস

- 📺 **১২টি YouTube চ্যানেল** সংযোগ ও একসাথে পোস্ট
- 📸 **২টি Instagram পেজ** ম্যানেজমেন্ট
- 🎵 **TikTok অ্যাকাউন্ট** সংযোগ
- 🚀 **একক ক্লিকে** সব প্ল্যাটফর্মে পোস্ট
- ⏰ **শিডিউল পোস্টিং** — ভবিষ্যৎ সময় নির্ধারণ
- 📁 **মাল্টি-ফাইল আপলোড** — একসাথে অনেক ভিডিও
- 📊 **ড্যাশবোর্ড** — সব কিছু এক নজরে
- 🎨 **সুন্দর ডার্ক UI** — মোবাইল ফ্রেন্ডলি

---

## 🚀 শুরু করুন

### ১. প্রথমবার চালু করুন

```bash
cd social-media-manager
chmod +x start.sh
./start.sh
```

তারপর ব্রাউজারে যান: **http://localhost:3000**

**লগইন:** `admin` / `admin123`

---

### ২. API Keys সেট করুন (OAuth এর জন্য)

`backend/.env` ফাইল খুলুন এবং আপনার API keys দিন:

#### YouTube (Google Cloud Console)
1. https://console.cloud.google.com → New Project
2. APIs & Services → Enable "YouTube Data API v3"
3. Credentials → OAuth 2.0 Client ID → Web Application
4. Redirect URI: `http://localhost:5000/api/auth/youtube/callback`
5. `.env` তে `YOUTUBE_CLIENT_ID` ও `YOUTUBE_CLIENT_SECRET` দিন

#### Instagram (Meta Developer)
1. https://developers.facebook.com → New App → Consumer
2. Instagram Basic Display → Add Platform → Website
3. Valid OAuth Redirect URIs: `http://localhost:5000/api/auth/instagram/callback`
4. `.env` তে `INSTAGRAM_CLIENT_ID` ও `INSTAGRAM_CLIENT_SECRET` দিন

#### TikTok (TikTok Developer)
1. https://developers.tiktok.com → New App
2. Products → Login Kit, Video Upload
3. Redirect URI: `http://localhost:5000/api/auth/tiktok/callback`
4. `.env` তে `TIKTOK_CLIENT_KEY` ও `TIKTOK_CLIENT_SECRET` দিন

---

### ৩. Manual অ্যাকাউন্ট (টেস্টিং এর জন্য)

API keys ছাড়াও অ্যাকাউন্ট যোগ করা যায়:
- Accounts পেজে যান
- "অ্যাকাউন্ট যোগ" বাটনে ক্লিক করুন
- প্ল্যাটফর্ম ও নাম দিন

> **নোট:** Manual অ্যাকাউন্টে পোস্ট locally রেকর্ড হয়, আসলে পাঠানো হয় না।

---

## 📁 প্রজেক্ট স্ট্রাকচার

```
social-media-manager/
├── backend/          # Node.js + Express API
│   ├── src/
│   │   ├── index.js       # মেইন সার্ভার
│   │   ├── routes/        # API রুটস
│   │   ├── services/      # পাবলিশ, DB, শিডিউলার
│   │   └── middleware/    # Auth
│   ├── uploads/           # আপলোড ফাইল (auto-created)
│   ├── db.json            # ডেটাবেজ (auto-created)
│   └── .env               # API Keys
├── frontend/         # React App
│   └── src/
│       ├── pages/         # 6টি পেজ
│       ├── components/    # Layout, Sidebar
│       ├── context/       # Auth Context
│       └── hooks/         # useApi
└── start.sh          # এক ক্লিকে চালু
```

---

## 🌐 GitHub Pages এ Deploy

```bash
cd frontend
npm run build
# তারপর build/ ফোল্ডার GitHub Pages এ আপলোড করুন
```

> **নোট:** GitHub Pages এ শুধু Frontend চলবে। Backend এর জন্য Railway, Render বা Heroku ব্যবহার করুন।

---

## 🛡️ Security নোট

- `.env` ফাইল কখনো GitHub এ আপলোড করবেন না
- Production এ `JWT_SECRET` পরিবর্তন করুন
- HTTPS ব্যবহার করুন production এ
