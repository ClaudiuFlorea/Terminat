<h1 align="center">Terminat</h1>

<p align="center">
  <strong>A native macOS terminal and SSH client for fast local shells, saved connections, flexible multi-terminal layouts, and Broadcast Input.</strong>
</p>

<p align="center">
  <a href="https://github.com/ClaudiuFlorea/Terminat/releases/latest"><strong>Download Terminat 2.0.0</strong></a>
  · macOS 26.3+
  · Developer ID signed & Apple notarized
</p>

## Why Terminat

Terminat is built for people who live in terminals but want the speed and polish of a native macOS app. It combines real local `zsh` sessions, saved SSH connections, system OpenSSH, secure Keychain credentials, flexible pane layouts, and multi-session Broadcast Input in one keyboard-first workspace.

There is no Terminat account, cloud backend, advertising SDK, or browser-based terminal layer.

## Workspace

## Workspace

Terminat supports **Single**, **Columns**, **Rows**, and **Grid** layouts without restarting sessions. Grid supports resizable rows and columns, horizontal/vertical pane expansion, persistent session order, and sidebar-free focused workflows.

## Broadcast Input

Select multiple terminal panes and send the same raw terminal input to all selected targets.

Useful for repeating commands across several machines or sessions without copy/paste loops.

- visually distinct selected and active Broadcast states
- disconnected sessions are excluded automatically
- input is forwarded at terminal-input level
- normal text, Enter, Backspace, Tab, arrows, Escape, and supported control sequences are preserved

The keyboard workflow is intentionally explicit:

| Shortcut | Action |
| --- | --- |
| **⌘1…⌘9** | Focus terminal 1…9 |
| **⇧⌘+** | Add current terminal to Broadcast selection |
| **⇧⌘-** | Remove current terminal from Broadcast selection |
| **⇧⌘B** | Toggle Broadcast Input |

## SSH without replacing OpenSSH

Terminat uses macOS' system `/usr/bin/ssh` rather than implementing its own SSH stack.

That means your normal OpenSSH environment continues to work, including:

- `~/.ssh/config`
- `known_hosts`
- SSH agent
- identity files
- ProxyJump / ProxyCommand
- custom OpenSSH options handled by your SSH configuration

Saved connections support:

- name, host, port, and username
- Password, Identity File, or None authentication modes
- optional SSH Keep Alive
- paste/import of a normal `ssh user@host ...` command
- folders and drag-and-drop organization
- search across saved connections and SSH-config entries

SSH config entries are read-only in Terminat and can be copied into Saved Connections when you want to manage them inside the app.

## Secure credentials

Saved SSH passwords are stored in **macOS Keychain**.

They are not stored in:

- connection JSON files
- UserDefaults
- command-line arguments
- logs

Terminat's AskPass flow uses a private local Unix-domain socket and validates the requesting process before the main app reads a password from Keychain.

See [SECURITY.md](SECURITY.md) for implementation details.

## Native appearance

Terminat is a native SwiftUI/AppKit macOS application with light/dark application themes, terminal themes, installed monospace font selection, live font sizing, and native Settings.

## Local terminal

- real local `zsh` sessions through a PTY
- independent terminal sessions
- ANSI colors and interactive CLI applications
- standard copy/paste and scrolling
- Control commands, Tab, arrows, Escape, and shell key combinations
- terminal title and size/status metadata

## Keyboard shortcuts

| Shortcut | Action |
| --- | --- |
| **⌘T** | New Local Shell |
| **⌘W** | Close current terminal session |
| **⌘1…⌘9** | Focus terminal 1…9 |
| **⌘←** | Previous terminal |
| **⌘→** | Next terminal |
| **⇧⌘+** | Add current terminal to Broadcast selection |
| **⇧⌘-** | Remove current terminal from Broadcast selection |
| **⇧⌘B** | Toggle Broadcast Input |
| **⇧⌘L** | Cycle layout |
| **⌘K** | Focus connection search |
| **⇧⌘S** | Toggle sidebar |
| **⌘,** | Settings |
| **⌘Q** | Quit |

## Download

Download the latest signed and notarized DMG from:

**[GitHub Releases](https://github.com/ClaudiuFlorea/Terminat/releases/latest)**

Current release: **2.0.0**

Requires **macOS 26.3 or later**.

Terminat is distributed directly for macOS and is not distributed through the Mac App Store.

## Updates

Terminat uses Sparkle 2 for signed application updates.

Existing GATE22 1.x installations can update directly to Terminat 2.0.0 through the legacy GATE22 feed. After that migration, Terminat uses this repository's update feed for future releases.

Updates are protected by Sparkle EdDSA signatures in addition to Apple Developer ID signing and notarization.

## Privacy

Terminat is local-first.

It currently has:

- no Terminat user account
- no Terminat cloud sync
- no Terminat backend
- no advertising SDK

Network access is used for SSH sessions explicitly opened by the user, Sparkle update checks/downloads, and network activity initiated by commands running inside terminal sessions.

See [PRIVACY.md](PRIVACY.md).

## Release integrity

**Terminat 2.0.0**

```text
SHA-256
c08d4e0ed2c3a8db09b1ec274cccfbb97b42549a3dc079a4fcae9663a7a77f8d
```

The release DMG is:

- Developer ID signed
- built with Hardened Runtime
- Apple notarized
- stapled for offline Gatekeeper verification

## Public repository

Terminat is closed-source software.

This repository contains:

- release downloads
- Sparkle update metadata
- changelog
- security documentation
- privacy documentation
- product screenshots

The application source code is maintained privately.

See [CHANGELOG.md](CHANGELOG.md) for release history.
