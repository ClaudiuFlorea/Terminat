# Terminat Roadmap

This roadmap tracks product directions under consideration. Items are intentionally not tied to release dates until implementation scope and technical constraints are validated.

## Command Layer

### Custom terminal commands

Introduce a Terminat-native command namespace using a reserved prefix such as `//`.

Examples:

```text
//new-tab
//close-tab
//next-tab
//prev-tab
//layout grid
//layout columns
//layout rows
//layout single
//broadcast
//sidebar toggle
```

Goals:

- execute Terminat actions directly from the terminal
- keep commands out of the underlying local shell or SSH session
- focus newly created sessions automatically
- preserve normal terminal behavior and avoid interfering with interactive CLI applications

Implementation must be designed around terminal input semantics rather than assuming shell input always arrives as complete lines.

## AI Command Assistant

Add an AI-assisted command layer that converts natural-language requests into shell commands and executes them in the active terminal session.

Example:

```text
//ai show me x.txt
```

Possible execution:

```bash
cat x.txt
```

Goals:

- support both local and SSH terminal sessions
- execute through the existing PTY/session rather than simulating terminal output
- show the generated command before or while it runs
- keep credentials out of model context
- support provider abstraction rather than hard-coding a single model vendor
- initially support bring-your-own API key stored in macOS Keychain
- distinguish read-only, mutating, and dangerous commands
- require confirmation for commands that modify the system or data
- preserve a clear audit trail between user intent, generated command, and real terminal output

Future direction:

- multi-step troubleshooting and sysadmin workflows
- use prior command output as context
- inspect logs, processes, configuration, and system state iteratively
- optional support for multiple AI providers

## Session Recording and Export

### Save Terminal Session to File

Allow any terminal session to be exported as a complete transcript.

Initial scope:

- `Save Session to File…`
- native macOS save panel
- include commands, output, errors, prompts, and available scrollback
- save as plain text

Potential extensions:

- `.log` export
- ANSI-preserving export
- timestamps
- automatic session recording
- save on close
- export selected ranges
- structured separation between input and output

The implementation must preserve the full available session history rather than exporting only the currently visible terminal viewport.
