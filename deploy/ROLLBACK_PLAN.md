# Rollback Plan (Midland Montessori)

## Strategy
We keep timestamped releases so rollback is a fast pointer switch (or re-upload previous artifact).

## Before each deploy
1. Pull fresh backup of production into `backups/<timestamp>/live/`
2. Create new release in `deploy/releases/<timestamp>/site`
3. Generate artifact `deploy/artifacts/site-<timestamp>.tar.gz`
4. Record release timestamp in changelog

## Rollback options

### A) If server supports release symlink switching (best)
- Point server docroot/current symlink back to previous release.
- Verify homepage + form + PDF.

### B) If deploying by upload (cPanel/SFTP)
- Upload previous known-good artifact from `deploy/artifacts/`.
- Replace live `index.html`, `robots.txt`, and `TiffinBayWaitingList.pdf`.
- Purge Cloudflare cache if needed.

## Smoke test checklist (post-deploy or rollback)
- `https://midland-montessori.ca/` returns 200
- Interest form submits (Formspree endpoint intact)
- PDF download works
- Email links use `mailto:` correctly
- No obvious layout regressions on mobile width
