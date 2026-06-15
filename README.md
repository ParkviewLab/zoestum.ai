# zoestum.ai

The Zoestum website — a plain static site (no framework) served by **GitHub Pages**
at [zoestum.ai](https://zoestum.ai). It follows the ParkviewLab
[website-repo conventions](https://github.com/ParkviewLab/handbook/blob/main/docs/website.md).
Currently a single coming-soon page.

## Layout

```
index.html                ← the page (coming-soon; styles are inline)
assets/
  fonts/michroma-latin.woff2   ← self-hosted Michroma (OFL-1.1)
  img/zoestum_logo.svg         ← Zoestum logo (brand mark, all rights reserved)
CNAME                     ← custom domain
scripts/
  preview.sh              ← local preview: stamp the date + serve on localhost
  stamp.py               ← stamps the page's "updated on" date from git
.github/workflows/        ← reuse.yml (lint) + pages-deploy.yml (stamp + deploy)
```

## Branches & publishing

- **`live`** — production; GitHub Pages serves this branch via the Actions deploy.
- **`staging`** — integration (the default branch); work happens here.

Edit on `staging`, preview locally, then **publish by promoting `staging` → `live`**:

```bash
scripts/preview.sh                            # stamp + serve at http://localhost:8000
# when it looks right, from the live worktree:
git merge --ff-only staging && git push       # push to live → deploys
```

There are no version bumps, tags, or releases — the deploy stamps each page's
"updated on" date from git and publishes.

## License

Standard copyright — © 2026 Gary Frattarola, all rights reserved (not open source).
The bundled Michroma font is third-party under `OFL-1.1`. See [`LICENSING.md`](LICENSING.md).
