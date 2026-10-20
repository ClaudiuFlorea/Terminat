# Privacy

Terminat is designed as a local-first macOS application.

## Local data

Terminat stores application configuration locally on the Mac, including:

- saved SSH connection metadata
- connection folders
- appearance preferences
- SSH configuration path preference

Saved SSH passwords are stored separately in macOS Keychain.

## No Terminat cloud account

Terminat currently has:

- no Terminat user account
- no Terminat cloud sync
- no Terminat application backend
- no advertising SDK

## Network activity

Terminat makes network connections when required for functionality:

- SSH connections explicitly opened by the user
- Sparkle update checks and downloads
- other network activity initiated by commands running inside terminal sessions

SSH traffic is handled by the system OpenSSH client.

## SSH configuration

If enabled, Terminat reads SSH configuration metadata from the configured SSH config file for display and launch purposes. Terminat does not modify that file.

## Updates

Sparkle checks the public Terminat update feed hosted through GitHub and downloads update artifacts from GitHub Releases.
