<div align="center">

# Celestial Server

**A fast, good-looking terminal app for running and managing Minecraft Java servers.** Built in Rust. Backups, remote managers, Playit tunnels. Windows and Linux.

<p>
  <img src="https://img.shields.io/badge/Rust-built%20with-orange?style=flat&logo=rust&logoColor=white" alt="Rust">
  <img src="https://img.shields.io/badge/Windows-10%20%7C%2011-0078D6?style=flat" alt="Windows 10 | 11">
  <img src="https://img.shields.io/badge/Linux-supported-FCC624?style=flat&logo=linux&logoColor=black" alt="Linux">
  <img src="https://img.shields.io/badge/Minecraft-Java-62B47A?style=flat" alt="Minecraft Java">
  <img src="https://img.shields.io/badge/tunnel-Playit-8A2BE2?style=flat" alt="Playit">
  <img src="https://img.shields.io/badge/license-MIT-blue?style=flat" alt="MIT License">
  <a href="https://github.com/kradengdeng/celestial-server/releases">
    <img src="https://img.shields.io/github/v/release/kradengdeng/celestial-server?style=flat&label=version&color=4c1" alt="Latest release">
  </a>
</p>

<img src="assets/screenshot.png" alt="Celestial Server showing its required update screen" width="760">

<p><em>Celestial Server's required update screen</em></p>

<p>
  <a href="#download">Download</a> |
  <a href="#quick-start">Quick start</a> |
  <a href="#controls">Controls</a> |
  <a href="#sharing-access-with-managers">Sharing</a> |
  <a href="#updates">Updates</a> |
  <a href="#data-and-privacy">Data</a> |
  <a href="#troubleshooting">Troubleshooting</a>
</p>

</div>

> **Note:** This project is under active development. Keep a recent backup of your Minecraft world before changing server files or updating.

## Features

| Feature | Description |
| --- | --- |
| **One terminal interface** | Start, stop, restart, and monitor a Minecraft Java server in one place. |
| **Live monitoring** | Server logs, player activity, uptime, and system resource usage. |
| **Console** | Press `/` to run server console commands without leaving the app. |
| **World backups** | Size and time estimates, plus control over how many backups are kept. |
| **Manager access** | Invite up to five managers with one-time codes that rotate automatically. |
| **Permissions** | Grant per-manager permissions and block specific console commands. |
| **Join tab** | Connect remotely to a host and reconnect to saved sessions. |
| **Playit and webhooks** | Configure Playit tunnels and Discord-compatible webhooks. |
| **Auto-update** | Checks GitHub releases and installs updates, keeping your settings and data. |

## Download

Get the latest release from the [Releases page](https://github.com/kradengdeng/celestial-server/releases).

**Windows:** extract the archive and run `celestial-server.exe` in a terminal.

**Linux:** download the matching asset, then:

```sh
chmod +x celestial-server
./celestial-server
```

On first launch, Celestial creates its configuration and data directory automatically and asks for your Minecraft server folder and Java executable.

### Requirements

| Requirement | Details |
| --- | --- |
| OS | Windows 10/11 or a supported Linux distribution |
| Java | Installed and compatible with your Minecraft server version |
| Server file | A Minecraft server `.jar` |
| Remote access | A TCP tunnel forwarding to the share port (Playit supported) |
| Rust toolchain | Only if building from source |

### Build from source

```sh
git clone https://github.com/kradengdeng/celestial-server.git
cd celestial-server
cargo build --release
```

The binary is created in `target/release/` (`celestial-server.exe` on Windows).

## Quick start

1. Launch Celestial and select your Minecraft server folder.
2. In **Settings**, set the server `.jar` and Java path if they were not detected.
3. Open `eula.txt` in your server folder, review the Minecraft EULA, and accept it.
4. On the **Main** tab, press `S` to start the server.
5. Open the **Server** tab to watch logs. Press `/` to enter a console command.
6. Stop the server, then press `B` on the Main tab to create a backup.

> Backups can only be created while the server is stopped.

## Controls

| Action | Keys |
| --- | --- |
| Switch tabs | `1`–`6`, `F1`–`F6`, `Tab` / `Shift+Tab` |
| Start / stop / restart server | `S` / `X` / `R` |
| Create backup | `B` |
| Connect / disconnect Playit | `P` / `O` |
| Enter a console command | `/`, then `Enter` to run or `Esc` to cancel |
| Scroll server logs | `Page Up` / `Page Down`; `End` to return to the bottom |
| Edit manager permissions (Share) | `F4` |
| Generate a new invite code (Share) | `F6` |
| Quit | `Ctrl+C` |

Tab numbers and function keys use physical key position, so they work across keyboard layouts.

## Sharing access with managers

A host can grant limited server controls to up to five managers.

**Host**

1. Configure a TCP tunnel forwarding to `127.0.0.1:25580` (or the port shown in Settings).
2. Enter the tunnel's public address in **Share address** (Settings).
3. Open **Share** and send the manager the displayed address and one-time invite code. Press `F6` for a new code.

**Manager**

1. Open **Join** and press `Enter`.
2. Enter the host's address and invite code when prompted.

**Permissions**

| Rule | Details |
| --- | --- |
| Default | New managers start with no permissions. Select one in **Share** and press `F4` to grant actions. |
| Commands | Console commands can be restricted by command name. |
| Backups | Managers cannot create backups. |
| Host control | Pause access, extend access time, or revoke access at any time. |

## Updates

Celestial checks `kradengdeng/celestial-server` releases on startup. When a newer release exists, the update screen requires installing it before continuing.

| Behavior | Details |
| --- | --- |
| Your data | Configuration and server data are kept. |
| Verification | A published `.sha256` checksum is verified when the release provides one. |
| Restart | Celestial restarts automatically after installing. |
| Network | Internet is required for the check and download. |

## Data and privacy

Celestial stores configuration, manager records, join details, audit log, and backups here:

| Platform | Default location |
| --- | --- |
| Windows | `%APPDATA%\CelestialServer` |
| Linux | `$XDG_CONFIG_HOME/CelestialServer` or `~/.config/CelestialServer` |

Set `CELESTIAL_DATA_DIR` to use a different directory.

> **Warning:** Never share this directory publicly. It can contain access credentials and server management information.

## Troubleshooting

| Problem | Fix |
| --- | --- |
| Java not found | Install a compatible Java version and set its executable path in **Settings**. |
| Server port already in use | Stop the other process using the port, or change it in `server.properties`. |
| Managers cannot connect | Check that the tunnel forwards to the local share port and the public address is correct. |
| Keyboard input issues | Set `CELESTIAL_INPUT_LOG=1` before starting. Key events are logged in the data directory. |

## License

Licensed under the MIT License. See [LICENSE](LICENSE).

## Credits

Created by [@kradengdeng](https://github.com/kradengdeng).
