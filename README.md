<p align="center">
  <img width="425" height="259" alt="usernotes running in a terminal" src="https://github.com/user-attachments/assets/794974dc-6e72-4c65-83fd-cac8bb322e0e" />
</p>
<div align="center">
  <h1>usernotes</h1>

A terminal task manager with the look and feel of **Claude Code / Codex CLI** — create tasks through a chat-style input box, then switch to keyboard-driven navigation to manage your list, with a live Markdown roadmap kept in sync automatically.

[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-green)](#-installation)
[![Built with](https://img.shields.io/badge/built%20with-Python%20%2B%20Textual-3776AB)](https://textual.textualize.io)
[![Packaged with](https://img.shields.io/badge/packaged%20with-PyInstaller-FFD43B)](https://pyinstaller.org)
</div>

---

## ✨ What It Does

- **Chat-style task capture** — type naturally into a single input box; the first entry names the list, everything after becomes a task
- **Keyboard-driven navigation** — leave typing mode with `↑` / `↓` and manage the whole list without touching a mouse
- **Five-stage status tracking** — Pending, In Progress, Done, Deferred, Cancelled, one keypress away
- **Up Next spotlight** — pin a single task above the rest, both on screen and in the exported roadmap, while it stays in its normal group too
- **Groups turn a list into a roadmap** — organize tasks under named sections that keep their creation order
- **Live Markdown roadmap export** — every change (status, order, groups, Up Next) is mirrored automatically to a `.md` file in the folder usernotes was launched from, ready to commit straight into a repo
- **Slash command palette** — `/` opens autocomplete for every action, from `/done N` to `/newgroup Name`
- **10 built-in themes** — Textual Dark, Nord, Gruvbox, Dracula, Tokyo Night, Monokai, Catppuccin Mocha/Latte, Solarized Dark, Rosé Pine

---

## 📖 How to Use

1. **Launch usernotes** and pick **New Task List** or **Continue Task List** from the main menu (`↑`/`↓` to move, `Enter` to select). Saved lists show their completion progress here and can be deleted right from the keyboard.
2. **Name your list.** In a new list, the first thing you type and submit becomes the list name.
3. **Add tasks.** Keep typing and pressing `Enter` — every submission after the name adds a task while you're still in typing mode.
4. **Switch to navigate mode** with `↑` or `↓` once you have tasks to manage.
5. **Move a task through its lifecycle** with `1`–`5` (Pending → In Progress → Done → Deferred → Cancelled), star it with `u` for Up Next, or edit/delete it with `Enter` / `Backspace`.
6. **Organize with groups** using `/newgroup Name` and `/group N Name` to turn a flat list into a proper roadmap.
7. **Check the exported roadmap** — usernotes writes a matching `.md` file to the folder it was launched from, and keeps it updated automatically as you work.

### Example exported roadmap

```markdown
# FullVolume Roadmap

## Up Next

- [ ] Improve vocal track smoothing ⭐

## Quality of Life Improvements

- [ ] Improve performance and loading times

## Bugfixes

- [ ] Fix incorrect song previews
```

---

## ⌨️ Navigation Reference

| Key                    | Action             |
| ---------------------- | ------------------ |
| `↑` / `↓`              | Move between tasks |
| `1`                    | Pending            |
| `2`                    | In Progress        |
| `3`                    | Done               |
| `4`                    | Deferred           |
| `5`                    | Cancelled          |
| `u`                    | Toggle Up Next     |
| `Enter`                | Edit task          |
| `Backspace` / `Delete` | Delete task        |
| `n`                    | Add a new task     |
| `Esc`                  | Return to typing   |

The selection stays on the current task when changing its status. Only one task can be marked **Up Next** at a time.

## 🔤 Slash Commands

Typing `/` opens a command palette with autocomplete.

| Command           | Action                         |
| ----------------- | ------------------------------ |
| `/help`           | Show available commands        |
| `/rename Name`    | Rename the list                |
| `/up N`           | Mark task as Up Next           |
| `/up clear`       | Clear Up Next                  |
| `/done N`         | Mark task Done                 |
| `/progress N`     | Mark task In Progress          |
| `/pending N`      | Mark task Pending              |
| `/defer N`        | Mark task Deferred             |
| `/cancel N`       | Mark task Cancelled            |
| `/group N Name`   | Add task to a group            |
| `/group N clear`  | Remove task from its group     |
| `/newgroup Name`  | Create a group                 |
| `/delgroup Name`  | Delete a group                 |
| `/groups`         | Show groups                    |
| `/clear-done`     | Remove completed tasks         |
| `/sort`           | Sort by group and status       |
| `/stats`          | Show completion statistics     |
| `/export`         | Re-export the Markdown roadmap |
| `/menu`           | Return to the main menu        |
| `/delete confirm` | Delete the current list        |

`Ctrl+Q` quits usernotes from anywhere.

---

## ⚙️ Settings

- **Themes** — 10 built-in options, switchable any time
- **Delete confirmation** — toggle a safety prompt before deleting tasks or lists
- **Markdown roadmap export** — toggle automatic `.md` mirroring on or off
- **Hint bar** — toggle the on-screen key hints

Settings and task lists are saved automatically in:

```text
~/.usernotes/
├── lists/
└── settings.json
```

On Windows:

```text
C:\Users\<you>\.usernotes\
```

---

## 🐛 Troubleshooting

**`usernotes` isn't recognized after building on Windows**
Open a *new* terminal window after running `build.bat` — PATH changes don't apply to terminals that were already open.

**Markdown roadmap isn't updating**
Check that export is enabled in **Settings**, and confirm you're looking in the folder usernotes was actually launched from — that's where the `.md` file is written.

**`build.bat` fails with a Python version error**
Confirm Python 3.10.7+ is installed and was added to PATH during setup; re-run the Python installer with "Add to PATH" checked if you skipped it the first time.

**A saved list won't open from Continue Task List**
Make sure the list file wasn't moved or edited outside usernotes — the app expects its own format in `~/.usernotes/lists/`.

---

## 📥 Installation

### Windows

1. Install **Python 3.10.7+** and make sure it's added to PATH.
2. Keep `usernotes.py`, `requirements.txt`, and `build.bat` in the same folder.
3. Run `build.bat`.

This installs the dependencies, builds a standalone executable, and adds `usernotes` to your User PATH. Python does **not** need to remain installed after the build. Open a new terminal and launch it anywhere with:

```text
usernotes
```

To update usernotes, run `build.bat` again.

### Run with Python (any OS)

```bash
pip install -r requirements.txt
python3 usernotes.py
```

Works on any OS supported by Python and Textual.

---

## 💬 Support

Found a bug, or something not behaving the way this README says it should? [Open an issue](../../issues) with what you were doing and what happened instead.

---

## Built With

* Python
* Textual
* PyInstaller

---

Made with ⌨️ by JURMR
