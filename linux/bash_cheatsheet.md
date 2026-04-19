# Bash Cheat Sheet (Essential Shortcuts & Commands)

## 🧠 Basics
- `Ctrl + C` → Cancel current command
- `Ctrl + D` → Exit shell
- `Ctrl + L` → Clear screen

---

## ⌨️ Cursor Movement
- `Ctrl + A` → Move to beginning of line
- `Ctrl + E` → Move to end of line
- `Alt  + B` → Move back one word
- `Alt  + F` → Move forward one word

---

## ✂️ Editing / Deleting
- `Ctrl + U` → Delete from cursor → beginning
- `Ctrl + K` → Delete from cursor → end
- `Ctrl + W` → Delete previous word
- `Ctrl + D` → Delete character
- `Ctrl + _` → Undo last change

---

## 📋 Copy / Paste (Kill & Yank)
- `Ctrl + U` → Cut to beginning
- `Ctrl + K` → Cut to end
- `Ctrl + W` → Cut word
- `Ctrl + Y` → Paste (yank)

---

## 🔍 Command History
- `Ctrl + P` → Previous command
- `Ctrl + N` → Next command
- `↑ / ↓` → Navigate history

### 🔥 Reverse Search
- `Ctrl + R` → Search command history
  - Type keyword (e.g. `docker`)
  - `Ctrl + R` → next match
  - `Enter` → run command
  - `→` → edit before running

---

## ⚡ Auto-complete
- `Tab` → Auto-complete file/command
- `Tab Tab` → Show options

---

## 🔄 Useful Shortcuts
- `!!` → Repeat last command
- `!$` → Last argument of previous command

Example:
```bash
mkdir test
cd !$
