# 词博士 Ci Boshi — English Vocabulary Master

## Quick Start

This is a local HTML prototype. To run it:

1. Open `index.html` in any browser
2. Works on phone, iPad, and computer
3. All data saves locally (localStorage)

## For GitHub Pages Deployment

When pushing to GitHub:
```bash
git add index.html SPEC.md
git commit -m "Add vocab-master app"
git push -u origin main
```

Then enable GitHub Pages in repo Settings → Pages → Source: main branch

The app will be live at: `https://ciboshir.github.io/vocab-master/`

## Features

- SRS spaced repetition algorithm (SM-2)
- Phrase-based vocabulary cards
- Browser TTS audio
- Progress tracking with streak
- Responsive design (phone/iPad/desktop)
- 200 中考高频词 with phrases

## File Structure

```
vocab-master/
├── SPEC.md      # Full product specification
└── index.html   # The complete app (single file)
```