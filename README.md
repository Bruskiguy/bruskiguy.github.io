# diffdev.io — homepage (user site)

GitHub Pages **user site** repo. Local folder name `diffdev-home`; on GitHub it must be
named `<username>.github.io` and it serves **https://diffdev.io/**.

- `CNAME` contains `diffdev.io` — this claims the custom domain for this GitHub account.
  Every other Pages project repo under the same account is then served under
  `diffdev.io/<repo-name>` (e.g. https://diffdev.io/video-marketing/).
- Deployment: Settings → Pages → Deploy from a branch → `main` → `/ (root)`.

## How to update
Edit `index.html`, commit, push to `main`. GitHub Pages redeploys automatically.
