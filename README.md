# CS2 Hot Take Widget

A channel points OBS overlay that generates spicy AI CS2 hot takes when viewers redeem a reward. Built for Twitch streamers — no API keys required for viewers, just a Twitch account and a free Twitch app registration.

![OBS Browser Source](https://img.shields.io/badge/OBS-Browser%20Source-orange) ![Free](https://img.shields.io/badge/Cost-Free-green)

---

## How It Works

1. A viewer redeems your channel points reward
2. The widget catches the redemption via Twitch EventSub
3. An AI generates a short, spicy CS2 hot take
4. A styled quote card slides in on stream and auto-dismisses after 12 seconds

---

## Setup

### Step 1 — Register a Twitch App

1. Go to [dev.twitch.tv/console](https://dev.twitch.tv/console)
2. Click **Register Your Application**
3. Fill in:
   - **Name** — anything (e.g. `hottake-widget`)
   - **OAuth Redirect URLs** — the URL of this widget page (e.g. `https://yourusername.github.io/hottake-widget/`)
   - **Category** — Other
4. Click **Create**
5. Click **Manage** on your new app and copy the **Client ID**

### Step 2 — Configure the Widget

1. Open the widget page in your browser
2. Enter your **Client ID** from Step 1
3. Enter your **Reward Title** — must exactly match the name of your channel points reward
4. Click **Connect with Twitch**
5. Authorize the app on the Twitch login page
6. You'll be redirected back — the widget connects automatically
7. **Bookmark the URL** — it contains your saved credentials

### Step 3 — Create the Channel Points Reward

1. Go to your Twitch **Creator Dashboard → Viewer Rewards → Channel Points → Manage Rewards**
2. Click **+** to add a custom reward
3. Name it exactly what you entered in the widget (e.g. `CS2 Hot Take`)
4. Set a point cost
5. Save

### Step 4 — Add to OBS

1. In OBS, add a **Browser Source**
2. Paste your bookmarked widget URL
3. Set width to **600** and height to **160**
4. Check **Refresh browser when scene becomes active**
5. Done

---

## Testing

With the widget open in a browser, press **T** to fire a test hot take without needing a redemption.

Press **Escape** to dismiss a card early.

---

## Hosting on GitHub Pages

1. Fork or create a repo
2. Add `index.html` (the widget file) to the root
3. Go to **Settings → Pages → Source → main branch** → Save
4. Your widget URL will be `https://yourusername.github.io/your-repo-name/`
5. Use this URL as the OAuth Redirect URL in your Twitch app and in OBS

---

## Re-authenticating / Changing Settings

The widget saves your credentials to the URL hash. To reconfigure:

1. Clear the URL hash (delete everything after `#` in the address bar and reload)
2. The setup form will reappear
3. Re-enter your settings and reconnect

---

## FAQ

**Does this cost anything?**
No. The AI generation runs on a shared Cloudflare Worker backed by Groq's free tier.

**Will it work on my channel or just the developer's?**
It works on your channel. Each streamer authorizes with their own Twitch account and the widget subscribes to their channel's redemptions.

**Does the reward need a text input?**
No — leave "Require Viewer to Enter Text" off.

**The widget is blank in OBS — is it broken?**
The background is transparent by design. It only shows content when a redemption fires. Press T in the browser source preview to test it.

**My redemptions aren't triggering it**
Make sure the reward title in the widget settings exactly matches your Twitch reward name (case-insensitive). Also ensure your Twitch app's OAuth Redirect URL matches the widget URL exactly including trailing slash.

---

## Credits

Built by [Dexterity](https://twitch.tv/dexterity_cs) — part of the [dexteritycs stream tools](https://github.com/dexteritycs) collection.
