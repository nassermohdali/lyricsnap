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

LyricSnap collects optional, anonymous usage analytics to help improve theme presets, share reliability, and lyrics accuracy:

- **Anonymous by design:** Uses only a random per-install UUID (`$process_person_profile: false`) with no user accounts, emails, cookies, or browsing history.
- **No copyrighted lyrics stored:** Tracks feature usage, chosen themes/sizes, share channels, track/artist metadata, selected line indices, and one-way SHA-256 snippet hashes—plaintext song lyrics and user-edited text never leave your browser.
- **Opt-out anytime:** Click the LyricSnap toolbar icon and toggle **"Share anonymous usage stats"** off at any time.

See the full [Privacy Policy](PRIVACY_POLICY.md) for complete details.

## How to Load in Chrome (Developer Mode)

1. Install from Chrome Web Store (https://chromewebstore.google.com/detail/aecjdfonfkkcmiobjclknjejeblhldob) 
2. Open [YouTube Music](https://music.youtube.com/), play a song, and click **Share lyrics** in the bottom-right corner!
