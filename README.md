# Trio

A minimal mobile-first web app for drone operators, with six tabs:

- **Timers** — create and manage multiple recurring reminders
- **Calc** — calculator with history
- **Tasks** — task list with groups, priorities, and drag-to-reorder
- **Notes** — flight observations with heading and description
- **Vehicles** — registry of aircraft (MAVLink ID, board number, SineLink name, video frequency, marshal timer, altitude)
- **Altitude** — mission altitude calculator

All data lives in your browser's `localStorage` — no accounts, no server, no analytics. Light and dark themes, follows system by default. Single-file app: just `index.html`, no build step, no dependencies.

## Host on GitHub Pages

1. Create a new public repository on GitHub (e.g. `trio`).
2. Upload `index.html` to the repository root.
3. In the repo, go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to `Deploy from a branch`, choose `main` (or `master`) and `/ (root)`, then **Save**.
5. After a minute, your app is live at `https://<your-username>.github.io/<repo>/`.

Open the URL on your phone, then **Add to Home Screen** from your browser's share menu — it launches full-screen like a native app.

## Run locally

Just open `index.html` in any modern browser. No server needed.

## Tabs

**Timers.** Each timer is a card with a label, an interval, and a play/pause button. Tap + to add one, tap a card body to edit (rename, change interval, delete), tap the round button to start or stop. Timers run independently — you can have several firing at once. Global notification toggles (sound, vibration, system notifications) sit at the bottom of the tab and apply to all timers.

**Calc.** Standard arithmetic with a live result as you type. History keeps the last 50 entries; tap one to load it back into the display. Hardware keyboard works (digits, operators, Enter to evaluate, Backspace, Esc to clear).

**Tasks.** Switch between groups via the chips at the top, or tap **Groups** to add/rename/delete them. Default groups are **Pre-flight**, **After-flight**, **Future Work**, and **To Reflect On**. Tasks have a name, description, and one of four priority levels (high / medium / low / none) shown as a colored dot. Use the handle on the right of each task to drag and reorder. Tap a task body to edit, tap the circle to mark done.

**Notes.** Free-form notes with a heading and a longer description. Sorted newest-first. Tap + to add, tap any note to edit or delete.

**Vehicles.** A registry of aircraft. Each entry stores:
- SineLink name (display name)
- MAVLink ID
- Board number
- Video frequency
- Marshal timer (seconds, optional)
- Altitude (meters, optional)

All fields are editable at any time — tap a vehicle to open the edit sheet.

**Altitude.** Mission altitude calculator. Enter your current telemetry altitude (AMSL) and your target altitude (MSL); the result — `Target MSL + Telemetry AMSL` — is shown live in meters. Inputs persist between sessions.

## Export & import

Tap the gear icon in the header to open the **Data** sheet.

- **Export JSON** downloads a single `trio-backup-<timestamp>.json` file containing all your timers, tasks, groups, notes, vehicles, calculator history, and timer notification settings.
- **Import JSON** opens a file picker; the backup replaces your current data after confirmation. Running timers are stopped automatically before import.

The backup file is plain JSON — you can edit it by hand if you ever need to, or commit it to a private repo to sync between devices.

## Browser support

Works in any recent Chromium, Safari, or Firefox. Some niceties (Wake Lock, vibration, system notifications) are best-effort and depend on platform support.
