# HUNTER FPV — Scroll-Scrubbed Portfolio Site

A scroll-scrubbed FPV drone operator portfolio: a 3D drone flies in, turns, you
enter it from behind, and the scroll drives a continuous FPV journey through
four extreme-sports scenes (skate / moto / surf / rally).

## Files

| File | Purpose |
|---|---|
| `index.html` | The site. Loads all content from `content.json` at runtime. |
| `admin.html` | The CMS. Edit every piece of site content in friendly forms. |
| `content.json` | All site content: names, sections, work list, rigs, video URLs. |
| `video/` | Put your MP4 scene files here for permanent self-hosted video. |

## Deploy on GitHub Pages

1. Create a new GitHub repo and upload this whole folder (keep the structure).
2. Repo → **Settings → Pages** → Source: **Deploy from a branch** → Branch: `main`, folder `/ (root)` → Save.
3. Your site goes live at `https://<username>.github.io/<repo>/` in a minute or two.

## Editing content (the CMS workflow)

1. Open `admin.html` — locally, or at `https://<username>.github.io/<repo>/admin.html`.
2. It loads the current `content.json`. Edit anything: pilot name, roles, reel
   cards, work list, equipment, contact info, video URLs. Add/remove rows freely.
3. Click **DOWNLOAD CONTENT.JSON**.
4. Replace `content.json` in the repo with the downloaded file, commit, push.
   The live site reflects it on the next page load. (No rebuild needed.)

Tip: on the GitHub website you can just drag the new `content.json` onto the
repo page to replace it — no git commands required.

## Videos (do this once)

The included video URLs are temporary Runway links that expire after ~a day.
To make the site permanent:

1. Download the four MP4s.
2. Re-encode each for smooth scrubbing (every frame becomes a keyframe):
   ```
   ffmpeg -i in.mp4 -c:v libx264 -g 1 -crf 20 -pix_fmt yuv420p -movflags +faststart out.mp4
   ```
3. Put them in `video/` as `skate.mp4`, `moto.mp4`, `surf.mp4`, `rally.mp4`.
4. In `admin.html`, set each scene's path to `video/skate.mp4` etc., download
   the new `content.json`, and push everything.

GitHub's file limit is 100 MB per file — these clips are well under that.

## Notes

- The site works opened straight from disk (it falls back to content embedded
  in `index.html` if `content.json` can't be fetched), but always test the
  deployed version — that's where `content.json` edits show up.
- Scroll scrubbing is smoothest in Chrome/Edge. The `-g 1` re-encode makes a
  dramatic difference — don't skip it.
