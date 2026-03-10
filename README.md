# 🛡️ ShieldDNS — Android Porn Blocker

A real **system-wide content blocker** for Android. Uses a local VPN to intercept all DNS queries — blocks adult content in Chrome, Firefox, Instagram, and every other app.

---

## ⚡ How It Works (Technical)

```
Your Phone App
     ↓  DNS query (e.g. "pornhub.com")
ShieldDNS VPN (local, tun0)
     ↓  Is it in blocklist?
    YES → Returns NXDOMAIN (blocked! 🚫)
     NO → Forwards to CleanBrowsing/Cloudflare DNS ✅
```

**No data leaves your device** — the VPN is 100% local.

---

## ✅ Features

| Feature | Description |
|---------|-------------|
| 🔒 System-wide blocking | Blocks in ALL apps via local VPN |
| 🌐 35+ built-in domains | Pornhub, Xvideos, XHamster, OnlyFans, etc. |
| ➕ Custom blocklist | Add any domain with one tap |
| 🔄 Auto-restart on boot | Survives phone restarts |
| 🔑 PIN protection | Settings locked behind 4-digit PIN |
| 🌐 3 DNS providers | CleanBrowsing, Cloudflare, OpenDNS |
| 🌙 Bedtime mode | Extra strict 10 PM – 6 AM |
| 🔍 Safe search | Forces Google/Bing safe search |
| 🚫 Block social media | Optional: block Instagram, TikTok, etc. |
| 🛡️ Device Admin | Prevents uninstall without PIN |

---

## 🏗️ How to Build (3 options)

### Option 1: Android Studio (Easiest, ~5 min)
1. Download & install **Android Studio**: https://developer.android.com/studio
2. Open this folder in Android Studio
3. Click the green ▶️ **Run** button (installs directly to your phone)
   — OR —
4. Build → **Generate Signed APK** for a shareable file

### Option 2: GitHub Actions (Auto-build, free)
1. Push this project to a new GitHub repo:
   ```bash
   git init
   git add .
   git commit -m "ShieldDNS v1.0"
   git remote add origin https://github.com/YOUR_USERNAME/ShieldDNS.git
   git push -u origin main
   ```
2. GitHub automatically builds the APK (takes ~3 minutes)
3. Go to **Actions** tab → Click the latest workflow run → Download **ShieldDNS-Debug** artifact
4. You get a ready `.apk` file!

### Option 3: Command Line (if Android SDK installed)
```bash
chmod +x gradlew
./gradlew assembleDebug
# APK at: app/build/outputs/apk/debug/app-debug.apk
```

---

## 📱 Install on Phone

After building, install the APK:
1. Enable **"Install from Unknown Sources"** in phone Settings
2. Transfer APK to phone (WhatsApp, USB, Google Drive)
3. Tap the APK file → Install
4. Open ShieldDNS → Tap **Activate Shield**
5. Accept the VPN permission popup ✅

---

## 🔧 Default Settings

| Setting | Default |
|---------|---------|
| PIN | **1234** (change immediately!) |
| DNS Provider | CleanBrowsing Family |
| Start on Boot | ON |
| Strict Mode | ON |
| Safe Search | ON |

---

## 🌐 DNS Providers Used

| Provider | Primary | Secondary | Specialty |
|----------|---------|-----------|-----------|
| **CleanBrowsing** | 185.228.168.168 | 185.228.169.168 | Best adult filter |
| **Cloudflare** | 1.1.1.3 | 1.0.0.3 | Fastest + malware |
| **OpenDNS** | 208.67.222.123 | 208.67.220.123 | Cisco-backed |

---

## 📂 Project Structure

```
ShieldDNS/
├── app/src/main/
│   ├── AndroidManifest.xml          — Permissions & components
│   ├── java/com/shielddns/app/
│   │   ├── MainActivity.java         — Main app entry
│   │   ├── DnsVpnService.java        ⭐ CORE: DNS interceptor
│   │   ├── HomeFragment.java         — Dashboard UI
│   │   ├── BlocklistFragment.java    — Manage blocked domains
│   │   ├── SettingsFragment.java     — Settings + PIN change
│   │   ├── SetupGuideFragment.java   — How-to guide
│   │   ├── PinLockActivity.java      — PIN entry screen
│   │   ├── BootReceiver.java         — Auto-restart on boot
│   │   └── ShieldDeviceAdmin.java    — Prevent easy uninstall
│   └── res/                          — Layouts, colors, icons
├── .github/workflows/build.yml       — Auto-build CI/CD
└── README.md
```

---

## ⚠️ Important Notes

- Requires Android 6.0+ (API 23)
- User must **accept VPN permission** once (standard Android dialog)
- Does **not** use actual internet — VPN is 100% local
- CleanBrowsing also filters at DNS level as a second layer
- For strongest protection, also set Private DNS in phone settings to `family-filter.cleanbrowsing.org`

---

Made with ❤️ by ShieldDNS
