# Changelog

All notable public Terminat releases are documented here.

## 2.0.0

Initial public release under the Terminat name.

### Changed

- Rebranded the application from GATE22 to Terminat
- Added the Terminat visual identity and app icon
- Refined the native macOS interface and workspace behavior
- Added flexible Grid pane spans and resizable Grid tracks
- Improved multi-terminal selection and Broadcast Input workflows
- Added keyboard-first terminal navigation and Broadcast selection controls
- Added SSH command import
- Improved saved SSH authentication modes: Password, Identity File, and None
- Added optional SSH Keep Alive
- Improved saved connection and folder management
- Improved Keychain-backed password handling and concurrent SSH authentication
- Added real session information and terminal status metadata
- Hardened disconnected-session handling for Broadcast selection
- Improved Command-W so it closes the current terminal session instead of the main window
- Preserved Sparkle update continuity from GATE22 1.x while moving future updates to the Terminat feed

### Distribution

- Developer ID signed
- Hardened Runtime enabled
- Apple notarized
- Distributed as a signed, notarized, stapled DMG
