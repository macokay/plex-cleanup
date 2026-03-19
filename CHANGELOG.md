# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [1.1.0] - 2026-03-19

### Added
- Tautulli is now optional — tool works with Plex alone
  - Plex `viewCount` and `lastViewedAt` used as baseline data source
  - Tautulli enriches with `watchedPct` and more accurate play counts when configured
  - Half-watched filter only requires Tautulli; all other filters work on Plex data alone
  - Recommended to use both, but not required
- Delete titles directly via Plex API, Radarr, or Sonarr
  - Deletion method chosen in Settings: Plex only, or Arr apps
  - Radarr and Sonarr can each be enabled independently
  - Matching via TMDB/IMDB/TVDB IDs with automatic title+year fallback
  - If arr app does not find a title, deletion falls back to Plex API automatically
  - Confirmation dialog shows which service handles each deletion
- Settings modal with save to localStorage — auto-connects on next visit
- Per-row delete button (hover to reveal) and "Delete marked" button in nav bar
- Error toast with human-readable message and contextual hints on delete failure
- Test connection buttons for Plex, Tautulli, Radarr and Sonarr — inline in Settings
- Show/hide eye button on all password and token fields
- In-app debug panel (Debug button in status bar) — no browser devtools needed
- GB → TB auto-formatting in header stats
- Large file flag always shown when threshold is met regardless of play count

### Fixed
- Show disk usage now correctly aggregated from episode-level Plex data
- Show play counts now correctly aggregated via Tautulli `grandparent_rating_key`
- Radarr/Sonarr API calls now use `X-Api-Key` header instead of query parameter
- Radarr/Sonarr lookup now fetches full library once and filters locally — fixes 400 Bad Request
- HTML tags stripped from API error messages shown in toast
- Plex deletion tip corrected to Settings → Server → Library
- All native emoji replaced with clean monoline SVG icons

---

## [1.0.0] - 2026-03-19

### Added
- Initial release
- Library view with movies and TV shows from Plex API
- Play history via Tautulli API
- Filters: Never watched, Added never started, Half-watched, Collecting dust, Large file
- Poster images served directly from Plex server
- Charts: Movies vs Shows, Disk usage by type, Top genres, Languages
- Export marked titles as CSV or XLS
- Password fields with show/hide toggle
