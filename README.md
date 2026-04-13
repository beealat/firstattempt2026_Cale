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

---

### Troubleshooting

| Problem | Fix |
|--------|-----|
| Page is blank | Make sure you used Live Server — do not double-click the file directly |
| Live Server not in right-click menu | Make sure the extension is installed, then restart VS Code |
| Styles not loading | Make sure you opened the whole **folder** in VS Code, not just the file |
| No internet connection | The app requires internet to load AngularJS and Chart.js from CDN |

---

## Project Structure

```
firstattempt2026_Cale/
├── index.html              ← Main entry point; contains all page templates as ng-template blocks
├── styles/
│   └── main.css            ← All CSS styles
├── js/
│   └── app.js              ← AngularJS module, controller, and all app data
└── screenshots/            ← All application screenshots
```

### How the Structure Works

Rather than loading separate HTML files (which can cause issues with Live Server), all page sections are defined as **inline `ng-template` blocks** inside `index.html`. AngularJS reads these templates directly from memory — no extra file requests needed. This gives the project a clean structure while working reliably in any browser.

---

## AI Tools Used

| Tool | Purpose |
|------|---------|
| **Claude AI** | Converted the original single-file HTML app into a structured AngularJS project using `ng-template` for inline partials |
| **ChatGPT** | Used to refine and improve prompts for better output |

---

## Prompts

**First Prompt** *(to Claude AI)*
> *"You are an expert Angular developer. I want you to generate a complete, working Angular web application based on a mobile app design that I will provide.

GOAL:
Convert my existing MOBILE APP DESIGN into a fully responsive and interactive WEB APPLICATION while preserving:
- Exact color scheme
- Layout structure
- UI components (buttons, cards, forms, etc.)
- Overall theme and visual style

DESIGN INSTRUCTIONS:
- The UI must closely match the provided mobile app (same spacing, fonts, colors, and hierarchy)
- Make it responsive (desktop + mobile view)
- Keep the design modern and clean
- Use CSS or Angular styling (no external UI frameworks unless necessary)

FUNCTIONALITY:
- Implement all visible features from the design as working components
- Add basic interactivity (button clicks, navigation, form input handling)
- Ensure smooth user experience

IMPORTANT:
- Do NOT skip files
- Do NOT give partial code
- Generate a FULL working project

I will provide the design next. Wait for it before generating code."*

**Key Prompt that generated the full working project** *(to Claude AI)*
> *"Here is my mobile app design (PDF/Image). Convert this into an Angular web application. Follow the exact UI, layout, and theme. Also Generate a complete Angular web application that converts my mobile app design into a responsive web interface. Maintain the exact UI/UX, colors, layout, and components. Use Angular JS and provide full working code with installation steps. Make sure to follow my previous prompts too"*

**Prompt that refines and improve my prompts** *(to Chatgpt)*
> *"Refine and improve my prompts + (block of prompts)."*

---

## Screenshots

### Alumni User POV

**1. Login Page — Alumni**
The login screen with the ADDU crest, biometric login option, and Alumni / User role selected.

<img width="1916" height="1020" alt="Screenshot 2026-04-13 151730" src="https://github.com/user-attachments/assets/126211e5-0e98-405c-8353-ec3ca77ac207" />

---

**2. Home Dashboard**
The alumni home screen showing the welcome hero banner, quick action shortcuts, daily snapshot cards, and recent activity feed.

<img width="1918" height="1016" alt="Screenshot 2026-04-13 151808" src="https://github.com/user-attachments/assets/68de9035-d140-462b-bb4f-601a3d4c8b0b" />

---

**3. Alumni Network**
The network page showing verified alumni cards with Connect and Message buttons, filterable by Near Me, Industry Experts, and Same Batch.

<img width="1917" height="1019" alt="Screenshot 2026-04-13 151816" src="https://github.com/user-attachments/assets/90a16122-3ada-4631-8ed0-fb4f23414b56" />

---

**4. Donation Hub**
The donation page showing total impact, donation categories, verified urgent appeals with progress bars, and a Start a Campaign button.

<img width="1918" height="1017" alt="Screenshot 2026-04-13 151825" src="https://github.com/user-attachments/assets/d78e5310-82bd-454d-adab-043e6189497d" />

---

**5. Career Opportunities**
The career page showing recommended job listings from Google and Spotify, alongside featured alumni mentors available for meetings.

<img width="1919" height="1021" alt="Screenshot 2026-04-13 151833" src="https://github.com/user-attachments/assets/8e62533d-67b3-4f3c-8744-7be70b3801ee" />

---

**6. Academic Records**
The documents page showing the Digital Academic Passport, document services (transcript, e-diploma, degree verification), and request history.

<img width="1919" height="1016" alt="Screenshot 2026-04-13 151841" src="https://github.com/user-attachments/assets/2d427972-b136-4fb6-b3bf-69d63f9a7e46" />

---

**7. My Profile**
The alumni profile page showing verified user info, academic passport card, additional credentials, and account settings.

<img width="1919" height="1020" alt="Screenshot 2026-04-13 151848" src="https://github.com/user-attachments/assets/f4ac0bed-c8b4-4096-b1dc-3352fbb7e238" />

---

**8. Pledge & Automate**
The pledge page showing a donut chart of contributions across 4 key areas, alongside a recurring donation setup form with payment method selection.

<img width="1919" height="908" alt="Screenshot 2026-04-13 151859" src="https://github.com/user-attachments/assets/5a5aa44f-2896-4efc-98c6-8d92e3bf9885" />

---

**9. My Impact**
The impact page showing total projects funded, lives touched, contributed amount, quick action grid, and full transaction history.

<img width="1919" height="1021" alt="Screenshot 2026-04-13 151913" src="https://github.com/user-attachments/assets/18dfd32b-9677-4201-8611-ef70a27f65c3" />

---

### Admin / Staff POV

**10. Login Page — Admin**
The same login screen with Admin / Staff role selected instead.

<img width="1919" height="1020" alt="Screenshot 2026-04-13 152049" src="https://github.com/user-attachments/assets/26610e12-b358-41d8-9062-d9f50bc6e6ff" />

---

**11. Admin Home Dashboard**
The admin home screen showing the coordinator welcome banner, daily overview with pending reviews and verifications, and recent platform activity.

<img width="1919" height="1022" alt="Screenshot 2026-04-13 152057" src="https://github.com/user-attachments/assets/395e51c0-940e-4ed2-a132-18d7acfdc4c1" />

---

**12. Moderation Queue**
The queue page showing all pending submissions — donations, network requests, job posts, document verifications, and emergency fund requests — each with a Review button.

<img width="1919" height="1018" alt="Screenshot 2026-04-13 152106" src="https://github.com/user-attachments/assets/d7ee03d3-397a-4bdb-89ec-c8d2be78418c" />

---

**13. Donation Insights**
The insights page showing platform analytics — total funds raised ($124.5k), new donors, active campaigns, verification rate, donation trend line chart, and category breakdown donut chart.

<img width="1919" height="1018" alt="Screenshot 2026-04-13 152115" src="https://github.com/user-attachments/assets/224cb1b1-a4e8-4787-9163-c49c7b1c3332" />

---

**14. Messages / Inbox**
The messages page showing the staff inbox with unread messages from alumni regarding scholarships, document verifications, and emergency fund requests.

<img width="1919" height="1023" alt="Screenshot 2026-04-13 152124" src="https://github.com/user-attachments/assets/dec76eee-ef97-4290-a9a1-b48fc8b1aa4b" />

---

**15. Admin Profile**
The admin coordinator profile showing the gold academic passport card, additional credentials, settings menu, and Log Out button.

<img width="1917" height="1019" alt="Screenshot 2026-04-13 152133" src="https://github.com/user-attachments/assets/66a24d7f-fe36-4d6b-846a-2f90ba4108e2" />

---

## References

- [AngularJS 1.x Documentation](https://docs.angularjs.org/guide)
- [Chart.js Documentation](https://www.chartjs.org/docs/)
- [Live Server VS Code Extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
- [How to write a good README](https://www.freecodecamp.org/news/how-to-write-a-good-readme-file/)
