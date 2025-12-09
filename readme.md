# 🟣 Neo-Futuristic Firefox Command Center Setup Guide

This guide will walk you through setting up a custom dark Firefox theme with neon purple accents, plus a matching command center landing page.

---

## 📁 What's Included

```
firefox-setup-guide/
├── SETUP-GUIDE.md          ← You're reading this
├── chrome/
│   └── userChrome.css      ← Firefox theme file
└── landing-page.html       ← Custom homepage
```

---

## Part 1: Firefox Theme Setup (userChrome.css)

### Step 1: Open Firefox Profile Folder

**Method A: Using about:support (Easiest)**
1. Open Firefox
2. Type `about:support` in the URL bar and press Enter
3. Find the row labeled **"Profile Folder"** (under Application Basics section)
4. Click the **"Open Folder"** button next to it

**Method B: Manual Navigation (If Method A doesn't work)**

On **Windows**:
```
C:\Users\YOUR_USERNAME\AppData\Roaming\Mozilla\Firefox\Profiles\
```
- Press `Win + R`, type `%APPDATA%\Mozilla\Firefox\Profiles\` and press Enter
- You'll see folder(s) like `xxxxxxxx.default-release` — open the one with "default-release" in the name

On **Mac**:
```
~/Library/Application Support/Firefox/Profiles/
```
- Open Finder, press `Cmd + Shift + G`, paste the path above

On **Linux**:
```
~/.mozilla/firefox/
```
- Open your file manager, press `Ctrl + L`, type the path above

### Step 2: Find the Correct Profile (If Multiple Exist)

If you see multiple profile folders:
1. Go back to Firefox and type `about:profiles` in the URL bar
2. Look for the profile that says **"This is the profile in use"**
3. Note the **Root Directory** path — that's your active profile folder
4. Open that specific folder

### Step 3: Create the Chrome Folder

1. Inside your profile folder, look for a folder named `chrome`
2. **If it doesn't exist**: Create a new folder and name it exactly `chrome` (lowercase)
3. Open the `chrome` folder

### Step 4: Add the Theme File

1. Copy the `userChrome.css` file (included in this package) into the `chrome` folder
2. Your structure should now look like:
   ```
   Your Profile Folder/
   └── chrome/
       └── userChrome.css
   ```

### Step 5: Enable Custom Stylesheets in Firefox

Firefox has this feature disabled by default. You need to enable it:

1. Open Firefox
2. Type `about:config` in the URL bar and press Enter
3. Click **"Accept the Risk and Continue"** (don't worry, this is safe)
4. In the search box, type: `toolkit.legacyUserProfileCustomizations.stylesheets`
5. Find the setting (there should be only one result)
6. Click the **toggle button** (↔️) on the right to change it from `false` to `true`
7. **Restart Firefox completely** (close all windows and reopen)

### Step 6: Verify the Theme

After restarting, you should see:
- ✅ Pure black tab bar, URL bar, and bookmarks bar
- ✅ Purple glow strip at the very top of the window
- ✅ Active tab is larger with purple top border and glow
- ✅ Inactive tabs are slightly smaller and gray
- ✅ Purple glow when hovering over tabs
- ✅ Pinned tabs have a pulsing purple border animation
- ✅ URL bar glows purple when focused

**Not working?** See Troubleshooting section below.

---

## Part 2: Landing Page Setup

### Step 1: Save the Landing Page

Choose where to save `landing-page.html`:

**Option A: Local File (Simplest)**
1. Create a folder for it, e.g., `C:\Users\YOU\Documents\Firefox-Home\` (Windows) or `~/Documents/Firefox-Home/` (Mac/Linux)
2. Copy `landing-page.html` into that folder
3. Note the full path to the file

**Option B: Cloud/Sync (Access from multiple devices)**
- Save it to Dropbox, Google Drive, OneDrive, etc.
- Use the synced local path as your homepage

### Step 2: Get the File Path

**Windows:**
1. Navigate to the folder containing `landing-page.html`
2. Click in the address bar of File Explorer
3. Copy the path (e.g., `C:\Users\YOU\Documents\Firefox-Home`)
4. Your full file URL will be: `file:///C:/Users/YOU/Documents/Firefox-Home/landing-page.html`
   - Note: Use forward slashes `/` and add `file:///` at the start

**Mac/Linux:**
1. Right-click the file → Get Info (Mac) or Properties (Linux)
2. Copy the path
3. Your full file URL will be: `file:///Users/YOU/Documents/Firefox-Home/landing-page.html`

### Step 3: Set as Firefox Homepage

1. Open Firefox
2. Click the **☰ hamburger menu** (top-right) → **Settings**
3. In the left sidebar, click **Home**
4. Under **"New Windows and Tabs"**:
   - Next to "Homepage and new windows", select **Custom URLs...**
   - Paste your file path: `file:///C:/Users/YOU/Documents/Firefox-Home/landing-page.html`
5. Optionally, set "New tabs" to **"Firefox Home (Default)"** or **"Blank Page"**
   - Note: Custom URLs don't work for new tabs without an extension

### Step 4: (Optional) Set for New Tabs Too

Firefox doesn't natively allow custom new tab pages. To use the landing page for new tabs:

1. Install the extension: **"New Tab Override"** from Firefox Add-ons
   - Go to: https://addons.mozilla.org/en-US/firefox/addon/new-tab-override/
2. After installing, go to the extension's options
3. Select "local file" and browse to your `landing-page.html`

---

## Part 3: Troubleshooting

### Theme not showing up?

1. **Check the file name**: Must be exactly `userChrome.css` (capital C, lowercase everything else)
2. **Check the folder name**: Must be exactly `chrome` (all lowercase)
3. **Verify about:config setting**: `toolkit.legacyUserProfileCustomizations.stylesheets` must be `true`
4. **Restart Firefox**: Close ALL Firefox windows, wait 5 seconds, reopen
5. **Check file location**: The `chrome` folder must be directly inside your profile folder, not nested elsewhere

### Finding the right profile folder

If you have multiple Firefox installations or profiles:
1. Type `about:profiles` in Firefox
2. Look for **"This is the profile in use and it cannot be deleted"**
3. Click **"Open Folder"** next to "Root Directory" for that profile

### Landing page features not working?

- **Weather not loading**: The page uses wttr.in which should work automatically. Check your internet connection.
- **Reddit/News not loading**: These use public APIs. If you're on a restricted network (work/school), they might be blocked.
- **Notes not saving**: Make sure you're opening the file from a local path (file:///) not a web server, as localStorage needs proper origin.

### Profile folder locations reference

| OS | Path |
|---|---|
| Windows 10/11 | `%APPDATA%\Mozilla\Firefox\Profiles\` |
| macOS | `~/Library/Application Support/Firefox/Profiles/` |
| Linux | `~/.mozilla/firefox/` |

---

## 🎨 Customization Tips

### Change the purple accent color

In `userChrome.css`, find all instances of:
```css
rgb(196, 0, 214)
rgba(196, 0, 214, ...)
```
Replace with your preferred color.

In `landing-page.html`, find the CSS variables at the top:
```css
--purple-main: rgb(196, 0, 214);
```
Change to your preferred color.

### Add more subreddits

In `landing-page.html`, find the CONFIG section:
```javascript
reddit: {
    subreddits: ['technology', 'programming', 'nfl', 'space', 'science'],
```
Add or remove subreddits as you like.

### Change crypto coins

In `landing-page.html`, find:
```javascript
crypto: {
    coins: ['bitcoin', 'ethereum', 'solana', 'cardano']
```
Use CoinGecko coin IDs (find them at coingecko.com).

---

## ⌨️ Landing Page Keyboard Shortcuts

| Key | Action |
|---|---|
| `/` | Focus search bar |
| `Esc` | Unfocus current element |
| `Enter` | Submit search / Add todo |

---

## 📝 Quick Reference Card

After setup, your workflow is:
1. Open Firefox → See your command center homepage
2. Press `/` → Start typing to search Google (or switch engines)
3. Click subreddit tabs → Browse different communities
4. Type notes → They auto-save locally
5. Right-click any tab → "Pin Tab" → Gets priority purple pulse animation

Enjoy your new setup! 🟣⚫
