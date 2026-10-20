# Terminat

**A native macOS terminal and SSH client built for fast local shell access, saved connections, multi-terminal workflows, and Broadcast Input.**

Terminat is a native macOS application for developers, sysadmins, and anyone who works across local shells and SSH sessions. It combines a real local `zsh` terminal, saved SSH connections, flexible multi-terminal layouts, secure macOS Keychain credentials, and keyboard-first controls in a single native interface.

> Current release: **2.0.0**  
> Requires **macOS 26.3 or later**.

## Download

Download the latest signed, notarized build from the **Releases** section of this repository.

Terminat is distributed directly for macOS and is not distributed through the Mac App Store.

## Highlights

### Native local terminal

- Real local `zsh` sessions through a PTY
- Standard terminal behavior including ANSI colors, copy/paste, scrolling, Tab, arrows, Control commands, and interactive CLI tools
- Independent local shell sessions
- Native macOS interface built with SwiftUI/AppKit

### SSH client

- Save SSH connections with name, host, port, username, optional identity file, optional saved password, and optional Keep Alive
- Uses the system `/usr/bin/ssh`
- Supports normal OpenSSH behavior including `~/.ssh/config`, `known_hosts`, SSH agent, keys, ProxyJump / ProxyCommand, and OpenSSH-managed options
- Password, Identity File, and None authentication modes
- Saved passwords are stored in macOS Keychain

### SSH config integration

- Reads aliases from the configured SSH config file
- Default path: `~/.ssh/config`
- SSH config entries remain read-only
- Custom SSH config paths are supported
- SSH config entries can be copied into Terminat's saved connections

### Saved connections and folders

- Create, rename, and delete folders
- Move saved connections between folders
- Drag-and-drop organization
- Search saved connections and SSH config entries
- Search by connection name, host/IP, and username

### Multi-terminal layouts

Terminat supports four workspace modes:

- **Single** — one terminal at a time
- **Columns** — terminals side-by-side
- **Rows** — terminals stacked vertically
- **Grid** — two-column grid with resizable rows and columns

Grid also supports user-controlled horizontal and vertical pane expansion while preserving session order and terminal state.

Switching layouts never restarts terminal sessions.

### Broadcast Input

Broadcast Input can mirror terminal input to multiple selected sessions.

Useful for running the same command across several machines at once.

The selection and broadcast state are visually distinct, and disconnected sessions are excluded from Broadcast targets.

Use Broadcast Input carefully: commands are sent to every selected target.

## Keyboard shortcuts

| Shortcut | Action |
| --- | --- |
| **⌘T** | New Local Shell |
| **⌘W** | Close current terminal session |
| **⌘1…⌘9** | Focus terminal 1…9 |
| **⇧⌘+** | Add current terminal to Broadcast selection |
| **⇧⌘-** | Remove current terminal from Broadcast selection |
| **⇧⌘B** | Toggle Broadcast Input |
| **⌘←** | Previous terminal |
| **⌘→** | Next terminal |
| **⇧⌘L** | Cycle layout |
| **⌘K** | Focus connection search |
| **⇧⌘S** | Toggle sidebar |
| **⌘,** | Settings |
| **⌘Q** | Quit |

Terminal-specific shortcuts such as Control-C, Control-D, Tab, arrows, Escape, and shell/application key combinations continue to go to the active terminal.

## Security

Terminat is designed for local-first terminal and SSH workflows.

Saved SSH passwords are stored in macOS Keychain. They are not stored in connection JSON files, UserDefaults, command-line arguments, or logs.

Saved passwords are delivered to OpenSSH through a local AskPass flow tied to the active SSH process and validated against the running Terminat application.

Release builds are:

- signed with Apple Developer ID
- built with Hardened Runtime
- notarized by Apple
- distributed in signed, notarized DMGs

See [SECURITY.md](SECURITY.md).

## Privacy

Terminat currently has:

- no Terminat cloud account
- no Terminat cloud sync
- no Terminat backend
- no advertising SDK

Local configuration remains on the Mac.

Network access is used for:

- SSH sessions explicitly opened by the user
- Sparkle update checks and downloads
- network activity initiated by commands and applications running inside terminal sessions

See [PRIVACY.md](PRIVACY.md).

## Updates

Terminat uses Sparkle 2 for signed application updates.

You can check manually from **Settings → Updates → Check for Updates…**.

Update metadata is published through this repository's `appcast.xml`.

## Distribution

Terminat is closed-source software.

This public repository is used for:

- release downloads
- Sparkle update metadata
- changelog and documentation
- public release information

The application source code is maintained privately.

## Release integrity

For Terminat 2.0.0:

```text
SHA-256
c08d4e0ed2c3a8db09b1ec274cccfbb97b42549a3dc079a4fcae9663a7a77f8d
```

The distributed DMG is Developer ID signed, Apple notarized, and stapled.
