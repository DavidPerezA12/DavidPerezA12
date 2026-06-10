# Mac UtilityHub

Mac UtilityHub is a native macOS utility app built around the parts of my setup that are too visual or stateful for dotfiles.

[Website](https://macutilityhub-site.vercel.app)

## Direction

The app is being built as one modular SwiftUI app, not a pile of small menu-bar tools. The repo is split into local Swift packages so risky parts can be tested away from the UI:

- `BatteryKit` for read-only battery state and later battery-care experiments.
- `CleanupKit` for scan reports, path safety and dry-run cleanup plans.
- `SystemMetricsKit` for CPU, memory, disk, network and hardware summaries.
- `CommandKit` for a command palette, aliases and frecency-based ranking.
- `AIChatKit` for provider-neutral chat models and OpenRouter streaming.
- `ClipboardKit` for local clipboard history with privacy rules.
- `HubCore`, `HubUI`, `MenuBarKit`, `InputKit` and `LicensingKit` for app shell, UI, menu-bar behavior and future paid/pro flags.

There are 11 Swift packages, around 121 Swift files across the app/packages, and tests for package-level behavior.

## Safety Rules

The cleanup and system modules are conservative on purpose. The first useful version should scan and explain before it deletes anything. Destructive work starts as dry-run output, with explicit path classification and no permanent deletion by default.

That same rule applies to battery and input features: read-only first, active control later, and only where the OS behavior is understood.

## Relation To Dotfiles

My dotfiles repo bootstraps the terminal side of a Mac: Zsh, Homebrew, Neovim, Git defaults, iTerm and setup scripts. Mac UtilityHub is the companion for things I want to inspect or trigger from a native interface: cleanup candidates, battery state, quick commands, clipboard history and small workflow utilities.

## Status

Private alpha. The app shell, command center and first useful modules are the focus. A private beta site exists, but the product is still more engineering platform than finished utility.
