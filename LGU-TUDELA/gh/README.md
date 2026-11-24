# Tudela LGU Portal (GitHub-based)

Static site + GitHub as the database. No server needed.

## Deploy
1. Create a **public** GitHub repo and upload everything in this folder (index.html, data/, uploads/).
2. Repo Settings > Pages > Deploy from branch `main` (root).
3. Open `https://<owner>.github.io/<repo>/`. The repo is auto-detected.
   (Custom domain or other host? Set `CFG.owner`/`CFG.repo` near the bottom of index.html.)

## Admin (post bulletins, upload/delete images, video, audio)
1. GitHub > Settings > Developer settings > Fine-grained tokens > Generate.
2. Repository access: only this repo. Permission: **Contents: Read and write**.
3. On the site tap **Admin**, paste the token. It is kept only in your browser (localStorage).

## How it works
- `data/bulletins.json` and `data/media.json` hold the records; files go to `uploads/`.
- Each post/upload is a commit via the GitHub Contents API.
- Visitors poll every 20 s (conditional requests, so no rate-limit cost when unchanged).
- Keep each file under ~25 MB. Anyone can read a public repo, so upload only public material.
- Never share your token or put it in index.html.
