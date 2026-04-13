<div align="center">

```
 __   _______ ____
 \ \ / /_   _| ___|
  \ V /  | | |___ \
   \_/   |_| |____/
```

# YTE — YouTube Terminal Edition

**Watch, search, stream, and download YouTube — entirely from your Linux terminal.**

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)](https://python.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Linux-orange?logo=linux)](https://github.com/chambtai-sys/YTE)
[![Powered by yt-dlp](https://img.shields.io/badge/Powered%20by-yt--dlp-red)](https://github.com/yt-dlp/yt-dlp)
[![TUI: Rich](https://img.shields.io/badge/TUI-Rich-blueviolet)](https://github.com/Textualize/rich)

</div>

---

## ✨ Features

| Feature | Description |
|---|---|
| 🔍 **Search** | Search YouTube from your terminal instantly — no API key required |
| 🔥 **Trending** | Browse trending: Now, Music, Gaming, Films |
| ▶ **Stream** | Play videos or audio-only via `mpv` (or your preferred player) |
| ⬇ **Download** | Save videos as MP4 or audio as MP3/AAC with ffmpeg |
| 📋 **Video Info** | View title, channel, views, likes, upload date, and description |
| 📝 **Queue** | Build a playlist and play it sequentially |
| ★ **Bookmarks** | Save your favourite videos locally for quick access |
| 🕓 **History** | Auto-tracks everything you watch (last 200 entries) |
| ⚙ **Config** | INI-based config — change player, quality, download paths |
| 📄 **Paging** | Navigate through multi-page search results |

---

## 🖥 Preview

```
╭─────────────────────────────────────────────────────╮
│   __   _______ ____                                 │
│   \ \ / /_   _| ___|                               │
│    \ V /  | | |___ \                               │
│     \_/   |_| |____/                                │
│         YouTube Terminal Edition                    │
│   v1.0.0  •  github.com/chambtai-sys/YTE            │
╰─────────────────────────────────────────────────────╯

⌨  Keybindings
╭──────┬──────────────────────────╮
│ Key  │ Action                   │
├──────┼──────────────────────────┤
│ [s]  │ New search               │
│ [t]  │ Browse trending          │
│ [p]  │ Play selected video      │
│ [a]  │ Play audio only          │
│ [d]  │ Download video           │
│ [A]  │ Download audio (mp3)     │
│ [i]  │ Show video info          │
│ [b]  │ Toggle bookmark          │
│ [q]  │ Add to queue             │
│ [Q]  │ Play queue               │
│ [n]  │ Next page                │
│ [P]  │ Previous page            │
│ [h]  │ View history             │
│ [B]  │ View bookmarks           │
│ [c]  │ Clear screen             │
│ [x]  │ Quit YTE                 │
╰──────┴──────────────────────────╯

🎬  Results for "lofi hip hop"  (page 1/3)
╭───┬────────────────────────────────────┬──────────────┬──────────┬─────────╮
│ # │ Title                              │ Channel      │ Duration │  Views  │
├───┼────────────────────────────────────┼──────────────┼──────────┼─────────┤
│ 1 │ lofi hip hop radio 📚 beats to...  │ Lofi Girl    │ LIVE     │  1.2B   │
│ 2 │ Lofi Hip Hop Mix - Beats to Study  │ ChilledCow   │ 1:02:34  │ 345.2M  │
╰───┴────────────────────────────────────┴──────────────┴──────────┴─────────╯
```

---

## 📦 Installation

### Prerequisites

```bash
# Debian / Ubuntu
sudo apt install mpv ffmpeg python3 python3-pip git

# Arch / Manjaro
sudo pacman -S mpv ffmpeg python python-pip git

# Fedora
sudo dnf install mpv ffmpeg python3 python3-pip git
```

### Install YTE

```bash
# 1. Clone the repo
git clone https://github.com/chambtai-sys/YTE.git
cd YTE

# 2. Install Python dependencies
pip install -r requirements.txt

# 3. Run it
python3 yte.py
```

### Optional: Install as a system command

```bash
# Symlink for global use
sudo ln -s "$(pwd)/yte.py" /usr/local/bin/yte
chmod +x yte.py

# Then just type:
yte
```

Or via pip editable install:

```bash
pip install -e .
yte
```

---

## 🚀 Usage

### Interactive TUI (recommended)

```bash
yte
```

Launches the full interactive TUI. Press `?` at any time to see keybindings.

### CLI Subcommands

```bash
# Search YouTube
yte search "lofi hip hop"
yte search "rick astley" -n 20       # 20 results

# Play a video URL directly
yte play https://www.youtube.com/watch?v=dQw4w9WgXcQ
yte play https://www.youtube.com/watch?v=dQw4w9WgXcQ --audio-only

# Download
yte download https://www.youtube.com/watch?v=dQw4w9WgXcQ           # MP4
yte download https://www.youtube.com/watch?v=dQw4w9WgXcQ --audio-only  # MP3

# Browse trending
yte trending

# View history
yte history

# Open config in editor
yte config
```

---

## ⚙ Configuration

Config is stored at `~/.config/yte/config.ini` and auto-created on first run.

```ini
[player]
video_player      = mpv
audio_only_player = mpv --no-video
default_quality   = best

[download]
output_dir   = ~/Downloads/YTE
format       = bestvideo+bestaudio/best
audio_format = mp3

[ui]
results_per_page = 10
color_scheme     = default
show_thumbnails  = false
```

### Supported Players

| Player | Install | Config value |
|--------|---------|---------------|
| **mpv** *(recommended)* | `sudo apt install mpv` | `mpv` |
| vlc | `sudo apt install vlc` | `vlc` |
| mplayer | `sudo apt install mplayer` | `mplayer` |
| celluloid | `sudo apt install celluloid` | `celluloid` |

---

## 📁 Data & Files

| Path | Contents |
|------|----------|
| `~/.config/yte/config.ini` | User settings |
| `~/.config/yte/history.json` | Watch history (last 200 entries) |
| `~/.config/yte/bookmarks.json` | Saved bookmarks |
| `~/Downloads/YTE/` | Downloaded files (default output) |

---

## 🛠 Requirements

- **Python** 3.10+
- **mpv** (or any yt-dlp-compatible player)
- **ffmpeg** (for downloads & audio extraction)

Python packages (`requirements.txt`):

```
yt-dlp>=2024.1.1
rich>=13.7.0
readchar>=4.0.5
```

---

## 🗺 Roadmap

- [ ] Channel browsing & subscriptions
- [ ] Subtitle display in terminal
- [ ] Thumbnail art (kitty / sixel terminals)
- [ ] Playlist import/export (M3U, JSON)
- [ ] Watch later sync
- [ ] Plugin system for custom sources

---

## 🤝 Contributing

Pull requests are welcome!

1. Fork the repo
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m "feat: add my feature"`
4. Push the branch: `git push origin feature/my-feature`
5. Open a Pull Request

---

## 📝 License

This project is licensed under the **MIT License** — see [LICENSE](LICENSE) for details.

---

## ⚠ Disclaimer

YTE is an open-source tool for personal use. It does not host, cache, or redistribute any YouTube content.
All media is streamed or downloaded directly from YouTube via yt-dlp. Use responsibly and in accordance with
[YouTubes Terms of Service](https://www.youtube.com/t/terms).

---

<div align="center">
Made with ❤️ and a Linux terminal
<br><br>
⭐ Star this repo if you find it useful!
</div>
