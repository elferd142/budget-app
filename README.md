# budget-app
my budgeting PWA personal
# Budget App — Complete Setup Guide

---

## What you're setting up

- A Google Apps Script that connects your app to your Google Sheet
- A GitHub account and GitHub Pages to host the app for free
- The app saved to your iPhone home screen as a PWA

**Total time: about 20–30 minutes**

---

## PART 1 — Set up the Google Apps Script

This is the "receiver" that lives inside your Google Sheet and accepts entries from the app.

### Step 1 — Open your Google Sheet
Open the budget spreadsheet you already have at:
https://docs.google.com/spreadsheets/d/1ks6_QM54kbsojnL1waG-8GTMbLQFDXbfHt6O9KWMbOo

### Step 2 — Open the Script Editor
1. Click **Extensions** in the top menu bar
2. Click **Apps Script**
3. A new tab will open — this is the script editor

### Step 3 — Paste the script
1. You'll see a default function `function myFunction() {}` — **select all of it and delete it**
2. Open the file `budget-apps-script.gs` that was provided to you
3. Copy the entire contents and paste it into the script editor

### Step 4 — Set your secret token
In the script, find this line near the top:
```
const SECRET_TOKEN = "your-secret-token-here";
```
Change `your-secret-token-here` to any phrase you want. For example:
```
const SECRET_TOKEN = "sunshine-budget-2026";
```
**Write this phrase down — you'll need it when setting up the app.**

### Step 5 — Save the script
1. Click the floppy disk icon (💾) or press **Cmd+S** (Mac) / **Ctrl+S** (Windows)
2. Give the project a name when asked — something like "Budget App"

### Step 6 — Deploy the script as a web app
1. Click the blue **Deploy** button (top right)
2. Select **New deployment**
3. Click the gear icon ⚙️ next to "Type" and select **Web app**
4. Fill in the settings:
   - **Description**: Budget App
   - **Execute as**: Me
   - **Who has access**: Anyone
5. Click **Deploy**
6. Google will ask you to authorize the app — click **Authorize access**
7. Choose your Google account
8. You may see a warning screen — click **Advanced** then **Go to Budget App (unsafe)**
   *(This is normal for personal scripts — it just means it hasn't been verified by Google)*
9. Click **Allow**
10. **Copy the Web App URL** — it looks like:
    `https://script.google.com/macros/s/AKfycb.../exec`
    **Save this URL — you'll need it shortly.**

---

## PART 2 — Set up GitHub and host the app

### Step 1 — Create a GitHub account
1. Go to https://github.com
2. Click **Sign up** and create a free account
3. Verify your email address

### Step 2 — Create a new repository
1. Once logged in, click the **+** icon (top right) → **New repository**
2. Fill in:
   - **Repository name**: `budget-app` (exactly, lowercase)
   - **Description**: My budget PWA (optional)
   - **Visibility**: Public *(required for free GitHub Pages hosting — no sensitive data is in this file)*
   - Check **Add a README file**
3. Click **Create repository**

### Step 3 — Upload the app file
1. In your new repository, click **Add file** → **Upload files**
2. Drag and drop the file `budget-app.html` from your computer
3. At the bottom, click **Commit changes**

### Step 4 — Rename the file to index.html
GitHub Pages needs the main file to be called `index.html`.
1. Click on `budget-app.html` in your repository
2. Click the pencil ✏️ icon to edit
3. At the top, change the filename from `budget-app.html` to `index.html`
4. Scroll down and click **Commit changes**

### Step 5 — Enable GitHub Pages
1. Click **Settings** (tab at the top of your repository)
2. Scroll down to the **Pages** section in the left sidebar
3. Under **Source**, select **Deploy from a branch**
4. Under **Branch**, select **main** and folder **/ (root)**
5. Click **Save**
6. Wait 1–2 minutes, then your app will be live at:
   `https://yourusername.github.io/budget-app`

---

## PART 3 — Configure the app

### Step 1 — Open the app in Safari on your iPhone
1. Open Safari (must be Safari, not Chrome)
2. Go to `https://yourusername.github.io/budget-app`
3. You'll see the PIN screen

### Step 2 — Set your PIN
The default PIN is `0000`. You'll change it in the next step.

### Step 3 — Enter the app and configure settings
1. Enter PIN `0000` to get in
2. Scroll down to **⚙️ Settings** and tap it to expand
3. Fill in:
   - **Apps Script URL**: Paste the URL you copied in Part 1 Step 10
   - **Secret Token**: Type the same secret phrase you set in the script (e.g. `sunshine-budget-2026`)
   - **Change PIN**: Type your new 4-digit PIN
4. Tap **Save Settings**
5. The app will confirm "Settings saved ✓"

### Step 4 — Share settings with your partner
Your partner will need to:
1. Open Safari and go to the same URL
2. Enter the default PIN `0000`
3. Go to Settings and enter the Apps Script URL, token, and your shared PIN
4. Save settings

---

## PART 4 — Add to iPhone Home Screen

Do this on **both** your phone and your partner's phone:

1. Open Safari and go to your app URL
2. Enter your PIN to confirm the app loads correctly
3. Tap the **Share** button (the box with an arrow pointing up, at the bottom of Safari)
4. Scroll down and tap **Add to Home Screen**
5. Name it "Budget" (or whatever you like)
6. Tap **Add**

The app icon will appear on your home screen. When you tap it, it opens full-screen like a native app — no browser bar.

---

## PART 5 — Test it end to end

1. Open the app from your home screen
2. Enter your PIN
3. Select a category (e.g. Groceries)
4. Set the toggle to **− Out**, enter an amount like `25.00`
5. Leave today's date, add a note like "Trader Joe's"
6. Tap **Log Entry**
7. You should see "✓ Entry logged!"
8. Open your Google Sheet — you should see a new row added to the leftmost tab

---

## Maintenance

**Each new month:** You don't need to do anything in the app. Just create your new sheet tab (e.g. `Jul26`) and **make sure it's the leftmost tab**. The script always writes to whichever tab is on the far left.

**If you add new categories to your sheet:** Let me know and I can update the app's category list for you. You'd just re-upload the HTML file to GitHub.

**If you need to update the app:** Make changes to `index.html` on GitHub (click the file → pencil icon to edit), commit, and GitHub Pages will update automatically within a minute or two.

---

## Troubleshooting

**"Entry logged" but nothing appears in the sheet:**
- Double-check the Apps Script URL in Settings — make sure there's no extra space
- Make sure the token in the app matches the token in the script exactly (case sensitive)
- In the script editor, click **Executions** in the left sidebar to see if there were any errors

**The app doesn't load after adding to home screen:**
- Make sure you added it from Safari specifically (not Chrome)
- Try visiting the URL in Safari again first, then add to home screen

**PIN screen shows but PIN doesn't work:**
- The first-time default PIN is `0000`
- If you changed it and forgot it, open the URL in Safari, open browser developer tools, and clear localStorage — or contact me and I'll help you reset it
