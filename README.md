# Relief Desk

An offline-first disaster help app. It runs in any modern phone browser, installs to the home screen like a normal app, and keeps working with no internet.

## Features

- **SOS:** reads your GPS and writes a help message with your coordinates and a map link. Send it by SMS, share it or copy it.
- **Emergency numbers:** one-tap calling for 112, 108, 101, 100, 1078 and 1091 (India).
- **Incident reports:** log problems with your location, mark them resolved, reopen or delete them.
- **Shelters and supply points:** save places, sort them by distance from you, and see them on a simple offline map.
- **Safety guides:** flood, earthquake, cyclone, fire, heatwave and first aid.
- **Emergency kit checklist:** tick off what you have ready.
- **Sync:** export your data as a file and import it on another device. Imports are merged, never overwritten.

## How it works

- Plain HTML, CSS and JavaScript. No frameworks, no build step, no external requests.
- `sw.js` (service worker) caches the app files so it opens with no network.
- `manifest.json` makes the app installable.
- Data is saved in the browser's `localStorage`. Each device holds its own data. Nothing is sent to any server.
- Distances use the Haversine formula. The map is drawn on a `<canvas>` element.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app |
| `sw.js` | Offline caching |
| `manifest.json` | Install settings |
| `icon.svg` | App icon |

## Run it

**Test on your computer**

```bash
python -m http.server 8000
```

Open `http://localhost:8000` in Chrome.

**Host it free with GitHub Pages**

1. Upload all four files to the top level of a public GitHub repository.
2. Go to **Settings**, then **Pages**.
3. Set Source to **Deploy from a branch**, choose **main** and **/ (root)**, then click **Save**.
4. After a minute or two the app is live at `https://YOUR-USERNAME.github.io/REPO-NAME/`.

## Install on a phone

1. Open the live link in Chrome while online and let it load fully once.
2. Open the browser menu and tap **Add to Home Screen** or **Install app**.
3. Turn on airplane mode and open the app to confirm it works offline.

## Updating

After changing any file, change the cache name in `sw.js` (for example `relief-desk-v1` to `relief-desk-v2`) so phones download the new version.

## Limitations

- Data is lost if the browser's site data is cleared. Use **Sync** to back up regularly.
- The map shows distances and positions only, not streets, because street maps need internet.
- SMS sending depends on the phone having mobile signal.
- Emergency numbers are for India. Edit the `NUMS` list in `index.html` for other countries.
- Not a replacement for official emergency services. Always call local authorities first.
