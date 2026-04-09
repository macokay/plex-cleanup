<p align="center">
  <!-- ⚠️ MISSING: Project logo (recommended 120x120px PNG with transparent background) -->
</p>

<h1 align="center">PlexCleanup</h1>

<p align="center">
  Single-file browser tool for identifying and cleaning up your Plex library. Connects directly to your local Plex server — no installation, no external services, no cloud.
</p>

<p align="center">
  <a href="https://github.com/macokay/plex-cleanup/releases">
    <img src="https://img.shields.io/github/v/release/macokay/plex-cleanup" alt="GitHub release" />
  </a>
  <img src="https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white" alt="HTML5" />
  <img src="https://img.shields.io/badge/Vanilla%20JS-F7DF1E?logo=javascript&logoColor=black" alt="Vanilla JS" />
  <a href="https://github.com/macokay/plex-cleanup/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/License-Non--Commercial-blue.svg" alt="License" />
  </a>
</p>

<p align="center">
  <a href="https://www.buymeacoffee.com/macokay">
    <img src="https://img.shields.io/badge/Buy%20Me%20A%20Coffee-%23FFDD00.svg?logo=buy-me-a-coffee&logoColor=black" alt="Buy Me A Coffee" />
  </a>
</p>

---

## Features

- Full library view with poster, title, year, size, date added, last watched, play count
- **Filters:**

| Filter | Data source | Notes |
|---|---|---|
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

## Requirements

| Requirement | Details |
|---|---|
| Browser | Safari (recommended) or Chrome via local web server |
| Plex Media Server | Running with API access enabled |
| Tautulli | Optional — required for Half-watched filter and accurate play counts |
| Radarr / Sonarr | Optional — required if routing deletions through them |

> **Chrome users:** Chrome blocks requests from `file://` URLs to local addresses. Either use Safari, or serve the file locally:
> ```bash
> cd ~/Downloads && python3 -m http.server 8765
> ```
> Then open `http://localhost:8765/plex-cleanup.html`

---

## Installation

### Automatic

1. Download the latest `plex-cleanup.html` from [GitHub Releases](https://github.com/macokay/plex-cleanup/releases).
2. Open the file in Safari (or via local server for Chrome).

### Manual

```bash
git clone https://github.com/macokay/plex-cleanup.git
```

Open `plex-cleanup.html` directly in your browser.

---

## Configuration

On first launch, the Settings modal opens automatically. Enter the required fields:

| Field | Description |
|---|---|
| Plex URL | URL of your Plex server (e.g. `http://192.168.1.10:32400`) |
| Plex Token | Your Plex authentication token (see below) |
| Tautulli URL | Optional — URL of your Tautulli instance |
| Tautulli API key | Optional — found in Tautulli → Settings → Web Interface |
| Radarr URL + API key | Optional — for routing movie deletions through Radarr |
| Sonarr URL + API key | Optional — for routing show deletions through Sonarr |

### Finding your Plex Token

1. Open [app.plex.tv](https://app.plex.tv) and sign in
2. Click any media item → `⋯` menu → **Get Info**
3. Click **View XML** in the bottom-left corner
4. Copy the value of `X-Plex-Token=` from the URL

[Official Plex guide →](https://support.plex.tv/articles/204059436-finding-an-authentication-token-x-plex-token/)

### Enabling Plex to delete files

In Plex: **Settings → Server → Library → enable "Allow media deletion"**

---

## Data

### Sources

| Source | Usage |
|---|---|
| [Plex](https://www.plex.tv) | Library, posters, file sizes, play counts, deletion |
| [Tautulli](https://tautulli.com) | Detailed watch percentage and per-user play history |
| [Radarr](https://radarr.video) | Optional — movie deletion with library cleanup |
| [Sonarr](https://sonarr.tv) | Optional — show deletion with library cleanup |

### Output

Marked titles can be exported as CSV or XLS with columns: Title, Year, Size, Last Watched, Play Count.

---

## Updating

Download the latest release from [GitHub Releases](https://github.com/macokay/plex-cleanup/releases) and replace the existing file.

---

## Known Limitations

- Half-watched filter requires Tautulli — Plex alone does not track watch percentage
- Radarr/Sonarr lookup fetches the full library — may be slow on large collections
- Chrome requires a local web server due to `file://` CORS restrictions

---

## Credits

- [Plex](https://www.plex.tv/) — media server API
- [Tautulli](https://tautulli.com/) — detailed Plex watch statistics
- [Radarr](https://radarr.video/) — movie library management
- [Sonarr](https://sonarr.tv/) — TV show library management

---

## License

&copy; 2026 Mac O Kay. Free to use and modify for personal, non-commercial use. Attribution appreciated if you share or build upon this work. Commercial use is not permitted.
