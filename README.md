# tmux config

## Features

- **Login shell** — `.zprofile` is sourced in every pane
- **Window navigation** — `Shift+Left/Right` to cycle windows
- **Pane navigation** — `Ctrl+h/j/k/l` to move between panes (no prefix needed)
- **Mouse support** — click to switch panes
- **Cross-platform clipboard integration** — copy-mode selections and mouse drag copies use `pbcopy` (macOS), `wl-copy`/`xclip`/`xsel` (Linux), or `clip.exe` (WSL)
- **Active pane highlight** — blue border + `▶` indicator on the active pane
- **Session persistence** — sessions survive reboots via `tmux-resurrect` + `tmux-continuum` (auto-saves every 15 min)

## Install on a new machine

### 1. Install tmux

```bash
# macOS
brew install tmux

# Ubuntu/Debian
sudo apt install tmux
```

### 2. Install TPM (plugin manager)

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

### 3. Copy the config

```bash
curl -fsSL https://raw.githubusercontent.com/LatencyTDH/tmux-config/main/.tmux.conf -o ~/.tmux.conf
```

Or clone and symlink:

```bash
git clone https://github.com/LatencyTDH/tmux-config.git ~/tmux-config
ln -s ~/tmux-config/.tmux.conf ~/.tmux.conf
```

### 4. Install plugins

Start tmux, then press `prefix + I` (capital i) to fetch plugins.

> Default prefix is `Ctrl+b`

### Clipboard helper notes

- **macOS** — no extra setup; `pbcopy` is built in
- **Linux (Wayland)** — install `wl-copy` via `wl-clipboard`
- **Linux (X11)** — install either `xclip` or `xsel`
- **WSL** — no extra setup if `clip.exe` is available in `PATH`

If none of those clipboard helpers are installed, copy-mode still fills tmux's paste buffer, but it will not reach the system clipboard.

That's it — session restore will kick in automatically on next launch.
