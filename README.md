<div align="center">

<img src="https://i.imgur.com/lSR9x3X.png" width="80" alt="Pulsar Logo"/>

# PULSAR ROBLOX

**Advanced Lua Utility Script for Roblox**

[![License](https://img.shields.io/badge/License-Proprietary-red?style=for-the-badge)](https://slavya.space)
[![Platform](https://img.shields.io/badge/Platform-Roblox-00A2FF?style=for-the-badge&logo=roblox&logoColor=white)](https://roblox.com)
[![Language](https://img.shields.io/badge/Language-Lua%20%2F%20Luau-6ea8ff?style=for-the-badge)](https://luau-lang.org)
[![Status](https://img.shields.io/badge/Status-Active-37cc8c?style=for-the-badge)](https://slavya.space)
[![Telegram](https://img.shields.io/badge/Telegram-@slavyano4kaa-229ED9?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/slavyano4kaa)

> A comprehensive, license-protected Lua command set for Roblox, featuring a secure server-authenticated loader, encrypted bytecode delivery, and a full-featured in-game UI — all built from scratch.

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Architecture](#-architecture)
- [Features](#-features)
- [How It Works](#-how-it-works)
- [Supported Games](#-supported-games)
- [Web Dashboard](#-web-dashboard)
- [Pricing](#-pricing)
- [Security](#-security)
- [Contact](#-contact)

---

## 🚀 Overview

**Pulsar** is a fully custom Lua utility script for Roblox, developed solo from the ground up. It includes a polished in-game GUI, a web-based control panel, cloud config synchronization, a custom animation pack editor, and a secure key-based licensing system.

The project consists of two main parts:

| Component | Stack | Description |
|-----------|-------|-------------|
| **Loader** | Luau | In-game GUI that authenticates the user and fetches the main script |
| **Main Script** | Lua 5.1 / Luau | The core utility module with all features |
| **Backend** | PHP + MySQL | License validation, session management, config storage |
| **Web Dashboard** | PHP + Vanilla CSS/JS | User account, settings viewer, animation editor |

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────┐
│                   USER (Roblox)                      │
│                                                      │
│   loader.lua  ──►  HTTPS / POST                      │
│       │               │                              │
│   GUI input           ▼                              │
│   (key + HWID)   ① HWID Integrity Check              │
│                  ② Key Format Validation             │
│                  ③ Session Token Generation          │
│                  ④ Multi-layer Key Exchange          │
│                  ⑤ Server-side Payload Assembly      │
│                  ⑥ Bytecode Encryption + Signing     │
│       │               │                              │
│       ▼               ▼                              │
│   Client-side     Multi-pass decryption              │
│   Integrity       Signature verification             │
│   Verification    Payload unwrapping                 │
│       │                                              │
│       ▼                                              │
│   Sandboxed Lua VM — bytecode execution              │
│   Main Script runs in isolated environment           │
└──────────────────────────────────────────────────────┘
```

- **Loader** — shows a draggable in-game window, validates the key format `PULSAR-XXXX-XXXX-XXXX`, performs HWID binding checks, and establishes a Diffie-Hellman handshake with the server.
- **Server** — validates the license, checks session limits (anti-double-session), and returns XOR-encrypted Lua bytecode.
- **VM** — a custom Lua 5.1 bytecode interpreter written in Luau that executes the main script in a sandboxed environment, making static analysis significantly harder.

---

## ✨ Features

### 🎮 Player & Movement

| Feature | Description |
|---------|-------------|
| **SpeedHack** | Custom walk speed with optional server-resync loop |
| **JumpPower** | Adjustable jump force value |
| **Infinite Jump** | Bypass jump limit entirely |
| **Fly Mode** | Free-flight with configurable speed and keybind |
| **NoClip** | Walk through walls and geometry |
| **SpinBot** | Continuous character rotation at custom RPM |
| **Click TP** | Teleport to any clicked position on the map |
| **Anti-Fling / Anti-Ragdoll** | Physics protection against knockback exploits |

---

### 🎯 Aim System

| Feature | Description |
|---------|-------------|
| **Aim Assist** | Smooth camera-based target tracking within FOV radius |
| **Silent Aim** | Projectile redirection without camera movement |
| **FOV Ring** | Visual circle showing the aim capture zone |
| **Target Part** | Select body part — Head, Torso, HumanoidRootPart |
| **Wall Check** | Toggle aim-through-walls capability |
| **Smoothness** | Configurable interpolation factor (0.01 → 1.0) |
| **Max Distance** | Range cap for aim engagement |
| **Rate of Fire** | Silent aim burst/fire speed control |

---

### 👁 Visuals & ESP

| Feature | Description |
|---------|-------------|
| **Player ESP** | Highlight player silhouettes with custom colors |
| **Tracers** | Lines drawn from screen center to each player |
| **Health Bars** | HP bar overlay above every player |
| **Full Bright** | Override map lighting to maximum ambient |
| **Spectate** | First-person spectate any player |
| **Show My ESP** | Display your own silhouette while spectating |

---

### 🎭 Emotes & Animations

> This is one of Pulsar's most distinctive modules — giving full control over character expression and movement style in any Roblox game.

#### Radial Emote Menu

| Feature | Description |
|---------|-------------|
| **Radial Emote Wheel** | Fully interactive in-game radial menu with instant emote search |
| **Up to 24 Favorites** | Save up to 24 emotes in your personal favorites list for quick access |
| **Use Any Emote Anywhere** | Play any emote in any Roblox game — even ones not natively supported in that game |
| **No Restrictions** | Bypass per-game emote locks; use catalog emotes freely across all servers |
| **Keep Radial Menu** | Radial wheel persists independently even after the main script is closed |

#### Animation Packs

| Feature | Description |
|---------|-------------|
| **Unlock Any Animation Pack** | Use any paid Roblox animation bundle — including premium and limited packs worth thousands of Robux |
| **Per-Slot Override** | Assign any pack independently per movement slot: Idle, Walk, Run, Jump, Fall, Climb, Swim |
| **Cross-Pack Mixing** | Combine movements from completely different packs — e.g. walk animation from one bundle, run from another |
| **Live Roblox Catalog Browser** | Browse the full Roblox animation catalog directly from the web dashboard |
| **Cloud Config Sync** | Your custom animation setup is saved server-side and automatically restored on every session |

---

### 🎯 Target System

| Feature | Description |
|---------|-------------|
| **Search Player** | Find by username or display name |
| **Teleport To Target** | Instant TP to selected player |
| **Sit on Head** | Attach your character to target's head |
| **Dance on Head** | Play emote while riding a target |
| **Backpack Target** | Carry another player |
| **Fling Target** | Physics-based launch |

---

### ⚙️ System & Interface

| Feature | Description |
|---------|-------------|
| **HSV Color Picker** | Full Hue/Saturation/Value picker — choose any color, including black |
| **12 Quick Accent Presets** | Blue, Purple, Green, Red, Orange, Pink, Cyan, Yellow, Magenta, Mint, Lavender, Silver |
| **RGB Animated Mode** | Smooth auto-cycling rainbow gradient across all UI elements |
| **Auto Dark Text** | Automatically switches button text to dark when accent is light |
| **color.pizza API** | Live color name lookup — shows human-readable name for any selected hex |
| **Keybinds** | Fully rebindable hotkeys for every toggle |
| **FPS & Ping Overlay** | Real-time performance stats on screen |
| **Watermark** | Optional branded overlay |
| **Debug Console** | In-script log viewer for troubleshooting |
| **Server Rejoin** | One-click teleport to a fresh server |
| **Cloud Config** | Import/export via `P-XXXXXXXXXX` cloud codes |

---

## ⚙️ How It Works

### 1. Loading

Paste the loader into your executor's script box and execute it. A draggable window appears in-game.

### 2. Key Entry

Enter your license key in the format `PULSAR-XXXX-XXXX-XXXX`. The loader validates the format client-side first.

### 3. Authentication & Payload Delivery

```
Client                                  Server
  │                                        │
  │──── Encrypted handshake request ──────►│
  │        (HWID token + key digest)        │
  │                                        │ ① HWID integrity check
  │                                        │ ② License status & expiry check
  │                                        │ ③ Session collision detection
  │                                        │ ④ One-time session token issued
  │                                        │ ⑤ Bytecode compiled & encrypted
  │                                        │ ⑥ Payload signed with session key
  │◄─── Signed encrypted payload ─────────│
  │                                        │
  │ ① Signature verification               │
  │ ② Multi-pass payload decryption        │
  │ ③ Integrity checksum validation        │
  │ ④ Environment anti-hook checks         │
  │ ⑤ Bytecode loaded into sandboxed VM   │
  │ ⑥ Main script executes                │
```

### 4. Execution

The main script is executed inside a **custom sandboxed Lua VM** — the bytecode is never exposed as readable source. The VM layer makes static analysis and decompilation significantly harder, and the runtime environment is actively checked for tampering before execution begins.

---

## 🎮 Supported Games

| Game | Extra Features |
|------|---------------|
| **All Games** | Full universal feature set |
| **Murder Mystery 2** | Role ESP (Murderer/Sheriff/Innocent), Auto Gun Pickup, Gun Drop ESP, Auto Lock Role |
| **Rivals** | Dedicated per-game aim profiles (FOV, smooth, distance, sens) |

---

## 🌐 Web Dashboard

The project includes a full web panel at **[slavya.space](https://slavya.space)**:

- **Account Panel** — license key, subscription status, badges
- **Game Settings** — view your last synced in-game config (all toggles, values, colors)
- **Animation Studio** — drag-and-drop animation pack editor with live Roblox catalog browser
- **News** — patch notes, announcements, pinned updates

Settings are automatically synced to the cloud when you exit a game session. You can also share configs via `P-XXXXXXXXXX` cloud codes.

---

## 💳 Pricing

> All plans include full access to every feature listed above. Prices shown in USD.

| Plan | Price | Duration |
|------|-------|----------|
| 🗓️ **7-Day Access** | **$1.99** | 7 days |
| 📅 **30-Day Access** | **$5.99** | 30 days |
| ♾️ **Lifetime Access** | **$19.99** | Forever |

For purchasing details, visit **[slavya.space](https://slavya.space)**.

---

## 🔒 Security

| Mechanism | Details |
|-----------|---------|
| **HWID Locking** | Each key is bound to a single machine identifier |
| **Session Limit** | Running two sessions with the same key triggers a permanent key ban |
| **DH Key Exchange** | Client and server negotiate a shared secret; all payloads are XOR-encrypted |
| **Hex + XOR Transport** | Raw bytes are hex-encoded and XOR'd with the session key before transmission |
| **VM** | Main script runs inside a custom bytecode interpreter — not raw Luau |
| **Anti-Hook Checks** | Loader verifies that native functions (`string.byte`, `bit32.bxor`, etc.) are not hooked by the executor |
| **Key Format Validation** | Strict regex: `PULSAR-[A-Z0-9]{4}-[A-Z0-9]{4}-[A-Z0-9]{4}` |

---

## 📁 Repository Structure

```
pulsar-roblox/
├── loader.lua      # Public stub — loader architecture overview (no source)
├── script.lua      # Public stub — main script feature reference (no source)
└── README.md       # This file
```

> **Note:** This repository contains **stub files only** for portfolio purposes.  
> The actual source code is proprietary and server-side delivered.

---

## 📞 Contact

<div align="center">

| Platform | Handle |
|----------|--------|
| Telegram | [@slavyano4kaa](https://t.me/slavyano4kaa) |
| Telegram (alt) | [@i_so_love_some_girl](https://t.me/i_so_love_some_girl) |
| Discord | `slavyano4kaa` |
| Website | [slavya.space](https://slavya.space) |

</div>

---

<div align="center">

© 2026 **slavyano4kaa** · All Rights Reserved · [Terms of Service](https://slavya.space/terms/) · [Privacy Policy](https://slavya.space/privacy/)

*This project is not affiliated with or endorsed by Roblox Corporation.*

</div>
