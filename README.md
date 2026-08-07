# Land Records — update channel

Public update channel for the **Land Records** Android app. No source code, no personal data —
just the in-app updater's manifest and the slim update APKs.

The app reads [`update.json`](./update.json) on demand (Settings → *Check for updates*):

```json
{ "versionCode": 6, "versionName": "0.6.0",
  "apkUrl": ".../releases/latest/download/land-records.apk", "notes": "..." }
```

If `versionCode` is higher than what's installed, the app downloads `apkUrl` and hands it to the
system installer (the user taps **Install** once — app data is preserved).

## Publishing an update
1. Build a **slim** (seed-free) APK: `versionCode` bumped, `assets/seed/` absent.
2. `gh release create vX.Y.Z land-records.apk` (asset named exactly `land-records.apk`).
3. Bump `versionCode`/`versionName`/`notes` in `update.json` and push.
