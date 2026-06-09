# Twitch - Auto Best Video Quality + vaft

A userscript for Tampermonkey and Violentmonkey that automatically selects the highest available quality on Twitch when you load a page or navigate to a new channel — without fighting your manual quality choices or conflicting with [TwitchAdSolutions (vaft)](https://github.com/ryanbr/TwitchAdSolutions).

---

## What it does

- On page load or channel navigation, automatically opens the quality menu and selects the highest available option (Source, 1440p, 1080p, etc.)
- Does **not** override quality changes you make manually mid-session
- Does **not** interfere with vaft while it is blocking ads

## How it differs from the original script

This is a fork of [Twitch - Auto Best Video Quality](https://greasyfork.org/en/scripts/543926-twitch-auto-best-video-quality) by Martin______X, with two behavioural changes:

### 1. Manual quality changes are respected

The original script monitors `video.videoHeight` and re-applies the highest quality whenever the resolution changes. This means any manual quality change you make (e.g. dropping to 480p on a slow connection) gets immediately overridden.

This fork removes that trigger. Quality is only set automatically on **page load** or **channel navigation**. After that, the player is yours.

### 2. vaft compatibility

When vaft blocks a Twitch ad, it intercepts the stream and briefly serves a lower-quality clean stream. The original script detects this as a resolution change and enters a loop — repeatedly trying to force highest quality while vaft is in control, causing the quality menu to flicker open and closed.

This fork detects when vaft is active by reading the `.adblock-overlay` element vaft maintains on `.video-player`. While vaft is blocking:

- Any in-progress quality-switch cycle is aborted
- No new quality-switch attempts are started

When vaft finishes, behaviour depends on whether quality was already set for the current channel:

- **Quality was never set** (e.g. vaft caught a pre-roll immediately after you navigated to a channel): one quality-set pass runs after the ad clears
- **Quality was already set** (e.g. you changed quality manually and then an ad played): nothing happens, your choice is kept

---

## Installation

1. Install [Tampermonkey](https://www.tampermonkey.net/) or [Violentmonkey](https://violentmonkey.github.io/) for your browser
2. Click [here](https://github.com/vexxowo/twitch-auto-best-video-quality/raw/refs/heads/main/twitch-auto-best-video-quality.user.js) and confirm the install

### Running alongside TwitchAdSolutions

This script is designed to run alongside [vaft](https://github.com/ryanbr/TwitchAdSolutions). Install both and they will not conflict.

---

## Compatibility

| Browser extension | Supported |
|---|---|
| Tampermonkey | ✓ |
| Violentmonkey | ✓ |

| Ad blocker script | Supported |
|---|---|
| vaft (TwitchAdSolutions) | ✓ |

---

## Credits

Original script: [Twitch - Auto Best Video Quality](https://greasyfork.org/en/scripts/543926-twitch-auto-best-video-quality) by [Martin______X](https://greasyfork.org/en/users/1370399)

vaft: [TwitchAdSolutions](https://github.com/ryanbr/TwitchAdSolutions) by ryanbr

---

## License

MIT
