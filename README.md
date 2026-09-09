# usernotes

A terminal task manager with the look and feel of **Claude Code / Codex CLI**.

Create tasks through a chat-style input box, then switch to keyboard-driven navigation to manage your list.

## Windows

The easiest way to install usernotes is with `build.bat`.

1. Install **Python 3.9+** and make sure it's added to PATH.
2. Keep `usernotes.py`, `requirements.txt`, and `build.bat` in the same folder.
3. Run `build.bat`.

The script installs the dependencies, builds a standalone executable, and adds `usernotes` to your User PATH.

After opening a new terminal, you can launch it anywhere with:

```text
usernotes
```

Python does **not** need to remain installed after the build.

To update usernotes, run `build.bat` again.

## Run with Python

```bash
pip install -r requirements.txt
python3 usernotes.py
```

Works on any OS supported by Python and Textual.

## Main Menu

```text
New Task List
Continue Task List
Settings
Exit
```

Use `↑` / `↓` to move and `Enter` to select.

## Creating Tasks

Inside a task list, you start in **typing mode**.

Type a task and press `Enter` to add it.

For a new list, the first entry becomes the list name. After that, every submission creates a task.

Press `↑` or `↓` to switch to **navigate mode**.

## Navigation

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

The selection stays on the current task when changing its status.

Only one task can be marked **Up Next** at a time.

## Slash Commands

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

## Groups

Groups turn a task list into a proper roadmap.

For example:

```markdown
# FullVolume Roadmap

## Up Next

- [ ] Improve vocal track smoothing ⭐

## Quality of Life Improvements

- [ ] Improve performance and loading times

## Bugfixes

- [ ] Fix incorrect song previews
```

Create groups with `/newgroup`, or assign a task to a new group directly with `/group`.

Groups keep their creation order in the exported Markdown file.

## Markdown Roadmaps

Every task list can automatically be mirrored to a `.md` file in the folder usernotes was launched from.

Changes are exported automatically when you:

* Add or edit tasks
* Change status
* Reorder tasks
* Change groups
* Change the Up Next task

This makes usernotes useful for maintaining project roadmaps directly inside a GitHub repository.

The **Up Next** task gets its own section at the top of the roadmap while remaining in its normal group below.

## Continue

Saved lists are available from **Continue Task List**.

Each list shows its completion progress and can be opened or deleted from the keyboard.

## Settings

usernotes includes:

* **10 built-in themes**
* **Delete confirmation**
* **Markdown roadmap export toggle**
* **Hint bar toggle**

Available themes:

`Textual Dark` · `Nord` · `Gruvbox` · `Dracula` · `Tokyo Night` · `Monokai` · `Catppuccin Mocha` · `Catppuccin Latte` · `Solarized Dark` · `Rosé Pine`

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

## Built With

* Python
* Textual
* PyInstaller
