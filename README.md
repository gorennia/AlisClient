<p align="center">
  <img src="logo.png" width="112" alt="AlisClient logo" />
</p>

<h1 align="center">AlisClient</h1>

<p align="center">
  A fast, modern Minecraft: Java Edition launcher for Windows — modpacks, mods, skins and your own servers in one place.
</p>

---

## About

AlisClient is an independent desktop launcher for **Minecraft: Java Edition**. It installs and runs the official game
files from Mojang's public servers, manages instances (separate game folders with their own versions, loaders and mods)
and makes it easy to build, share and play modpacks.

The launcher is written in **Rust** (core) with a **React + TypeScript** interface on **Tauri 2**. It is a native
Windows application; the interface is available in **English and Russian**.

## Features

- **Instances** — any Minecraft release, with Fabric, Quilt, Forge or NeoForge. Each instance has its own Java,
  memory, JVM flags (with presets), window size and environment.
- **Automatic Java** — downloads the Java runtime Mojang recommends for each version; detects installed Java as well.
- **Fast downloads** — parallel downloads with SHA-1 verification and resume; missing libraries and mod dependencies
  are fetched automatically before launch.
- **Content catalog** — mods, modpacks, resource packs, shader packs, data packs and plugins from
  [Modrinth](https://modrinth.com), with filters by version, loader, category and environment, infinite scroll and
  one-click install with dependencies.
- **Modpack sharing** — export an instance as `.mrpack`, `.zip` or the launcher's own `.alispack` file (Modrinth mods
  are stored as links, so packs stay small) and import them with a double click.
- **AI pack builder and AI crash helper** — optional; uses the player's own AI provider key. The helper reads the
  game log and crash report and suggests which mod to disable.
- **Skins** — 3D preview, a personal skin library, upload from PNG or by player name, and a skin catalog.
- **Local servers** — create a server on Paper, Vanilla, Fabric, Quilt, Forge or NeoForge, add plugins or mods,
  or turn a Modrinth modpack into a server. The player accepts the Minecraft EULA themselves.
- **Discord Rich Presence** — optional status ("In the launcher" / "Playing <pack>"), can be turned off in Settings.
- **Customisation** — themes, accent colours and a home screen layout editor.

## Accounts and sign-in

| Account type  | Status |
| ------------- | ------ |
| Microsoft     | In progress — waiting for Minecraft API access approval |
| Ely.by        | Supported |
| Offline       | Supported (for local / LAN play) |

### How Microsoft sign-in works in AlisClient

- Sign-in uses the **official Microsoft OAuth 2.0 flow** (authorization code with PKCE) in the system web browser.
  The launcher never sees or stores the user's Microsoft password.
- The token chain is the standard one: Microsoft account → Xbox Live → XSTS → Minecraft services, followed by an
  entitlement check that the account **owns Minecraft: Java Edition**. Accounts without the game cannot play online.
- Refresh tokens are stored **only on the user's computer**, in the operating system's secure credential store
  (Windows Credential Manager). Nothing is sent to any server run by AlisClient — the launcher has no backend of its own.
- Tokens are used only to sign in, launch the game and manage the player's own skin and profile.

## Privacy

- No telemetry, no analytics, no accounts on our side.
- Network requests go only to the services a feature needs: Mojang / Microsoft (game files, sign-in), Modrinth
  (content), Mojang (Java runtime) and, if the player enables them, Discord (local IPC only) or an AI provider.
- Secrets (tokens, API keys) live in the OS credential store, never in plain-text files.

## Download

Releases are published as a Windows installer (`AlisClient-Setup.exe`). The installer works per user and does not
need administrator rights; it can be removed from Windows *Installed apps*.

## Disclaimer

AlisClient is **not an official Minecraft product** and is not approved by or associated with Mojang or Microsoft.
Minecraft is a trademark of Mojang Synergies AB. The launcher downloads the game only from official Mojang servers and
requires a legitimate copy of Minecraft: Java Edition for online play.
