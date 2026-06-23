# Add Video Playback to the NBA Draft Website

This package adds:

- MP4/WebM uploads on the Commissioner page
- A video library with **Preview**, **Play on Big Screen**, and **Delete**
- A **Stop Video and Return to Draft** button
- Automatic return to the draft screen when a video ends
- An option to pause the draft clock before starting a video
- A browser-only demo mode that works between tabs on the same browser

## Files included

- `commissioner.html` — replacement file
- `display.html` — replacement file
- `video-feature.js` — new file
- `video-feature.css` — new file
- `video-setup.sql` — Supabase add-on migration

## Install

1. Back up the current GitHub repository.
2. Upload these four website files to the repository root:
   - `commissioner.html`
   - `display.html`
   - `video-feature.js`
   - `video-feature.css`
3. Replace the existing `commissioner.html` and `display.html` when GitHub asks.
4. For live syncing across phones/computers:
   - Run the existing `setup.sql` first if it has not already been run.
   - Open Supabase → SQL Editor.
   - Paste and run `video-setup.sql`.
5. Keep the existing `config.js`, `common.js`, `commissioner.js`, `display.js`, and other files unchanged.
6. Refresh the GitHub Pages website.

## Test

1. Open `display.html` in one tab and log in.
2. Open `commissioner.html` in another tab and log in.
3. Go to Step 4: Draft.
4. Upload a small MP4.
5. Press **Play on Big Screen**.
6. The display tab should switch to the video and return to the draft when it ends.

## Important notes

- MP4 is the safest format for TVs and browsers.
- Maximum file size in this package is 100 MB.
- Some browsers block automatic sound. If that happens, the display starts muted and shows a **Turn On Sound** button.
- In demo mode, videos are stored only in that browser using IndexedDB.
- In live mode, videos are stored in the public Supabase Storage bucket named `draft-videos`.
- The simple browser upload policy permits anyone who has your public Supabase project credentials to upload/delete objects in this bucket. For a private family or league event this may be acceptable. A hardened public production site should move uploads behind a server or Supabase Edge Function.
- If you rerun the original destructive `setup.sql`, rerun `video-setup.sql` afterward.
