```markdown
# PTEC NoteBOT 🎓

**PTEC NoteBOT** is a single‑file, mobile‑first web app for the students of **Pabna Textile Engineering College (PTEC)**.  
It provides quick access to **notes, lab reports, question banks, syllabus, notices, routines, results, a phone book, mini tools and games** — all in one beautiful glass‑morphic interface.

---

## ✨ Features

- 📚 **Notes & Study Materials** – Browse by semester, department and subject  
- 📋 **Lab Reports & Q‑Bank** – Separate sections organised by level  
- 📢 **Notice / Routine / Result** – Quick access to updates  
- ☎️ **Phone Book** – Searchable directory of teachers, staff and support  
- 🤖 **Tex‑GPT** – Offline chatbot for basic textile definitions  
- 🧶 **Count Koto** – Stitch/row counter + Ne ↔ Tex converter  
- 🎮 **Games** – Tic‑Tac‑Toe, Stone‑Paper‑Scissors, Memory Match  
- 🌗 **Smart Theme** – Dark/light mode, follows system preference  
- 📌 **Pin Subjects** – Bookmark frequently used notes  
- 🔍 **Global Search** – Search subjects, terms, and people  
- 📱 **Fully Responsive** – Optimised for mobile and desktop  
- ⚡ **Performance‑Tuned** – No lag on mid‑range phones

---

## 🚀 How to Run

The entire app is contained in a **single `index.html` file**. No server or build step is required.

1. **Download** or copy the `index.html` file to your computer.
2. **Open** the file in any modern browser (Chrome, Firefox, Edge, Safari).
3. That’s it! The app will start immediately.

> 💡 **Tip:** For best mobile experience, you can host the file on GitHub Pages, Netlify, Vercel, or any static file host.

---

## 🛠️ Customisation Guide

All the data (subjects, notes, notices, phone numbers, jokes, etc.) is stored in **JavaScript objects** inside the `<script>` tag at the bottom of `index.html`.  
You can easily modify them to match your college’s actual data.

### 📁 Main Data Objects

| Object        | Purpose                                                         |
|---------------|-----------------------------------------------------------------|
| `NOTES`       | Theory subjects for each semester and department                |
| `REPORTS`     | Lab report names per level                                      |
| `QBANK`       | Question bank names per level                                   |
| `FILES`       | Google Drive links for actual PDF notes (key: `term\|dept\|subject`) |
| `NOTICES`     | Notice items (title, date)                                      |
| `ROUTINES`    | Routine items                                                   |
| `RESULTS`     | Result items                                                    |
| `PHONES`      | Phone book entries (name, position, phone, category)            |
| `TEXKB`       | Knowledge base for Tex‑GPT (keywords → answer)                  |
| `JOKES`       | Jokes displayed in the Jokes section                            |
| `INFO`        | Content for Library and Free Courses pages                      |
| `SUBMIT_FORM_URL` | External URL for note submission form (optional)             |

---

### How to Add a New Subject / Note

1. **Add the subject** to the correct semester and department inside `NOTES`:

```javascript
var NOTES = {
  '2-2': {
    AE: ['Stat', 'YM-I', 'FM-I', 'MMTF', 'TTQC', 'FME', 'YourNewSubject'],
    // ...
  },
  // ...
};
```

2. Add the Google Drive link (if available) to FILES:

```javascript
var FILES = {
  '2-2|AE|YourNewSubject': [
    { t: 'Note 1 by XYZ', u: 'https://drive.google.com/file/d/...' },
    { t: 'Note 2 by ABC', u: 'https://drive.google.com/file/d/...' }
  ],
  // ...
};
```

The key format is 'term|department|subject', e.g. '2-2|AE|MMTF'.
If no entry exists, the app will show a demo card telling you to add a link.

---

How to Add a Notice / Routine / Result

Simply push a new object into the corresponding array:

```javascript
NOTICES.push({ t: 'New notice title', d: 'Aug 25, 2026' });
ROUTINES.push({ t: 'Exam routine L‑3', d: 'Aug 22, 2026' });
RESULTS.push({ t: 'Result L‑2 T‑1', d: 'Aug 21, 2026' });
```

---

How to Add a Phone Number

Add an object to PHONES with the following fields:

```javascript
{ n: 'Name (Bangla)', p: 'Position', ph: '01XXXXXXXXX', c: 'teacher' }
```

Categories: 'teacher', 'staff', 'support'.

---

Changing the Theme

The app automatically follows your device theme. Users can manually switch with the ☀️/🌙 button in the header.
To reset the theme to system default, open the drawer and tap 🔄 System Theme.

---

🧠 Technical Architecture

· Single Page Application (SPA) – All views are dynamically rendered by the render() function.
· Custom Router – Uses the History API (pushState) for back/forward navigation.
· No Dependencies – Pure HTML, CSS, and vanilla JavaScript.
· Performance Optimisations:
  · IntersectionObserver for reveal animations
  · requestAnimationFrame throttled scroll handler
  · Mobile‑specific CSS removes heavy backdrop-filter and animations
  · GPU‑accelerated transform for scroll progress bar
· LocalStorage – Used for theme choice and pinned subjects.

---

📱 Performance Notes

On mobile devices, the following optimisations are automatically applied:

· Background doodles and ambient animations are frozen
· All backdrop-filter effects are removed (replaced with solid backgrounds)
· Fixed header and bottom nav become solid glass to avoid repaint lag
· Scroll progress bar uses transform: scaleX() instead of width changes
· Box shadows are reduced for smoother rendering

These changes keep the visual design essentially identical while eliminating janky scrolling.

---

🤝 Credits

· Project idea & development – PTEC students
· Data sources – Official PTEC notices, teacher contacts, public Drive links
· Icons – Emoji + custom SVG (textile machinery doodles)

---

📄 License

This project is unofficial and intended for student use only.
You are free to modify and share it within your college.
If you deploy it publicly, please give credit to the original creators.

---

🐛 Known Limitations

· The app is offline‑only (except for external Google Drive links).
· FILES object currently contains only one real example (2-2|AE|MMTF). Others are demo placeholders.
· The SUBMIT_FORM_URL is empty – you may replace it with a Google Form link.
· The syllabus section shows placeholder content; no actual PDFs are linked yet.

---

🚧 Future Improvements

· Add PWA manifest for installable experience
· Integrate Firebase for dynamic content
· Add more subjects and Drive links
· Multi‑language support (English/Bangla)
· User accounts for personalised pins

---

Made with ❤️ by PTEC students

```
