# zerotap agent

Companion app for [zerotap](https://zerotap.app) that enables AI agent capabilities on Android devices.

> **Security notice:** Only download zerotap agent from the official repository at **[github.com/zerotap-app/agent](https://github.com/zerotap-app/agent)**. Before downloading, check that you are on the correct page — the URL must be exactly `github.com/zerotap-app/agent`. If you see "forked from" at the top of the page, **you are on a copy that may contain a modified APK — leave immediately**. The official link is always available at [zerotap.app](https://zerotap.app).

## Why a separate app?

Google Play policy restricts the use of Accessibility Service APIs. Apps that use these APIs must demonstrate that accessibility is their core function — otherwise they risk removal from the store.

zerotap uses Android Accessibility Service to read screen content and perform actions (taps, swipes, text input) on behalf of the AI agent. To comply with Google Play policy while keeping zerotap available on the Play Store, the accessibility functionality has been moved into this separate companion app.

**The result is a two-app architecture:**

| App | Source | Role |
|-----|--------|------|
| **zerotap** (main app) | [Play Store](https://play.google.com/store/apps/details?id=com.inscode.zerotap) | AI chat, UI |
| **zerotap agent** (this app) | [GitHub Releases](https://github.com/zerotap-app/agent/releases) | Accessibility service, screen reading, device control |

The two apps communicate over a secure local connection using Android AIDL (Android Interface Definition Language). The main app sends commands, the agent executes them on-device.

> **Note:** If you installed zerotap as a direct APK (full version), you don't need this companion app — it has accessibility built in.

## What does zerotap agent do?

The agent app provides an Android Accessibility Service that enables:

- Reading screen content (text and UI elements)
- Performing touch gestures on screen
- Navigation actions (back, home, recent apps)
- Text entry into fields and forms
- Launching applications and services

All processing happens locally on your device. Screen content is read by the agent and passed to the zerotap main app for AI processing. No data is collected, shared, or stored beyond what's needed to execute your command.

## Installation

### 1. Download the APK

Go to [Releases](https://github.com/zerotap-app/agent/releases) and download the latest `zerotap-agent.apk`.

### 2. Install on your device

You'll need to allow installation from unknown sources since this app is not distributed via an app store. On most Android devices:

1. Open the downloaded APK file
2. Android will prompt you to allow installation from this source — tap **Allow**
3. Tap **Install**

### 3. Enable the Accessibility Service

1. Open the **zerotap agent** app
2. Tap **Enable Accessibility Service**
3. In Android Settings, find **zerotap agent** and toggle it on
4. Confirm the permission dialog

### 4. Open zerotap

That's it. The main zerotap app will automatically detect and connect to the agent. You can verify the connection status in zerotap's settings.

## Requirements

- Android 8.0 (Oreo) or higher
- [zerotap](https://play.google.com/store/apps/details?id=com.inscode.zerotap) main app installed

## FAQ

**Do I need this app?**
Only if you installed zerotap from the Google Play Store. The Play Store version requires this companion app for device control features. If you installed zerotap as a direct APK (full version), accessibility is already built in.

**Is it safe to install APKs from GitHub?**
Yes, as long as you download from the [official releases page](https://github.com/zerotap-app/agent/releases). Always verify you're on the official repo — not a fork.

**Why isn't this on the Play Store?**
Because its sole purpose is providing an Accessibility Service for another app, it doesn't meet Play Store listing requirements as a standalone product.

**Does it run in the background?**
The Accessibility Service runs as a background service, which is required for it to respond to commands from the main app. It only performs actions when instructed by zerotap and has minimal impact on battery life.

**What data does it access?**
The agent reads screen content only when the zerotap main app sends a command. Screen data is processed in real-time and never stored. No data is sent to external servers by the agent app itself.

## Links

- [zerotap website](https://zerotap.app)
- [zerotap on Google Play](https://play.google.com/store/apps/details?id=com.inscode.zerotap)
- [MCP Server setup](https://github.com/zerotap-app/android-mcp-server)
- [Discord](https://discord.gg/XyMpNdF2Va)
