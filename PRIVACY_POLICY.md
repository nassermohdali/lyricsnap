# Privacy Policy for LyricSnap — Lyric Card Maker for YouTube Music

**Last updated:** November 14, 2026

**LyricSnap — Lyric Card Maker for YouTube Music** does not collect user accounts, emails, cookies, YouTube account information, IP-derived location profiles, or general browsing history. You can customize, download, and share lyric cards with optional anonymous usage analytics that you can turn off at any time.

## What Data We Store Locally

1. **Saved Card Preferences (Local Storage):** To remember your visual card preferences across sessions, the extension saves your selected card theme preset and card size (`1:1`, `4:5`, `9:16`, or `16:9`) locally inside your browser.
2. **Temporary Social Share Image (Session Storage):** When you click "Share on X", "Facebook", or "Instagram", the extension temporarily holds your generated lyric card PNG image in browser session memory for up to 3 minutes solely to attach it into the newly opened composer, after which it is cleared.
3. **Anonymous Analytics State (Local Storage):** To power optional anonymous telemetry without identifying you, the extension stores:
   - `analytics_anon_id`: a randomly generated UUID created on first install.
   - `analytics_enabled`: your opt-in/opt-out preference (`true` by default).
   - `analytics_queue` and daily counter keys: an offline event batch queue (capped at 200 events) and a local daily counter (capped at 300 events/day).

## Analytics

When **"Share anonymous usage stats"** is enabled (default ON), the background service worker sends batched, personless usage events (`$process_person_profile: false`) to **PostHog US Cloud** (`https://us.i.posthog.com`) using only your random `analytics_anon_id`.

### Exactly what is collected
- **Install & update lifecycle:** `extension_installed` / `extension_updated` (`version`, `previous_version`).
- **Studio opens:** `studio_opened` (`video_id`, `track_title`, `artist`, `has_lyrics`, `lyrics_line_count`).
- **Card exports & shares:** `lyric_card_exported` (`action`, `video_id`, `track_title`, `artist`, `album`, `theme`, `size`, `selected_line_count`, `selection_mode`, `line_indices`, `original_text`, SHA-256 `snippet_key`, `is_edited`, `edit_type`, `similarity`, `final_char_count`). User-edited/typed text is **not** sent by default.
- **Individual shared lyric lines:** `lyric_line_shared` (up to 8 original lines per non-custom export: `video_id`, `track_title`, `artist`, `line_index`, original `line_text`, SHA-256 `line_key`, `is_edited`, `action`).
- **UI & error telemetry:** `edit_text_opened` (`video_id`), `link_copied` (`video_id`, `had_playlist_params`), and `analytics_error` (`stage`, `error_name`, short URL-stripped `message`), plus `extension_version`, `browser_language`, and `$lib`.

### What is NEVER collected
- No user accounts, emails, or person profiles (`$process_person_profile: false` on every event).
- No YouTube account information, cookies, session tokens, or page URLs beyond the `music.youtube.com` `video_id`.
- No autocapture, pageview tracking, session replay, heatmaps, or third-party ad trackers.

### How to Opt Out
Click the LyricSnap extension icon in Chrome and toggle **"Share anonymous usage stats"** OFF at any time. Turning it off immediately stops all event capture and clears any unsent queued events in local storage.

## Data Retention and Deletion

Locally saved preferences, your random install ID, and any unsent local queue are removed immediately when you uninstall the extension (and the queue is cleared immediately whenever you opt out).

## Changes to This Policy

If our privacy practices ever change, we will update this policy and bump the "Last updated" date above prior to releasing the updated extension version.

## Contact

If you have any questions about this Privacy Policy, please contact:
- **Email:** [nasser.mohd.ali+LS@gmail.com]
