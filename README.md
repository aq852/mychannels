# 📡 Telegram Channels Hub (Python/Flask)

A beautiful, secure Telegram channel directory built with **Python + Flask**.

> **🔒 Security**: Actual Telegram invite links are **never exposed** to the browser. Links live only in server environment variables. Users are redirected server-side — the link never touches the client.

## ✨ Features
- 🎨 Dark glassmorphism UI (Tailwind CDN — no build step!)
- 🔍 Live search by name, tag, category
- 🏷️ Category filter pills
- ⭐ Featured channels section
- 🔒 Server-side redirect (links hidden in env vars)
- 📱 Fully responsive
- ⚡ Rate limiting on join endpoint
- 🚀 One-click deploy on Vercel

---

## 🚀 Local Setup

### 1. Install Python (if not installed)
Download from [python.org](https://python.org)

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Set up your secret links
```bash
copy .env.example .env.local
```
Edit `.env.local` and replace the placeholder URLs with your actual Telegram invite links.

### 4. Run locally
```bash
python api/index.py
```
Open [http://localhost:3000](http://localhost:3000)

---

## 🔧 Adding Your Channels

### Step 1 — Add public info to `data/channels.py`
```python
{
    "id": "my_channel",          # unique ID (no spaces)
    "name": "My Channel",
    "description": "About my channel...",
    "category": "Tech",
    "members": "1.2K",
    "emoji": "🔥",
    "tags": ["Tag1", "Tag2"],
    "featured": False,
}
```

### Step 2 — Add the secret link to `.env.local`
```
CHANNEL_LINK_MY_CHANNEL=https://t.me/+xxxxxxxxxxxxxxxx
```
> Rule: ID in env var = channel `id` field, uppercased, underscores kept.

---

## 🌐 Deploy to Vercel (Free)

1. Push this repo to GitHub
2. Go to [vercel.com](https://vercel.com) → **New Project** → Import your repo
3. Vercel auto-detects Python from `vercel.json`
4. Go to **Project → Settings → Environment Variables**
5. Add each `CHANNEL_LINK_XXX` variable with its real Telegram link
6. Click **Deploy** ✅

---

## 🔐 How the Security Works

```
User clicks "Join"
      ↓
Browser calls GET /join/channel_id
      ↓
Flask reads CHANNEL_LINK_CHANNEL_ID from environment
      ↓
Flask returns HTTP 302 redirect → Telegram
      ↓
User lands on Telegram — actual link NEVER sent to browser
```

Even if someone inspects your HTML/JS, they will only see `/join/channel_id` — never the real `t.me/+...` link.
