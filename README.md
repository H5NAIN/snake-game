# 🐍 Google Play Arcade: Snake Game

A fast, polished browser Snake game built as a single HTML file — no install, no build step, just open it and play. Runs fully offline (except the live global leaderboard, which needs internet).

**Made by HUSNAIN.**

---

## 🎮 Play it by clicking this link (https://h5nain.github.io/snake-game/)

It works on all devices like desktop, mobile, tablet, or a Smart TV browser (Android TV / Bravia and similar).

Works fully offline. Only the global leaderboard requires an internet connection — everything else (movement, sound, shop, skins, controls) works with no connection at all.

---

## ✨ Features

- **Three map sizes** — Small, Medium, and Large, each with its own score cap and unlock tiers.
- **Four speed settings** — Easy, Normal, Hard, and Insane.
- **Combo system** — chain fruit pickups quickly to multiply your score.
- **Global leaderboard** — top 50 scores worldwide, live via Firebase (requires internet).
- **Shop system** — unlock and equip:
  - 🐍 **Snake skins** (Classic, Emerald, Inferno, Amber, Void, and an exclusive **Golden** skin earned only by winning all three map sizes)
  - 🟩 **Grid color themes**
  - 💡 **Boundary glow themes**
  - Everything unlocks by reaching score milestones — nothing is ever spent, unlocks are permanent.
- **Reset Game button** — wipes your own leaderboard entry and all local progress, so you can start fresh as a new player.
- **In-memory anti-cheat** — flags and discards runs where the score doesn't match what was actually earned in-game (see *Security notes* below).
- **Real emoji fruit art** — same emoji artwork (via Twemoji) on every device, instead of each device's own inconsistent emoji font.

---

## 🕹️ Controls

Controls automatically adapt to the device you're playing on:

| Device | Controls |
|---|---|
| **PC / laptop** | Arrow keys or WASD to move · `P` or `Enter` to pause/resume · Spacebar/Enter to restart |
| **Phone / tablet** | Swipe anywhere on the page, **or** tap the on-screen D-pad below the game — both work at the same time, use whichever you prefer |
| **Smart TV (Android TV / Bravia, etc.)** | Full D-pad remote support: steer the snake in-game, and navigate every menu/button (before the game starts, on pause, and on game-over/win screens) by pressing the D-pad — the selected button highlights, and the center **OK** button activates it, exactly like a native TV app |

---

## 🔧 Tech notes

- Single self-contained HTML file — HTML, CSS, and JavaScript all in one place.
- Uses [Firebase Firestore](https://firebase.google.com/docs/firestore) for the live global leaderboard, loaded as a **dynamic import** so a lack of internet only disables the leaderboard rather than breaking the whole game.
- Canvas-based rendering with several performance optimizations for weaker mobile/TV hardware: a pre-rendered/cached grid background, a cached snake-body gradient, and a cached boundary glow — all recomputed only when something actually changes, not every frame.
- No build tools, no dependencies to install, no bundler — just open the HTML file.

---

## 🔒 Security notes

Score validation (grid-size score caps + in-memory integrity checks) runs client-side, which stops casual tampering but can't fully stop a determined attacker from hitting Firestore directly. The durable fix is mirroring the same score caps in **Firestore Security Rules** — see the comment block at the top of the `<script>` section in `index.html` for the exact rule to add in the Firebase console.

The shop (skins/themes/unlocks) is stored entirely in each browser's local storage and never touches the shared Firestore leaderboard — it's private per-device progress, separate from everyone else's global scores.

---

## 📄 License

All rights reserved by the author unless stated otherwise.
