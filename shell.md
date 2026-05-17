# Command Shell — Roblox (Site Polaris)

## Overview

The **Command Shell** is a lightweight, extensible command-line interface designed for **Site Polaris** on Roblox. Inspired by traditional operating system shells such as **Bash**, **PowerShell**, and **Windows Command Prompt**, the project aims to provide privileged users with a fast, scriptable, and efficient environment for interacting with in-game systems, moderation tools, administrative functions, and developer utilities.

The shell serves both as a standalone productivity tool and as the architectural foundation for a future **Command Console** — a graphical administrative interface intended for moderators, developers, and operators with minimal technical training.

The project prioritizes:
- Speed and responsiveness
- Modular command architecture
- User accessibility
- Extensibility for future tooling
- Lightweight runtime overhead
- Familiar shell-like interaction patterns

---

# Goals

## Primary Goals

- Create a functional shell environment within Roblox
- Provide fast execution of administrative and utility commands
- Enable efficient moderation and development workflows
- Support future GUI-based tooling through shared backend systems
- Offer a familiar terminal-style experience for experienced users

## Secondary Goals

- Allow command scripting and automation in the future
- Support role-based access control and permission layers
- Enable customizable aliases, profiles, and shell behaviors
- Maintain high maintainability and modularity
- Ensure low impact on gameplay performance

---

# Core Features

## Command Execution

- Parse and execute typed commands
- Support positional arguments and flags/options
- Command chaining and piping (future consideration)
- Quoted string parsing
- Error handling and syntax feedback

Example:
```shell
kick PlayerName "Disruptive behavior"
teleport PlayerName Spawn
ban PlayerName --duration 7d