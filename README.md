# Twitch - Auto Best Video Quality (VAFT Compatible & Manual Control)

A modified userscript that automatically forces Twitch streams to their highest available video resolution, optimized to work harmoniously with modern ad-blocking solutions and user overrides.

## 🚀 Key Improvements in this Fork

* **VAFT Compatibility:** Fully compatible with [TwitchAdSolutions' VAFT script](https://github.com/ryanbr/TwitchAdSolutions). It prevents the quality-locking issues or player crashes that occur when both scripts try to manipulate the Twitch web player simultaneously.
* **Manual Overrides Allowed:** While the script defaults to forcing the absolute best video quality on page load or stream switch, it no longer permanently locks the player UI. If you need to manually drop the resolution down to save bandwidth, the script will respect your choice until the stream refreshes or changes.

## 📦 Installation

1. Ensure you have a userscript manager installed in your browser (e.g., [Tampermonkey](https://www.tampermonkey.net/) or [Violentmonkey](https://violentmonkey.github.io/)).
2. Click the link below to install the script directly from the source:
   * **[Install directly from GitHub](https://raw.githubusercontent.com/vexxowo/twitch-auto-best-video-quality/refs/heads/main/twitch-auto-best-video-quality.user.js)**
3. Confirm Installation:
   - Your browser extension will open a new tab. Click **Install** to finish.

## ⚙️ How it Works

The script monitors the internal Twitch player state and automatically triggers a quality change event to the maximum available source resolution upon player initialization. If an advertisement script (like VAFT) alters the player stream topology to bypass an ad, this fork gracefully steps aside to ensure your stream playback is uninterrupted, resuming its optimization once the normal stream structure returns.

## 📄 License & Attribution

This project is a fork of the original Greasy Fork script [Twitch - Auto Best Video Quality](https://greasyfork.org/scripts/543926). 

This script is distributed under the **MIT License**. You are free to modify, distribute, and use it as you see fit, provided the original copyright notices are preserved.
