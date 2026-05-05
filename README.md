# Work-Storage

**Work-Storage** is an open-source, cross-platform cloud storage application built by **worksuvadh**. It turns your Telegram account into an unlimited, secure cloud workspace — giving you a familiar file explorer interface to upload, organize, and manage files.

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20MacOS%20%7C%20Linux%20%7C%20Web-blue)
![Project](https://img.shields.io/badge/project-worksuvadh-indigo)

## What is Work-Storage?

Work-Storage uses Telegram's cloud infrastructure as a backend, letting you upload and organize files through a clean, modern file explorer interface. Your files are stored in your Telegram "Saved Messages" and private channels — giving you effectively unlimited storage for free.

### Key Features

- **Unlimited Cloud Storage** — Powered by Telegram's cloud (up to 2 GB per file free, 4 GB with Telegram Premium)
- **No Login Required** — Open the web UI directly without Telegram credentials (browser mode)
- **High Performance Grid** — Virtual scrolling handles folders with thousands of files instantly
- **Media Streaming** — Stream video and audio files directly without downloading
- **PDF Viewer** — Built-in PDF support with infinite scrolling
- **Drag & Drop** — Intuitive drag-and-drop upload interface
- **Thumbnail Previews** — Inline thumbnails for images and media
- **Folder Management** — Create folders (private Telegram Channels) to organize content
- **Privacy Focused** — API keys and data stay local; no third-party servers
- **Cross-Platform** — Runs as a desktop app (Windows, macOS, Linux) or in a browser

## Screenshots

| Dashboard | Authentication |
|-----------|----------------|
| ![Dashboard](screenshots/DashboardWithFiles.png) | ![Login](screenshots/LoginScreen.png) |

| Grid View | File Preview |
|-----------|--------------|
| ![Grid](screenshots/DarkModeGrid.png) | ![Preview](screenshots/ImagePreview.png) |

## Tech Stack

- **Frontend**: React 19, TypeScript, TailwindCSS v4, Framer Motion
- **Desktop Backend**: Rust (Tauri v2), Grammers (Telegram MTProto client)
- **Build Tool**: Vite
- **Package Manager**: npm

## Getting Started

### Run in Browser (No Setup Required)

The easiest way to try Work-Storage is in your browser:

1. Open the app URL
2. Click **"Open App — No Login Required"**
3. Explore the full UI instantly

> Note: File operations (upload/download) require connecting a Telegram account.

### Desktop App Setup

#### Prerequisites

- **Node.js v18+** — [Download](https://nodejs.org/)
- **Rust (latest stable)** — Install via [rustup](https://rustup.rs/):
  ```bash
  curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
  ```
- **Telegram API Credentials**:
  1. Go to [my.telegram.org](https://my.telegram.org)
  2. Click "API development tools"
  3. Create an app and copy your `api_id` and `api_hash`

#### Linux Dependencies (Ubuntu/Debian)

```bash
sudo apt update && sudo apt install libwebkit2gtk-4.1-dev build-essential curl wget file libxdo-dev libssl-dev libayatana-appindicator3-dev librsvg2-dev
```

#### Install & Run

```bash
# Clone the repository
git clone https://github.com/worksuvadh/work-storage.git
cd work-storage/app

# Install dependencies
npm install

# Run in browser mode (no Rust required)
npm run dev

# Run as desktop app (requires Rust)
npm run tauri dev
```

> **First build note:** The initial Tauri build downloads and compiles 300+ Rust crates. This takes 5–15 minutes. Subsequent builds are much faster.

#### Build for Production

```bash
npm run tauri build
```

## Storage Details

| Location | What is stored |
|---|---|
| Browser `localStorage` | Settings, preferences, folder list, queue state |
| Telegram Saved Messages | Default file storage (unlimited) |
| Private Telegram Channels | Named folders you create in the app |

## How Much Storage Do I Get?

| Plan | Max File Size | Total Storage |
|---|---|---|
| Free Telegram | 2 GB per file | Unlimited |
| Telegram Premium | 4 GB per file | Unlimited |

## Project Structure

```
app/                    # Frontend + Tauri root
  src/                  # React frontend (TypeScript)
    components/         # UI components
    hooks/              # React hooks
    context/            # Theme, Confirm, DropZone
    mocks/              # Browser stubs for Tauri APIs
  src-tauri/            # Rust backend
  public/               # Static assets (logo, icons)
  vite.config.ts        # Vite configuration
```

## Made by worksuvadh

Work-Storage is developed and maintained by the **worksuvadh** project.

- Built with open-source tools
- Privacy-first design — no tracking, no telemetry
- Your data, your storage, your control

## License

MIT License — see [LICENSE](LICENSE) for details.
