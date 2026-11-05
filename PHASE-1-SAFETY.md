# Phase 1 — Safety and baseline

## Current production baseline
- Default branch: `main`
- Existing app entry point: `index.html`
- Existing browser storage key: `anirudhOS_v2`
- Existing data collections: `business`, `study`, `fitness`, `payouts`
- Existing backup/restore: JSON export/import in the Backup section.

## Safety snapshot
The original `index.html` from `main` is preserved at:
`backups/index-before-upgrade.html`

This snapshot is committed on the isolated branch `phase-1-safety-backup`. Production `main` and the live GitHub Pages app have not been changed.

## Important user-side action
The repository snapshot preserves the source code only. It does not contain data stored privately in the user's phone/browser. Before any app migration or storage changes, the user must open the current app and use **Backup → Download JSON Backup**, then keep that file safely on their device.

## Phase 1 verification findings
- The current app is a single-page HTML/CSS/JavaScript app.
- It stores records in browser `localStorage` under `anirudhOS_v2`.
- The current app has Business, SSC, Fitness, and Backup sections plus the Home dashboard.
- Future development must preserve the existing storage key and collection fields, or perform an explicit backward-compatible migration.
- Do not replace the production entry point until the backup is verified and the new version is tested.

## Next implementation gate
1. User downloads the in-app JSON backup.
2. Confirm the file is saved.
3. Build new modules on this branch, not directly on `main`.
4. Test old-data loading and backup restoration before merging/deploying.
