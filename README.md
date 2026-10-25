# LyricSnap — YouTube Music Lyric Card & Share

A Manifest V3 Chrome Extension that lets you select lyrics from YouTube Music inside a dedicated floating studio window (so clicking synced lyrics never seeks or interrupts your playing song), customize high-resolution lyric cards, and share them with a **clean track link** (with `&list=` playlist parameters automatically removed).

## Features

- **Playback-Safe Floating Lyric Selector**:
  - Click the floating **Share Lyrics** button in the bottom-right corner of YouTube Music (or open via the toolbar popup).
  - Extracts synced (`ytmusic-timed-lyrics-line-renderer`) and static lyrics into an isolated floating modal (`<dialog closedby="any">`).
  - Select individual lines, `Shift + Click` to select a range, or edit/paste custom lyrics without ever seeking or pausing the active track.
- **Album Artwork & Theme Presets**:
  - **Blurred Album Art** (high-resolution blurred cover background with adjustable blur & dark contrast sliders)
  - **Album Glow** (adaptive gradient sampled from the track's album cover)
  - **YTM Crimson**, **Midnight**, **Sunset Gold**, **Ocean Neon**, and **Paper Light**
- **Aspect Ratio Presets**:
  - **1:1 Square** (`1080 × 1080`)
  - **9:16 Story** (`1080 × 1920`)
  - **16:9 Wide** (`1920 × 1080`)
- **Clean Track Links (Playlist Stripped)**:
  - Automatically strips `&list=...`, `&index=...`, and tracking parameters to produce a clean `https://music.youtube.com/watch?v=VIDEO_ID` URL.
- **Export & Social Share**:
  - **Download + Link**: Downloads the high-res PNG card and copies the clean track link to your clipboard.
  - **Share on X (Twitter)**: Copies the PNG card image to your clipboard (ready to paste with `Cmd+V` / `Ctrl+V`) and opens the X post composer with the lyric snippet and clean track URL.
  - **Share on Facebook**: Copies the PNG card image to your clipboard and opens the Facebook sharer with the clean track URL.

## How to Load in Chrome (Developer Mode)

1. Open Chrome and navigate to `chrome://extensions`.
2. Enable **Developer mode** in the top-right toggle.
3. Click **Load unpacked** and select `/Users/SURVV/Desktop/ChromeExtension`.
4. Open [YouTube Music](https://music.youtube.com/), play a song, and click **Share Lyrics** in the bottom-right corner!
