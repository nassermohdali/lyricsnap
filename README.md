# LyricSnap — Lyric Card Maker for YouTube Music

A Manifest V3 Chrome Extension that lets you select lyrics from YouTube Music inside a dedicated floating studio window (so clicking synced lyrics never seeks or interrupts your playing song), customize high-resolution lyric cards, and share them with a **clean track link** (with `&list=` playlist parameters automatically removed).

## Features

- **Playback-Safe Floating Lyric Selector**:
  - Click the floating **Share lyrics** pill in the bottom-right corner of YouTube Music (or open via the toolbar popup).
  - Extracts synced (`ytmusic-timed-lyrics-line-renderer`) and static lyrics into an isolated floating modal (`<dialog closedby="any">`).
  - Select individual lines, `Shift + Click` to select a range, or edit/paste custom lyrics via **Edit text** without ever seeking or pausing the active track.
- **10 Built-in Theme Presets**:
  - **Frosted Cover**, **Mesh Aura**, **Neo-Brutalist**, **Cyber CRT**, **Minimal Quote**, **Polaroid**, **Receipt**, **Vinyl Sleeve**, **Concert Ticket**, and **Retro Y2K CD**.
- **4 Social Aspect Ratio Presets**:
  - **1:1 Square** (`1080 × 1080`)
  - **4:5 IG Post** (`1080 × 1350`)
  - **9:16 Story** (`1080 × 1920`)
  - **16:9 Wide** (`1920 × 1080`)
- **Clean Track Links (Playlist Stripped)**:
  - Automatically strips `&list=...`, `&index=...`, and tracking parameters to produce a clean `https://music.youtube.com/watch?v=VIDEO_ID` URL.
- **Export & Social Share**:
  - **Copy image**: Copies the rendered PNG card straight to your clipboard.
  - **Download**: Saves the high-res PNG card and copies the clean track link.
  - **Share on X**, **Facebook**, and **Instagram**: Automatically opens the composer, attaches the lyric card image, and fills a clean caption with artist hashtags.

## Analytics

LyricSnap includes lightweight, privacy-friendly product analytics powered by PostHog US Cloud (free-tier optimized, personless mode `$process_person_profile: false`), routed exclusively through the background service worker (`background/service-worker.js`).

- **What is collected (when enabled):**
  - Random per-install UUID (`analytics_anon_id` stored in `chrome.storage.local`, never linked to a person profile).
  - Extension lifecycle (`extension_installed`, `extension_updated`).
  - Studio usage (`studio_opened` with `video_id`, `track_title`, `artist`, `has_lyrics`, `lyrics_line_count`).
  - Card exports & shared lines (`lyric_card_exported` and up to 8 `lyric_line_shared` events per non-custom export with theme, size, selection mode, SHA-256 snippet/line keys, similarity ratio, and `edit_type`; user-edited text is **not** sent by default).
  - UI & error metrics (`edit_text_opened`, `link_copied` with `had_playlist_params`, `analytics_error` with URL-stripped messages), plus `extension_version`, `browser_language`, and `$lib`.
- **Volume & Privacy Guardrails:**
  - Batched in the service worker (every 30s or 20 events), max 200 queued events in `chrome.storage.local`, max 300 events per user per day.
  - No autocapture, no pageviews, no session replay, no cookies, no emails, and no browsing history URLs.
  - Toggleable anytime via **"Share anonymous usage stats"** in the toolbar popup (disabling clears the queue immediately).

## Development & Packaging

1. Set your PostHog project API key in `src/analytics/config.ts` (`POSTHOG_API_KEY`).
2. Build `shared/analytics.js` from `src/analytics/`:
   ```bash
   node scripts/build.mjs
   ```
3. Run unit & integration tests:
   ```bash
   node tests/analytics.test.mjs
   ```
4. Package a clean Chrome Web Store `.zip`:
   ```bash
   ./package-extension.sh
   ```

## How to Load in Chrome (Developer Mode)

1. Run `node scripts/build.mjs`.
2. Open Chrome and navigate to `chrome://extensions`.
3. Enable **Developer mode** in the top-right toggle.
4. Click **Load unpacked** and select `/Users/SURVV/Desktop/ChromeExtension`.
5. Open [YouTube Music](https://music.youtube.com/), play a song, and click **Share lyrics** in the bottom-right corner!
