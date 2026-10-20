# Security

Security is a core requirement for Terminat because the application manages terminal sessions, SSH connections, and optional saved credentials.

## Reporting a security issue

Do **not** report vulnerabilities, credentials, private keys, host details, or other sensitive information in a public GitHub issue.

If you discover a security issue, contact the maintainer privately through the GitHub account associated with this repository.

## Credential storage

Saved SSH passwords are stored in macOS Keychain.

Terminat does not store SSH passwords in:

- connection JSON files
- UserDefaults
- command-line arguments
- logs

Keychain items are configured as non-synchronizing local items.

## SSH password delivery

Saved passwords are supplied to OpenSSH through Terminat's compiled AskPass flow.

The helper:

- has no direct Keychain password-reading capability
- communicates with the running Terminat application over a private local Unix-domain socket
- is validated by process identity and code-signing identity
- is tied to the exact live `/usr/bin/ssh` parent PID for the active terminal session
- fails closed if session, process, prompt, or identity validation fails

The main Terminat process remains the only component that reads the saved password from Keychain.

## Local shell

Terminat intentionally runs outside the macOS App Sandbox so local `zsh` behaves like a normal terminal.

Release builds retain Hardened Runtime and are signed with Apple Developer ID and notarized by Apple.

## Updates

Terminat uses Sparkle 2.

Updates are:

- delivered over HTTPS
- described by the public Sparkle appcast
- protected by Sparkle EdDSA signatures
- distributed as Apple Developer ID signed and notarized builds

## Data integrity

Saved connection data is written atomically.

If the saved-connections JSON exists but is unreadable or corrupt, Terminat preserves the original data, creates a timestamped backup, and blocks automatic connection/folder persistence writes until a valid reload restores a safe state.
