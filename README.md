# 🔥 Campfire Write — Storytelling Studio

A fully-featured, Firebase-powered modular storytelling platform.

## ✨ Features

### Modules
- **📊 Dashboard** — Project overview, writing stats, word count progress bar
- **👥 Characters** — Full CRUD, image upload to Firebase Storage, relationship linking, tags
- **🌍 World & Lore** — Rich text entries with categories and image support
- **🕸️ Relationship Web** — Visual canvas graph of character connections
- **📅 Timeline** — Events with dates, colors, character links
- **🎬 Plot & Arcs** — Story arc management, drag-and-drop scene board
- **✍️ Manuscript** — Quill rich text editor, autosave to Firestore, word count
- **📝 Notes** — Markdown-supported quick notes
- **⚙️ Settings** — Theme (dark/light/sepia), font selector, accent color, saved to Firebase

### Extra Features
- 🍅 **Pomodoro Timer** — Configurable focus sessions
- 🔥 **Writing Streak** — Tracks consecutive writing days
- 🎨 **Theme System** — Dark (default), Light, Sepia + 8 accent colors
- 🔤 **5 Font Choices** — DM Sans, Lora, Instrument Serif, Playfair Display, JetBrains Mono
- ⊞ **Focus Mode** — Hides UI chrome for distraction-free writing
- 📸 **Image Upload** — Characters & Lore images stored in Firebase Storage

## 🚀 Setup

### 1. Open the file
This is a **single-file HTML app** — just open `index.html` in any modern browser.

```
# Option A: Direct open
Open campfire-write/index.html in Chrome, Firefox, or Edge

# Option B: Local server (recommended)
cd campfire-write
npx serve .
# Then visit http://localhost:3000
```

### 2. Firebase is pre-configured
The app uses the Firebase project `campfire-replical` — no additional setup required.

Firebase services used:
- **Firestore** — All data storage
- **Firebase Storage** — Image uploads

### 3. Start writing!
1. Click **Projects** in the top bar (or the project selector in the sidebar)
2. Create your first project
3. Start adding characters, lore, and manuscripts

## 📁 Project Structure

```
campfire-write/
└── index.html          # Complete single-file application
    ├── Firebase SDK    # Loaded from CDN
    ├── Quill.js        # Rich text editor
    ├── All CSS         # Embedded design system
    └── All JavaScript  # App logic, Firebase operations
```

## 🔥 Firebase Collections

| Collection     | Data                                              |
|----------------|---------------------------------------------------|
| `projects`     | Project metadata, arcs                            |
| `characters`   | Name, role, background, imageUrl, tags            |
| `lore`         | Title, category, summary, rich content, imageUrl  |
| `events`       | Title, date, description, characters, color       |
| `relationships`| charA, charB, type, description                   |
| `manuscripts`  | Title, content (HTML), scenes, status             |
| `notes`        | Title, content (Markdown)                         |
| `settings`     | theme, font, accentColor, dailyGoal               |

All documents include `projectId`, `createdAt`, `updatedAt`.

## 🎨 Themes

| Theme | Description |
|-------|-------------|
| Dark  | Default — deep blacks and purples |
| Light | Clean white interface |
| Sepia | Warm amber tones for writing mood |

## 🔤 Fonts

| Font | Style |
|------|-------|
| DM Sans | Modern, clean sans-serif |
| Lora | Elegant, readable serif |
| Instrument Serif | Literary, refined |
| Playfair Display | Classic, editorial |
| JetBrains Mono | Monospace, technical |

## 💡 Tips

- **Autosave**: Manuscripts autosave 1 second after you stop typing
- **Focus Mode**: Click ⊞ in the sidebar footer to hide all UI chrome
- **Pomodoro**: Click 🍅 to start a focus session (configurable in Settings)
- **Relationship Web**: Add 2+ characters first, then add relationships to see the visual graph
- **Image Upload**: Click the dashed upload area on character/lore forms to upload images to Firebase Storage

## ⚠️ Firebase Security

This app is configured for **personal/single-user use without authentication**. 

For production use, configure Firestore Security Rules:
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true; // Change for production!
    }
  }
}
```

Enable CORS for Firebase Storage in the Firebase Console for image uploads to work.
