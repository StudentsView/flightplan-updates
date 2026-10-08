# FlightPlan update policy

Only public update metadata is stored here. App source and account data are not included.

Edit `version.json` on `main`:

- `minimumVersion`: versions below this value cannot enter the app.
- `minimumBuild`: blocks lower builds of the minimum version. Higher versions are allowed.
- `latestVersion`: latest published version, at least `minimumVersion`.
- `updateURL`: HTTPS update page; replace with the App Store URL when published.
- `message`: concise text shown on the mandatory update screen.

Example: to require 0.2.0 build 3, set minimumVersion to 0.2.0, minimumBuild to 3, and latestVersion to 0.2.0 or newer.

The app checks on launch and foreground (at most once per minute). It caches valid metadata. If the server is unavailable, a previously confirmed mandatory update remains mandatory; first-run network failure permits entry. Lowering the minimum unblocks clients after their next successful check. This is a client gate, not server-side authorization.

Current development build: 0.1.0 (1). The initial policy permits it.
