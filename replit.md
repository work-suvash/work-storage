# Telegram Drive

## Overview
Telegram Drive is an open-source, cross-platform desktop application that turns your Telegram account into unlimited cloud storage. It uses Telegram's "Saved Messages" and private channels as file storage backends with a familiar file explorer interface.

## Architecture
This is a **Tauri v2 desktop application** — it cannot run as a traditional web app. The Replit environment runs the React/Vite frontend only for development preview purposes.

- **Frontend**: React 19 + TypeScript + TailwindCSS v4 + Framer Motion, built with Vite
- **Desktop Backend**: Rust (Tauri v2) + Grammers (Telegram MTProto client)
- **Build Tool**: Vite (frontend), Cargo (Rust backend)
- **Package Manager**: npm

## Project Structure
```
app/                        # Frontend + Tauri root
  src/                      # React frontend source
    components/             # UI components (AuthWizard, Dashboard, etc.)
    hooks/                  # Custom React hooks
    context/ & contexts/    # Theme, Confirm, DropZone providers
    App.tsx                 # Root component
    main.tsx                # Entry point
  src-tauri/                # Rust backend
    src/                    # Rust source (commands, streaming, auth)
    Cargo.toml              # Rust dependencies (grammers, tauri, tokio)
    tauri.conf.json         # Tauri configuration
  vite.config.ts            # Vite config (port 5000, host 0.0.0.0)
  package.json              # npm dependencies
screenshots/                # App UI screenshots for README
```

## Running in Replit
The workflow `Start application` runs `cd app && npm run dev` on port 5000.

**Important**: When viewed in a browser, the app shows a "Desktop App Required" message. This is intentional — the app requires the Tauri/Rust backend which is only available in the compiled desktop binary.

## Key Features
- Unlimited cloud storage via Telegram API
- Virtual scrolling for large file lists
- Media streaming (video/audio) without full download
- Built-in PDF viewer
- Drag & drop uploads
- Thumbnail previews
- Folder management (private Telegram channels)
- Auto-updates for desktop releases

## Deployment
Configured as a **static** deployment:
- Build: `cd app && npm run build`
- Public dir: `app/dist`

## Development Notes
- Tauri `invoke()` calls communicate with the Rust backend — these fail gracefully in browser environments
- The `AuthWizard` component detects if it's running in a browser (`!('__TAURI_INTERNALS__' in window)`) and shows an info screen
- Vite is configured to allow all hosts for Replit's proxy setup
