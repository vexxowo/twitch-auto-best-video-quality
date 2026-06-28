# Twitch - Auto Best Video Quality + vaft

A userscript for Tampermonkey and Violentmonkey that automatically selects the highest available quality on Twitch when you load a page or navigate to a new channel — without fighting your manual quality choices or conflicting with [TwitchAdSolutions (vaft)](https://github.com/ryanbr/TwitchAdSolutions).

---

## What it does

- On page load or channel navigation, automatically opens the quality menu and selects the highest available option (Source, 1440p, 1080p, etc.)
- Does **not** override quality changes you make manually mid-session
- Does **not** conflict with vaft while it is blocking ads

## How it differs from the original script

This is a fork of [Twitch - Auto Best Video Quality](https://greasyfork.org/en/scripts/543926-twitch-auto-best-video-quality) by Martin______X, with two behavioural changes:

### 1. Manual quality changes are respected

The original script monitors `video.videoHeight` and re-applies the highest quality whenever the resolution changes. This means any manual quality change you make (e.g. dropping to 480p on a slow connection) gets immediately overridden.

This fork removes that trigger entirely. Quality is only set automatically on **page load** or **channel navigation**. After that, the player is yours.

### 2. vaft compatibility

The original script's resolution-change trigger is what causes the conflict with vaft. When vaft blocks an ad it briefly serves a lower-quality clean stream, which drops `videoHeight`, which the original script treats as a trigger — repeatedly trying to force quality back up while vaft is in control and causing the quality menu to flicker open and closed.

Since this fork removes that trigger and only acts on URL changes, and vaft never causes a URL change, the two scripts cannot conflict. There is no active vaft detection — compatibility is a passive consequence of the design.

---

## Installation

1. Install [Tampermonkey](https://www.tampermonkey.net/) or [Violentmonkey](https://violentmonkey.github.io/) for your browser
2. Click [here](https://raw.githubusercontent.com/vexxowo/twitch-auto-best-video-quality/main/twitch-auto-best-video-quality.user.js) and confirm the install

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

Original script: [Twitch - Auto Best Video Quality](https://greasyfork.org/en/scripts/543926-twitch-auto-best-video-quality) by [Martin______X](https://greasyfork.org/en/users/1250827-martin-x)

vaft: [TwitchAdSolutions](https://github.com/ryanbr/TwitchAdSolutions) by ryanbr

---

## License

MIT
