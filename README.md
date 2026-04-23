# Cale

**Framework:** AngularJS 1.x
**Module:** ADDU Nation

---

## About

**ADDU Nation** is a web application for the Ateneo de Davao University alumni community. It serves as a platform for alumni to connect, donate to causes, access academic documents, explore career opportunities, and manage their profiles. It also includes an admin side for managing submissions, campaigns, and moderation queues.

This project was built using **AngularJS 1.x** as a single-page application (SPA). The project is structured across 3 files — a main `index.html` that uses `ng-template` blocks to organize all page partials inline, a separate `main.css` stylesheet, and a separate `app.js` controller.

> ✅ **No Node.js, no npm, no terminal commands required.** All dependencies (AngularJS, Chart.js, Google Fonts) are loaded automatically from CDN when the app runs in the browser.

---

## Installation & Setup

### What You Need to Install

**1. Visual Studio Code**
- Download from: https://code.visualstudio.com/
- Run the installer and keep all default settings

**2. Live Server Extension** (inside VS Code)
- Open VS Code
- Press `Ctrl + Shift + X` to open Extensions
- Search for **Live Server** by Ritwick Dey
- Click **Install**

**3. Git** *(only needed if cloning — skip if downloading ZIP)*
- Download from: https://git-scm.com/downloads
- Run the installer and keep all default settings
- Confirm install by opening a terminal and typing:
  ```
  git --version
  ```

---

### Getting the Project

#### Option A — Clone with Git
1. Open VS Code
2. Press **Ctrl + `** to open the terminal
3. Run:
   ```bash
   git clone https://github.com/beealat/firstattempt2026_Cale.git
   ```

#### Option B — Download ZIP (no Git needed)
1. Go to https://github.com/beealat/firstattempt2026_Cale
2. Click the green **Code** button → **Download ZIP**
3. Right-click the downloaded ZIP → **Extract All**
4. Choose a location and click **Extract**

---

### Running the Project

1. Open **VS Code**
2. Go to **File → Open Folder**
3. Select the `firstattempt2026_Cale` folder
4. In the left sidebar, click on `index.html` to open it
5. Right-click inside the file → select **"Open with Live Server"**
6. Your browser will automatically open at:
   ```
   http://127.0.0.1:5500/index.html
   ```

The app is now running! ✅

> ⚠️ **Important for PWA testing:** Always use Live Server — never open `index.html` by double-clicking or using VS Code's Run & Debug. The PWA features (Service Worker and manifest) require an `http://` origin and will not work over `file://`.

---

### Setting Live Server to Open Chrome (Required for PWA Install Demo)

By default, Live Server may open your system's default browser (e.g. Edge). For PWA testing, Chrome is recommended because it shows the install button most reliably.

**Option 1 — Via Settings UI:**
1. Press `Ctrl + ,` to open VS Code Settings
2. Search for `Live Server browser`
3. Find **Live Server > Settings: Custom Browser**
4. Change the dropdown to **chrome**

**Option 2 — Via settings.json:**
1. Press `Ctrl + Shift + P`
2. Type `Open User Settings JSON` and select it
3. Add this inside the curly braces:
   ```json
   "liveServer.settings.CustomBrowser": "chrome"
   ```
4. Save with `Ctrl + S`

After this, right-clicking `index.html` → **Open with Live Server** will launch Chrome at `http://127.0.0.1:5500/index.html`.

---

### Troubleshooting

| Problem | Fix |
|--------|-----|
| Page is blank | Make sure you used Live Server — do not double-click the file directly |
| Live Server not in right-click menu | Make sure the extension is installed, then restart VS Code |
| Styles not loading | Make sure you opened the whole **folder** in VS Code, not just the file |
| PWA install button not showing | Open via Live Server in Chrome — not Edge, not via Run & Debug |
| Service Worker registration failed (`null` origin error) | You opened the file directly in the browser — use Live Server instead |

---

## Project Structure

```
firstattempt2026_Cale/
├── index.html              ← Main entry point; contains all page templates as ng-template blocks
├── main.css                ← All CSS styles (flat structure, no subfolders)
├── app.js                  ← AngularJS module, controller, and all app data
├── sw.js                   ← Service Worker for PWA offline caching
├── manifest.json           ← PWA manifest with app identity and icons
└── icons/
    ├── icon-72x72.png
    ├── icon-96x96.png
    ├── icon-128x128.png
    ├── icon-144x144.png
    ├── icon-152x152.png
    ├── icon-192x192.png
    ├── icon-384x384.png
    └── icon-512x512.png
```

### How the Structure Works

Rather than loading separate HTML files (which can cause issues with Live Server), all page sections are defined as **inline `ng-template` blocks** inside `index.html`. AngularJS reads these templates directly from memory — no extra file requests needed. This gives the project a clean structure while working reliably in any browser.

---

## PWA Conversion (Activity 15)

This branch (`feature/pwa-ready`) adds Progressive Web App capabilities to the existing AngularJS project. The app can now be installed on a device and loads offline.

### What Was Added

- `manifest.json` — defines app identity, theme color, icons, and shortcuts
- `sw.js` — Service Worker implementing Cache-First for static assets and Network-First for CDN resources
- SW registration script inside `index.html` — registers `sw.js` on page load
- `icons/` folder — 8 icon sizes (72×72 to 512×512) for device home screens

### Master Prompt (PWA Conversion)

> *"I am using AngularJS 1.x as my framework. My project has a flat file structure — all files (index.html, main.css, app.js) are at the root, with an icons/ subfolder for PWA icons. Help me convert this into a fully working PWA by: (1) generating a valid manifest.json with ADDU Nation branding and all 8 icon sizes, (2) creating a sw.js Service Worker with Cache-First strategy for local assets and Network-First for CDN URLs like AngularJS and Chart.js, and (3) adding the Service Worker registration script inside index.html before the closing body tag. Make sure all file paths match the flat structure — no styles/ or js/ subfolders."*

---

### AI Hallucinations & Errors Encountered

These are the errors and issues discovered during the PWA conversion that required manual fixes:

**1. Service Worker was never registered (biggest issue)**
- What happened: The AI generated `sw.js` but never added the registration script to `index.html`. The browser had no idea `sw.js` existed, so DevTools showed no Service Worker at all.
- Fix: Manually added the registration block before `</body>` in `index.html`:
  ```js
  if ('serviceWorker' in navigator) {
    window.addEventListener('load', () => {
      navigator.serviceWorker.register('./sw.js')
        .then(r => console.log('[PWA] SW registered', r))
        .catch(e => console.error('[PWA] SW failed', e));
    });
  }
  ```

**2. Wrong file paths in `sw.js`**
- What happened: The AI assumed a structured folder layout (`./styles/main.css`, `./js/app.js`) but the actual project uses a flat structure where `main.css` and `app.js` are at the root.
- Fix: Updated the `PRECACHE_ASSETS` array in `sw.js` to use the correct flat paths:
  ```js
  './main.css',
  './app.js',
  ```

**3. `manifest.json` icon purpose warning**
- What happened: The AI used `"purpose": "maskable any"` on all icons, which Chrome's DevTools flags as discouraged because it can cause rendering issues on some platforms.
- Fix: Split each icon entry into two separate entries — one with `"purpose": "any"` and one with `"purpose": "maskable"`.

**4. Service Worker registration error when opening via Chrome directly**
- What happened: Opening `index.html` through VS Code's Run & Debug or by double-clicking caused this error in the console:
  ```
  TypeError: Failed to register a ServiceWorker: The URL protocol of the current origin ('null') is not supported.
  ```
- Root cause: Chrome blocks Service Workers over the `file://` protocol. This is a browser security restriction, not a code bug.
- Fix: Always open the project using Live Server (`http://127.0.0.1:5500`) — never via `file://`.

**5. Live Server defaulted to Edge instead of Chrome**
- What happened: After setting up Live Server, right-clicking → Open with Live Server opened Microsoft Edge, where the PWA install button looked different and behavior varied.
- Fix: Changed the Live Server custom browser setting to Chrome via VS Code Settings → search `Live Server browser` → set to `chrome`. Alternatively, add `"liveServer.settings.CustomBrowser": "chrome"` to `settings.json`.

---

## AI Tools Used

| Tool | Purpose |
|------|---------|
| **Claude AI** | Converted the original single-file HTML app into a structured AngularJS project using `ng-template` for inline partials; also assisted with PWA conversion (manifest, Service Worker, icon setup) |
| **ChatGPT** | Used to refine and improve prompts for better output |

---

## Prompts

**First Prompt** *(to Claude AI)*
> *"You are an expert Angular developer. I want you to generate a complete, working Angular web application based on a mobile app design that I will provide.*
>
> *GOAL: Convert my existing MOBILE APP DESIGN into a fully responsive and interactive WEB APPLICATION while preserving: Exact color scheme, Layout structure, UI components (buttons, cards, forms, etc.), Overall theme and visual style.*
>
> *DESIGN INSTRUCTIONS: The UI must closely match the provided mobile app (same spacing, fonts, colors, and hierarchy). Make it responsive (desktop + mobile view). Keep the design modern and clean. Use CSS or Angular styling (no external UI frameworks unless necessary).*
>
> *FUNCTIONALITY: Implement all visible features from the design as working components. Add basic interactivity (button clicks, navigation, form input handling). Ensure smooth user experience.*
>
> *IMPORTANT: Do NOT skip files. Do NOT give partial code. Generate a FULL working project. I will provide the design next. Wait for it before generating code."*

**Key Prompt that generated the full working project** *(to Claude AI)*
> *"Here is my mobile app design (PDF/Image). Convert this into an Angular web application. Follow the exact UI, layout, and theme. Also Generate a complete Angular web application that converts my mobile app design into a responsive web interface. Maintain the exact UI/UX, colors, layout, and components. Use Angular JS and provide full working code with installation steps. Make sure to follow my previous prompts too."*

**PWA Master Prompt** *(to Claude AI)*
> *"I am using AngularJS 1.x as my framework. My project has a flat file structure — all files (index.html, main.css, app.js) are at the root, with an icons/ subfolder for PWA icons. Help me convert this into a fully working PWA by: (1) generating a valid manifest.json with ADDU Nation branding and all 8 icon sizes, (2) creating a sw.js Service Worker with Cache-First strategy for local assets and Network-First for CDN URLs like AngularJS and Chart.js, and (3) adding the Service Worker registration script inside index.html before the closing body tag. Make sure all file paths match the flat structure — no styles/ or js/ subfolders."*

**Prompt that refines and improves prompts** *(to ChatGPT)*
> *"Refine and improve my prompts + (block of prompts)."*

---

## Screenshots

### Alumni User POV

**1. Login Page — Alumni**
The login screen with the ADDU crest, biometric login option, and Alumni / User role selected.

<img width="1919" height="1018" alt="image" src="https://github.com/user-attachments/assets/ebf80cd9-4d44-40dc-aafa-a0008a2943a1" />

---

**2. Home Dashboard**
The alumni home screen showing the welcome hero banner, quick action shortcuts, daily snapshot cards, and recent activity feed.

<img width="1919" height="1020" alt="image" src="https://github.com/user-attachments/assets/fc98203e-8f4f-4635-a000-11825290f87e" />

---

**3. Alumni Network**
The network page showing verified alumni cards with Connect and Message buttons, filterable by Near Me, Industry Experts, and Same Batch.

<img width="1919" height="1019" alt="image" src="https://github.com/user-attachments/assets/b44b234f-3e00-4be1-aac5-5ccd8e24b03f" />

---

**4. Donation Hub**
The donation page showing total impact, donation categories, verified urgent appeals with progress bars, and a Start a Campaign button.

<img width="1915" height="1022" alt="image" src="https://github.com/user-attachments/assets/8b0cc31f-02f4-4197-b260-c2e6f4ba0f3e" />

---

**5. Career Opportunities**
The career page showing recommended job listings from Google and Spotify, alongside featured alumni mentors available for meetings.

<img width="1919" height="1020" alt="image" src="https://github.com/user-attachments/assets/f66c850c-58bd-4314-a472-879f3f6b17e1" />

---

**6. Academic Records**
The documents page showing the Digital Academic Passport, document services (transcript, e-diploma, degree verification), and request history.

<img width="1919" height="1019" alt="image" src="https://github.com/user-attachments/assets/b5d39e54-faf2-43d9-882f-c927b6cf5468" />

---

**7. My Profile**
The alumni profile page showing verified user info, academic passport card, additional credentials, and account settings.

<img width="1916" height="1009" alt="image" src="https://github.com/user-attachments/assets/67510aac-1ae0-474a-870c-224fad7471d6" />

---

**8. Pledge & Automate**
The pledge page showing a donut chart of contributions across 4 key areas, alongside a recurring donation setup form with payment method selection.

<img width="1919" height="1017" alt="image" src="https://github.com/user-attachments/assets/c6232abd-68cb-4e45-913b-5b9caf7bb9d1" />

---

**9. My Impact**
The impact page showing total projects funded, lives touched, contributed amount, quick action grid, and full transaction history.

<img width="1919" height="1020" alt="image" src="https://github.com/user-attachments/assets/a90bf367-91d2-4f86-9866-afedeba9b709" />

---

### Admin / Staff POV

**10. Login Page — Admin**
The same login screen with Admin / Staff role selected instead.

<img width="1916" height="1009" alt="image" src="https://github.com/user-attachments/assets/379af8bc-45cc-4337-8140-93790c40bd1a" />

---

**11. Admin Home Dashboard**
The admin home screen showing the coordinator welcome banner, daily overview with pending reviews and verifications, and recent platform activity.

<img width="1919" height="1023" alt="image" src="https://github.com/user-attachments/assets/74776973-221e-433f-ae82-be1d60bf4109" />

---

**12. Moderation Queue**
The queue page showing all pending submissions — donations, network requests, job posts, document verifications, and emergency fund requests — each with a Review button.

<img width="1919" height="1020" alt="image" src="https://github.com/user-attachments/assets/e05626c2-095d-46f2-8c7f-87558e7509cb" />

---

**13. Donation Insights**
The insights page showing platform analytics — total funds raised ($124.5k), new donors, active campaigns, verification rate, donation trend line chart, and category breakdown donut chart.

<img width="1919" height="1016" alt="image" src="https://github.com/user-attachments/assets/4dc96e10-34d8-43eb-8fc1-de27a8130913" />

---

**14. Messages / Inbox**
The messages page showing the staff inbox with unread messages from alumni regarding scholarships, document verifications, and emergency fund requests.

<img width="1919" height="1021" alt="image" src="https://github.com/user-attachments/assets/a28e266d-05fb-4dac-af87-bfe8f173a74b" />

---

**15. Admin Profile**
The admin coordinator profile showing the gold academic passport card, additional credentials, settings menu, and Log Out button.

<img width="1919" height="1025" alt="image" src="https://github.com/user-attachments/assets/0936af14-9285-4b8f-829b-1d7c5d1968d2" />

---

## References

- [AngularJS 1.x Documentation](https://docs.angularjs.org/guide)
- [Chart.js Documentation](https://www.chartjs.org/docs/)
- [Live Server VS Code Extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
- [MDN Web Docs — Progressive Web Apps](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps)
- [web.dev — Service Workers](https://web.dev/service-workers-cache-storage/)
- [web.dev — Web App Manifest](https://web.dev/add-manifest/)
- [How to write a good README](https://www.freecodecamp.org/news/how-to-write-a-good-readme-file/)
