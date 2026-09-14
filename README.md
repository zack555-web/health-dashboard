# Personal Dashboard

## Structure

- `/index.html`: Personal Dashboard entry point; Main Dashboard will be added here.
- `/personal/health/`: existing Health Dashboard.
- `/personal/english/`: planned English Dashboard.
- `/personal/food/`: possible future Food Dashboard.
- `/test/`: web experiments.
- `/data/health-data.json`: canonical Health data.
- `/health-data.json`: frozen migration snapshot for old read links; do not update this file. It is not synchronized.

## URLs

Site: https://zack555-web.github.io/health-dashboard/

Health: https://zack555-web.github.io/health-dashboard/personal/health/

Data: https://zack555-web.github.io/health-dashboard/data/health-data.json

The repository name and Pages base URL are unchanged. Paths above are relative to the repository root, not the github.io domain root. The old site URL remains the entry point with a Health link.

## Shortcut setup

The owner confirmed that the Shortcut is not yet in operation. Configure all future reads and writes to `data/health-data.json`. For the GitHub Contents API, use:

`https://api.github.com/repos/zack555-web/health-dashboard/contents/data/health-data.json`

Read with `?ref=main`. For a PUT, use `branch: main`, the current SHA returned by GET for this exact path, and Base64-encoded JSON in `content`. Never reuse the SHA of the old root file. Keep credentials in the Shortcut, never in this repository. An iPhone run is still required to verify the eventual Shortcut.

## Migration and recovery (2026-09-14)

Original commit: `c81089dfc17a065a4c0f95f63836ac271e42d8c1`.

Backup branch: `codex/backup-before-personal-20260914`.

The JSON is copied byte-for-byte without changing its schema or values. Health now fetches `../../data/health-data.json`; its display and fixed sample values are preserved. The root JSON remains only as a compatibility snapshot. Once any old consumers are retired, it can be removed.

To undo the layout migration, revert the migration merge commit. Preserve and back up any data updates made after migration first. Do not reset the whole repository to the backup branch, which would discard later data. To restore the original UI only, copy `index.html` from the backup branch and point its fetch to `data/health-data.json` so that it continues to read current data.
