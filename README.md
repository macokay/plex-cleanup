# PlexCleanup

[![License](https://img.shields.io/badge/license-Non--Commercial-blue.svg)](#license)
[![GitHub release](https://img.shields.io/github/release/macokay/plex-cleanup.svg)](https://github.com/macokay/plex-cleanup/releases)

A single-file browser tool for identifying and cleaning up your Plex library. Connects directly to your local Plex server — no installation, no external services, no cloud.

---

## Requirements

- A running [Plex Media Server](https://www.plex.tv/media-server-downloads/)
- Safari (recommended) or Chrome served via a local web server (see below)

Everything else — Tautulli, Radarr, Sonarr — is optional.

> **Chrome users:** Chrome blocks requests from `file://` URLs to local network addresses. Either use Safari, or serve the file via a local web server:
> ```
> cd ~/Downloads && python3 -m http.server 8765
> ```
> Then open `http://localhost:8765/plex-cleanup.html`

---

## Data sources

PlexCleanup works with just Plex alone, but gets more powerful with Tautulli added. Radarr and Sonarr are only needed if you want to delete through them.

### Plex only (minimum setup)
Everything runs on Plex's own API. You get the full library, posters, file sizes, filters, charts, and deletion. The only thing missing is the Half-watched filter.

### Plex + Tautulli (recommended)
Tautulli adds detailed play history per user, including how much of each title was actually watched. This enables the Half-watched filter and gives more accurate play counts. **Using both is recommended** for the best experience.

### + Radarr and/or Sonarr (optional)
If you manage your library through Radarr or Sonarr, you can route deletions through them instead of Plex directly. This removes titles from monitoring and queues cleanly. You can enable Radarr, Sonarr, both, or neither — independently of each other.

---

## Features

- Full library view with poster, title, year, size, date added, last watched, play count
- **Filters:**

| Filter | Data source | Notes |
|--------|-------------|-------|
| Never watched | Plex | 0 plays |
| Added, never started (6m+) | Plex | Added 6+ months ago, never played |
| Half-watched (<50%, 3m+) | Tautulli | Requires Tautulli |
| Collecting dust (1yr+) | Plex | Last watched 12+ months ago |
| Large file | Plex | Movies >18 GB, Shows >80 GB |

- **Delete** via Plex API, Radarr, or Sonarr — with confirmation dialog
- Radarr/Sonarr matching via TMDB/IMDB/TVDB IDs, with title+year as fallback
- If a title isn't found in Radarr/Sonarr, deletion falls back to Plex automatically
- Posters loaded directly from your Plex server — no third-party API needed
- Charts: Movies vs Shows, Disk usage by type, Top genres, Languages
- Export marked titles as CSV or XLS
- Settings saved to localStorage — auto-connects on next visit
- Test connection buttons for each service
- Built-in debug panel — no browser devtools needed

---

## Setup

1. Download `plex-cleanup.html`
2. Open it in Safari (or via a modern browser)
3. The Settings modal opens automatically on first visit
4. Enter your Plex URL and Token — that's the minimum required
5. Optionally add Tautulli, Radarr, and/or Sonarr
6. Press **Save & connect**

---

## Finding your credentials

### Plex Token
1. Open [app.plex.tv](https://app.plex.tv) and sign in
2. Click any media item → `⋯` menu → **Get Info**
3. Click **View XML** in the bottom-left corner
4. Copy the value of `X-Plex-Token=` from the URL

[Official Plex guide →](https://support.plex.tv/articles/204059436-finding-an-authentication-token-x-plex-token/)

### Allowing Plex to delete files
In Plex: **Settings → Server → Library → enable "Allow media deletion"**

[Official guide →](https://support.plex.tv/articles/202606363-how-do-i-delete-something-from-my-library/)

### Tautulli API Key
1. Open Tautulli → **Settings** → **Web Interface**
2. Scroll to the **API** section and copy the **API Key**

### Radarr / Sonarr API Key
1. Open Radarr or Sonarr → **Settings** → **General**
2. Copy the **API Key** value

---

## Credits

Built by [Mac O Kay](https://github.com/macokay).

---

## License

© 2026 Mac O Kay
Free to use and modify for personal, non-commercial use.
Credit appreciated if you share or build upon this work.
Commercial use is not permitted.
