# Sphero Controller PWA

A Progressive Web App to control your Sphero robot with a Bluetooth gamepad, using Web Bluetooth on Android Chrome.

## Requirements

- **Android phone** with Chrome (v56+)
- **Sphero robot** using V2 BLE API: SPRK+, Mini, BOLT, BB-8, BB-9E, R2-D2, R2-Q5, Ollie
- **Bluetooth gamepad** (any standard HID gamepad — PS4, Xbox, 8BitDo, etc.)

> ⚠️ Web Bluetooth is only supported in **Chrome on Android** (and Chrome desktop). It does not work in Firefox, Safari, or most other browsers.

## Setup

### Option A — Serve locally on your network
1. Put all files on a local HTTPS server (e.g. using `npx serve` or `python -m http.server`)
2. Or use a free static host like **GitHub Pages**, **Netlify**, or **Vercel**
3. Open the URL in Chrome on your Android device

### Option B — GitHub Pages (easiest)
1. Create a new GitHub repo
2. Upload all files (`index.html`, `manifest.json`, `sw.js`, `icons/`)
3. Enable GitHub Pages (Settings → Pages → main branch)
4. Open `https://yourusername.github.io/yourrepo/` in Chrome on Android

> The app must be served over **HTTPS** for Web Bluetooth to work. `localhost` also works for testing.

## Pairing devices (do this before opening the app)

1. **Pair your Sphero**: Go to Android Settings → Bluetooth → Pair new device → select your Sphero
2. **Pair your gamepad**: Same Bluetooth settings → pair your controller (put it in pairing mode first)

## Using the app

1. Open the app in Chrome on Android
2. Tap **⬡ Connect Sphero** — a browser picker will appear, select your robot
3. Connect your gamepad (it will auto-detect via the Gamepad API)
4. Drive!

## Controller mappings

| Input | Action |
|-------|--------|
| Left stick | Drive (direction + speed) |
| Right stick | Rotate heading without driving |
| D-pad | Drive at fixed speed in cardinal directions |
| A / Cross | Emergency STOP |
| B / Circle | Reset heading to 0° |
| X / Square | Cycle LED color |
| Y / Triangle (hold) | Full boost |
| RB / R1 | Wake Sphero |

## Supported Sphero models

Models using the **V2 BLE API** (2018+):
- Sphero SPRK+
- Sphero Mini  
- Sphero BOLT / BOLT+
- Sphero BB-8 / BB-9E
- Sphero R2-D2 / R2-Q5
- Sphero Ollie (some firmware versions)

> **Older Sphero 1.0/2.0** use Bluetooth Classic (not BLE) and are **not** compatible with Web Bluetooth.

## Troubleshooting

- **"Web Bluetooth not supported"** → Must use Chrome on Android, not Firefox or Samsung Internet
- **Sphero not appearing in picker** → Make sure Sphero is awake (shake it), and paired in Android Bluetooth settings
- **Connected but not responding** → Try the Wake button; some models need a wake command before accepting drive commands
- **Heading is wrong** → Use the **⊕ Aim** button to reset heading, or adjust the Heading Offset slider
- **Gamepad not detected** → Press any button on the controller after the app is open; gamepads only register after first input
