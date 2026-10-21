[Uploading README.md…]()
# ✈️ Telegram Channels Directory — AkMovieVerse

A high-performance, responsive web directory for Telegram channels featuring a **Sunset Glassmorphism UI**, a **7-second circular countdown redirect page**, a **Load More** pagination system, and an **Admin reporting bot integration**.

Built with **Zero Build Step** (Pure HTML + Tailwind CSS CDN + Vanilla JavaScript) for instant static deployment on **Vercel** or **GitHub Pages**.

---

## ✨ Features

- 🌅 **Sunset Glassmorphism Design:** Dark, modern theme with glowing gradients and ambient background blobs.
- ⭐ **Sticky Main Channel Banner:** Permanent top bar highlighting `@AkMovieVerse` across every page scroll.
- ⏱️ **7-Second Countdown Redirect Page (`redirect.html`):**
  - Smooth animated SVG circular countdown ring.
  - Dynamically displays the channel's actual poster image, name, and emoji.
  - Includes an **"Open Now ➜"** skip button and progress bar.
- ⚡ **"Load More" Dynamic Loading:** Displays 6 channels initially; loads remaining channels in batches of 6 with an animated trigger button.
- 📢 **Live Marquee Ticker:** Continuously scrolls channel names at the top.
- 🔢 **Animated Count-Up Statistics:** Stats counter smoothly counts up to the total number of channels on page load.
- 👁️ **Hidden Channel Toggle:** Toggle channels between `hidden: false` (visible) and `hidden: true` (draft/hidden) without deleting them.
- 🤖 **Admin Broken Link Reporting (`@AK_ownerbot`):**
  - Floating action pill in bottom-right corner across all pages.
  - Integrated footer links to report broken links or banned channels.
- 🔒 **Right-Click & Inspect Protection:** Prevents right-click context menu and common inspection shortcuts (`F12`, `Ctrl+U`, `Ctrl+Shift+I`).
- 🌐 **Rich Social Previews (Open Graph):** Custom metadata for cards on WhatsApp, Telegram, and Twitter.
- 🎨 **Custom SVG Favicon:** Sunset orange Telegram paper-plane icon.

---

## 📁 Project Structure

```
├── index.html        # Main landing page (Channel cards, ticker, stats, load more)
├── redirect.html     # 7-second countdown intermediary redirect page
└── README.md         # Documentation
```

---

## 🔧 Adding & Editing Channels

All channels are defined in the `channels` array inside [`index.html`](index.html).

To add or update a channel, edit or add an object in the array:

```javascript
{
  name:    "Channel Name",                                    // Channel title
  desc:    "Short 1-line description of the channel.",         // Channel description
  emoji:   "🎬",                                              // Fallback icon
  image:   "https://i.ibb.co/your-image.jpg",                 // Poster image URL (or "" for gradient fallback)
  members: "10.5K",                                           // Subscriber count
  link:    "https://t.me/+your_invite_link",                  // Telegram invite URL
  isNew:   true,                                              // Set true for "NEW" badge, false to hide
  hidden:  false,                                             // Set false to show, true to hide
},
```

### 💡 Pro Tips:
- **Hide a channel temporarily:** Set `hidden: true`. The channel will be hidden from the grid, ticker, and stats count.
- **Show a channel:** Set `hidden: false`.
- **Add a poster:** Paste any image URL into `image`. If left empty `""`, an animated gradient fallback with the channel's `emoji` will be displayed automatically.

---

## 🌐 Deploy to Vercel (1-Click)

1. Push this repository to **GitHub**:
   ```bash
   git add .
   git commit -m "Update Telegram directory"
   git push origin main
   ```
2. Log in to [vercel.com](https://vercel.com).
3. Click **Add New Project** → Import your repository (`mychannels`).
4. Click **Deploy**. Vercel will automatically host it as a high-speed static website with zero configuration needed.

---

## 🛠️ Customization

- **Admin Bot Link:** Configured for [`https://t.me/AK_ownerbot`](https://t.me/AK_ownerbot) in `index.html` and `redirect.html`.
- **Main Channel Link:** Configured for [`https://t.me/AkMovieVerse`](https://t.me/AkMovieVerse) in the top sticky bar.
- **Batch Size:** Configured to 6 channels per batch (`const BATCH_SIZE = 6;` in `index.html`).

---

© 2025–2026 My Telegram Channels · Powered by AkMovieVerse
