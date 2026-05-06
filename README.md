# AzuDl - GC2GD

<p align="center">
  <a href="README.fa.md">فارسی</a> · <strong>English</strong>
</p>

<p align="center">
  <strong>Azizi Universal Downloader - Google Colab to Google Drive</strong>
</p>

<p align="center">
  A clean, practical, and powerful downloader for Google Colab that saves files directly to Google Drive.
</p>

<p align="center">
  <code>Google Colab</code> · <code>Google Drive</code> · <code>aria2</code> · <code>yt-dlp</code> · <code>Python</code>
</p>

---

## Table of Contents

- [What is AzuDl - GC2GD?](#what-is-azudl---gc2gd)
- [For Everyone](#for-everyone)
- [For Developers](#for-developers)
- [Features](#features)
- [Supported Download Types](#supported-download-types)
- [Storage Structure](#storage-structure)
- [How to Use](#how-to-use)
- [Menu Guide](#menu-guide)
- [YouTube Quality Guide](#youtube-quality-guide)
- [Speed Limit Guide](#speed-limit-guide)
- [Download History](#download-history)
- [Technical Architecture](#technical-architecture)
- [Dependencies](#dependencies)
- [Troubleshooting](#troubleshooting)
- [Legal and Responsible Use](#legal-and-responsible-use)
- [Developer](#developer)

---

## What is AzuDl - GC2GD?

**AzuDl - GC2GD** is a Python-based downloader designed for **Google Colab**.  
It downloads files using Colab's runtime and saves them directly into your **Google Drive**.

The name means:

> **Azizi Universal Downloader - Google Colab to Google Drive**

It supports multiple download types:

- Torrent magnet links
- YouTube videos and playlists
- Direct download links
- Batch downloads
- Automatic link detection

---

## For Everyone

Imagine you want to download a file, a YouTube video, a playlist, or a torrent magnet, but you do not want to keep your own computer running.

AzuDl - GC2GD lets you:

1. Open Google Colab
2. Paste the code
3. Connect your Google Drive
4. Paste a link
5. Wait for the progress bar
6. Find the downloaded file inside your Drive

You do not need to install anything on your personal computer.  
Everything runs in the browser using Google Colab.

### Simple Example

You choose:

```text
1. Auto detect link
```

Then paste:

```text
https://example.com/file.zip
```

The program detects that it is a direct link and downloads it to Google Drive.

For YouTube, you can choose quality such as:

```text
1080
720
best
```

For torrent magnet links, you can paste a magnet link and the program will download it using `aria2`.

---

## For Developers

AzuDl - GC2GD is built around a single Python class:

```python
class AzuDlGC2GD:
```

The class manages:

- Google Drive mounting
- Folder creation
- aria2 RPC server startup
- JSON-RPC calls to aria2
- Torrent magnet handling
- Direct link downloads
- YouTube downloads through `yt-dlp`
- Progress bars through `tqdm`
- Download history logging
- Auto detection of link types
- Batch processing

The architecture is intentionally simple, portable, and Colab-friendly.

---

## Features

### Core Features

- Google Drive integration
- Auto link detection
- Torrent magnet downloads
- Direct URL downloads
- YouTube video downloads
- YouTube playlist downloads
- YouTube audio-only MP3 downloads
- Quality selection
- Custom YouTube format ID support
- Batch download mode
- Download history
- File listing
- Developer information panel
- Help menu
- Real-time progress bars
- Speed limit support
- Safe folder and file naming
- Resume support for interrupted downloads

### Interface Features

The app provides a simple terminal-style menu:

```text
1. Auto detect link
2. Torrent magnet
3. YouTube video or playlist
4. Direct link
5. Batch download
6. Download history
7. List downloaded files
8. Developer
9. Help
10. Exit
```

---

## Supported Download Types

### 1. Torrent Magnet

Supported format:

```text
magnet:?xt=urn:btih:...
```

Torrent downloads are handled through `aria2c` using RPC mode.

The program enables:

- DHT
- DHT6
- Peer exchange
- Local peer discovery
- Metadata saving
- Resume support
- Zero seed time after completion

### 2. YouTube

Supported YouTube sources include:

- Single videos
- Playlists
- Standard YouTube links
- Short `youtu.be` links
- Music YouTube links

Examples:

```text
https://www.youtube.com/watch?v=VIDEO_ID
https://youtu.be/VIDEO_ID
https://www.youtube.com/playlist?list=PLAYLIST_ID
https://music.youtube.com/watch?v=VIDEO_ID
```

### 3. Direct Links

Supported protocols:

```text
http://
https://
ftp://
```

Examples:

```text
https://example.com/file.zip
https://example.com/video.mp4
https://example.com/archive.rar
https://example.com/document.pdf
```

### 4. Batch Mode

Batch mode lets you paste multiple links one by one.

Supported in batch mode:

- Torrent magnet links
- YouTube links
- Direct links

---

## Storage Structure

AzuDl - GC2GD creates this folder in your Google Drive:

```text
/content/drive/MyDrive/AzuDl-GC2GD
```

Inside it:

```text
AzuDl-GC2GD/
├── TorrentDownloads/
├── YouTubeDownloads/
├── DirectDownloads/
├── BatchDownloads/
└── Logs/
    └── download_history.json
```

### Folder Purpose

| Folder | Purpose |
|---|---|
| `TorrentDownloads` | Stores torrent magnet downloads |
| `YouTubeDownloads` | Stores YouTube videos, playlists, and audio |
| `DirectDownloads` | Stores direct URL downloads |
| `BatchDownloads` | Used for grouped batch operations |
| `Logs` | Stores download history |

---

## How to Use

### Step 1: Open Google Colab

Go to Google Colab and create a new notebook.

### Step 2: Paste the Code

Paste the full AzuDl - GC2GD source code into a cell.

### Step 3: Run the Cell

Run the cell. The program will install required packages:

```text
aria2
ffmpeg
tqdm
requests
yt-dlp
```

### Step 4: Mount Google Drive

Google Colab will ask for permission to connect to your Google Drive.

### Step 5: Choose an Option

Use the menu to select what you want to do.

---

## Menu Guide

### 1. Auto detect link

Best option for most users.

Paste any supported link and the program detects the type automatically.

Supported detection:

| Link Type | Detected As |
|---|---|
| `magnet:?...` | Torrent |
| `youtube.com` | YouTube |
| `youtu.be` | YouTube |
| `music.youtube.com` | YouTube |
| `http://...` | Direct |
| `https://...` | Direct |
| `ftp://...` | Direct |

### 2. Torrent magnet

Use this when you specifically want to download a torrent magnet link.

### 3. YouTube video or playlist

Use this for YouTube videos, playlists, or audio extraction.

### 4. Direct link

Use this for normal file URLs.

### 5. Batch download

Use this when you have multiple links.

### 6. Download history

Shows recent download records.

### 7. List downloaded files

Lists files saved inside project folders.

### 8. Developer

Shows project and developer links.

### 9. Help

Shows built-in help.

### 10. Exit

Closes the program loop.

---

## YouTube Quality Guide

Available quality presets:

```text
best
4320
2160
1440
1080
720
480
360
```

### Recommended Choices

| Choice | Meaning |
|---|---|
| `best` | Best available quality |
| `1080` | Full HD or lower |
| `720` | HD or lower |
| `480` | Lower file size |
| `360` | Smaller downloads |

### Audio Only

When asked:

```text
Audio only? y/n:
```

Enter:

```text
y
```

The program saves audio as MP3 using FFmpeg.

### Custom Format ID

You can list available formats and enter custom IDs.

Examples:

```text
137+140
248+251
22
18
best
```

This is useful when you want exact control over video and audio streams.

---

## Speed Limit Guide

Speed limit is optional.

Examples:

```text
500K
2M
10M
```

Meaning:

| Value | Meaning |
|---|---|
| `500K` | 500 KB/s |
| `2M` | 2 MB/s |
| `10M` | 10 MB/s |
| empty | unlimited |

Speed limits are mainly used by aria2 for torrent and direct downloads.

---

## Download History

Download history is stored in:

```text
/content/drive/MyDrive/AzuDl-GC2GD/Logs/download_history.json
```

Each record can include:

- Type
- Source URL
- Output path
- Time
- Status
- Format
- Error message if failed

Example:

```json
{
  "type": "youtube",
  "source": "https://www.youtube.com/watch?v=VIDEO_ID",
  "output": "/content/drive/MyDrive/AzuDl-GC2GD/YouTubeDownloads/MyFolder",
  "format": "bv*+ba/best",
  "status": "completed",
  "time": "2026-05-06 18:30:00"
}
```

---

## Technical Architecture

### Main Components

```text
AzuDlGC2GD
├── setup
├── aria2 RPC control
├── link detection
├── torrent downloader
├── direct downloader
├── YouTube downloader
├── batch manager
├── history manager
├── file lister
├── help panel
└── developer panel
```

### aria2 RPC

Torrent and direct downloads use `aria2c` in daemon RPC mode:

```text
http://localhost:6800/jsonrpc
```

The app sends JSON-RPC requests to aria2.

Important methods:

```text
aria2.addUri
aria2.tellStatus
```

### yt-dlp

YouTube downloads are handled by `yt-dlp`.

The app uses:

- Format selection
- Playlist support
- Audio extraction
- FFmpeg post-processing
- Download hooks for progress bars

### tqdm

Progress bars are displayed with:

```python
tqdm.notebook
```

This makes it suitable for Google Colab notebooks.

---

## Dependencies

System packages:

```text
aria2
ffmpeg
```

Python packages:

```text
tqdm
requests
yt-dlp
```

Install command used in Colab:

```python
!apt update -qq
!apt install -y aria2 ffmpeg
!pip install -q tqdm requests yt-dlp
```

---

## Troubleshooting

### Google Drive does not mount

Run the cell again and approve Drive access.

### Torrent does not start

Possible reasons:

- No seeders
- Weak magnet link
- Blocked peers
- Metadata unavailable

Try another magnet link or wait longer.

### YouTube download fails

Possible reasons:

- Video is private
- Region restriction
- Age restriction
- Login required
- yt-dlp needs an update

Try updating:

```python
!pip install -U yt-dlp
```

### Direct link fails

Possible reasons:

- Link expired
- Server blocks Colab
- Authentication required
- Cookies required
- Temporary token expired

### Progress bar does not show total size

Some servers do not provide file size.  
The download may still work.

---

## Legal and Responsible Use

AzuDl - GC2GD is a downloader tool.  
Use it only for content you have the right to download and store.

Responsible examples:

- Your own files
- Public domain content
- Creative Commons content
- Open-source releases
- Backups of your own data
- Files shared with permission

Do not use this tool to download or distribute copyrighted content without permission.

---

## Developer

**Project:** AzuDl - GC2GD  
**Full Name:** Azizi Universal Downloader - Google Colab to Google Drive  
**Developer:** The Azizi

### Links

- X: https://x.com/the_azzi
- GitHub: https://github.com/TheGreatAzizi
- Telegram: https://t.me/luluch_code
- Git: https://git.theazizi.ir/TheAzizi
- Website: https://theazizi.ir

---

## Final Note

AzuDl - GC2GD is designed to be simple enough for normal users and flexible enough for developers.

Use Auto Detect for the easiest workflow.  
Use custom YouTube formats, batch mode, and history features when you need more control.
