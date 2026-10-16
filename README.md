# 🌿 MindEase

**A Digital Mental Health and Psychological Support System for college students.**

MindEase gives students a private, stigma-free place to reach their college counselling cell, keep a digital diary, check in on their wellbeing and find calm, at any hour and with the option to stay anonymous.

> Mini Project 2026-27 · CSEMPID072
> Department of Computer Science and Engineering, ABES Institute of Technology, Ghaziabad
> Built for **Smart India Hackathon 2025**, problem statement **SIH25092**

---

## Table of contents

- [Features](#features)
- [Tech stack](#tech-stack)
- [Project structure](#project-structure)
- [Getting started](#getting-started)
- [Using the demo](#using-the-demo)
- [How data is stored](#how-data-is-stored)
- [Privacy and safety notes](#privacy-and-safety-notes)
- [Customising](#customising)
- [Limitations and roadmap](#limitations-and-roadmap)
- [SDG alignment](#sdg-alignment)
- [Team](#team)

---

## Features

### For students

| Feature | What it does |
| --- | --- |
| **Support tickets** | Pick a problem category (Relationships, Academics, Career, Anxiety, Low mood, Stress, Family and more), describe it, and the ticket is routed only to a counsellor of the matching section. Tickets can be marked urgent, raised anonymously, pinned or deleted. |
| **Digital diary** | Write freely and tag your mood. Entries are visible only to you. A weekly mood chart shows how you have been feeling, and a separate diary log lets you browse past entries. |
| **Wellness check** | Short self-screening quizzes: **PHQ-2** (mood), **GAD-7** (anxiety), plus short checks for stress/burnout and sleep. Results point to the right type of counsellor and can pre-fill a support ticket. |
| **Relaxation section** | Pick a book, movie or game and get a recommendation matched to how you feel (Happy, Calm, Stressed, Anxious, Sad, Angry). |
| **Companion chat** | A lightweight, rule-based chat companion with quick-reply chips for common worries such as exams, sleep and stress. |
| **Calm sound** | Ambient soothing sound generated in the browser with the Web Audio API. No audio files are needed. |
| **Emergency SOS** | One tap opens a helpline panel with a call button for **Tele-MANAS (14416)** and **112**, along with a guided breathing animation. |
| **Image space** | A private gallery for images that bring you comfort. |
| **Dashboard extras** | Daily positive thought, digital/analog clock toggle and a profile page. |

### For counsellors

- Sign up and choose the sections you handle (clinical, relationship, academic and career, family and social, general).
- Declare your level: student volunteer, peer counsellor or professional counsellor.
- See only the tickets that match your section and reply to students.
- Serious cases are flagged for a professional-level counsellor.

### Design and accessibility

- Responsive layout (sidebar on desktop, horizontal nav on mobile, safe-area aware)
- Automatic **light and dark mode** via `prefers-color-scheme`
- Visible keyboard focus states and `prefers-reduced-motion` support
- Semantic labels and ARIA attributes on key controls

---

## Tech stack

- **HTML5**, **CSS3** (custom properties, grid, flexbox) and **vanilla JavaScript (ES6+)**
- **Web Audio API** for ambient sound
- **localStorage** for demo persistence
- **Google Fonts**: Figtree and Outfit

No frameworks, no build step and no dependencies to install.

---

## Project structure

```
.
├── index.html   # Landing page markup and app/overlay mount points
├── style.css    # Theme tokens, layout, components, dark mode, responsive rules
└── script.js    # App logic: auth, routing, views, quizzes, chat, tickets, sound
```

---

## Getting started

### Option 1: open directly

Download or clone the repository and open `index.html` in any modern browser.

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
```

### Option 2: run a local server (recommended)

```bash
# Python
python3 -m http.server 8000

# or Node.js
npx serve .
```

Then visit <http://localhost:8000>.

### Deploy to GitHub Pages

1. Push the three files to the repository root.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose your branch and the `/ (root)` folder.
4. Save. Your site will be live at `https://<your-username>.github.io/<your-repo>/`.

---

## Using the demo

1. Click **Get started** or **Log in**.
2. Choose whether you are a **Student** or **Counsellor**.
3. Enter any email and password. A new email automatically creates an account, then you complete a short profile setup. *(Authentication is simulated for the demo.)*
4. **Continue with Google** is a UI placeholder for future real OAuth.
5. Use the sidebar to explore tickets, diary, wellness check and more.

The dashboard includes options to **load demo data** (sample tickets from several students so a counsellor account has something to review) and to **wipe demo data** from your device.

> Tip: open two browser profiles, one logged in as a student and one as a counsellor, to see how tickets are routed by section.

---

## How data is stored

This is a **frontend-only prototype**. Everything is kept in the browser's `localStorage` on the current device. Nothing is sent to a server.

| Key | Contents |
| --- | --- |
| `dmh_session` | Currently logged-in user |
| `dmh_tickets` | All support tickets |
| `dmh_diary_<email>` | Diary entries for a user |
| `dmh_img_<email>` | Image space items for a user |
| `dmh_profile_*` | Profile details |
| `dmh_quiz_*` | Wellness check results |
| `dmh_clock` | Clock display preference |

---

## Privacy and safety notes

- ⚠️ **This is a demo, not a clinical tool.** The wellness check, quizzes and chat companion are for self-awareness and guidance only. They do not provide diagnosis or treatment.
- Passwords are **not** securely handled in this prototype. Do not enter real passwords or sensitive personal data.
- Because data lives in `localStorage`, anyone with access to the same browser profile could see it.
- If you or someone you know is in crisis, contact **Tele-MANAS at 14416** (India) or **112** for emergencies.

---

## Customising

- **Colours and themes:** edit the CSS variables in `:root` at the top of `style.css`. Dark-mode values live in the `prefers-color-scheme` and `[data-theme="dark"]` blocks.
- **Problem categories and counsellor sections:** update the `CATS` and `FLD` objects in `script.js`.
- **Quizzes:** edit `PHQ`, `GAD` and the `QZ` object in `script.js`.
- **Recommendations and quotes:** edit `REC`, `LIB` and `QS`.
- **Chat companion replies:** edit the `INT` pattern/response list.
- **Helpline numbers:** change the `tel:` links in the SOS modal in `script.js`.

---

## Limitations and roadmap

Current limitations:

- No backend, so no real multi-device sync or real-time counsellor/student messaging
- Simulated authentication and Google sign-in
- Rule-based chat rather than a trained model
- Data limited by browser storage quotas

Planned improvements:

- [ ] Backend API with a database and secure authentication (JWT / OAuth)
- [ ] Encrypted storage of diaries and tickets
- [ ] Real-time notifications and counsellor messaging
- [ ] Institution-level admin dashboard and anonymised analytics
- [ ] Hindi and regional language support
- [ ] AI-assisted triage with human counsellor oversight
- [ ] Progressive Web App (offline support, installable)

---

## SDG alignment

- **SDG 3: Good Health and Well-being.** Early, private support and stress management for students.
- **SDG 10: Reduced Inequalities.** Equal, stigma-free access to mental health support for every student.

---

## Team

| Name | Role |
| --- | --- |
| Srijan Diwan | Team member |
| Vinayak Pandey | Team member |
| Vibhu Varma | Team member |
| Yash Prakash Singh | Team member |

**Supervisor:** Prof. Satyendra Singh
**Institution:** ABES Institute of Technology, Ghaziabad

---

## License

Add a license of your choice (for example MIT) by creating a `LICENSE` file in the repository root.
