<p align="center">
  <img src="dashboard/public/branding/kreo-banner-v2.webp" alt="Kreo — music for your Discord server" width="960" />
</p>

<h1 align="center">🎵 Kreo - Discord Music Bot & Real-Time Web Dashboard</h1>

<p align="center">
  A state-of-the-art Discord music ecosystem featuring a hybrid-sharded bot and a responsive, purple-themed Next.js web dashboard.<br />
  Stream high-fidelity audio, control playback with live Socket.IO sync, and customize room soundscapes together.
</p>

<p align="center">
  <a href="https://github.com/mohsinmomin440/Kreo"><img src="https://img.shields.io/github/stars/mohsinmomin440/Kreo?style=for-the-badge&color=8B5CF6&logo=github" alt="Stars" /></a>
  <a href="https://github.com/mohsinmomin440/Kreo/actions/workflows/ci.yml"><img src="https://img.shields.io/github/actions/workflow/status/mohsinmomin440/Kreo/ci.yml?branch=main&style=for-the-badge&logo=githubactions&logoColor=white&label=CI" alt="CI Status" /></a>
  <a href="./package.json"><img src="https://img.shields.io/badge/Node.js-24%2B-5FA04E?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js 24" /></a>
  <a href="./package.json"><img src="https://img.shields.io/badge/Discord.js-v14-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Discord.js 14" /></a>
  <a href="./dashboard/package.json"><img src="https://img.shields.io/badge/Next.js-v16-000000?style=for-the-badge&logo=nextdotjs&logoColor=white" alt="Next.js 16" /></a>
  <a href="./LICENSE"><img src="https://img.shields.io/badge/License-Source%20Available-A78BFA?style=for-the-badge" alt="License" /></a>
</p>

<p align="center">
  <a href="#-features">Features</a> •
  <a href="#-quick-start">Quick Start</a> •
  <a href="./SETUP_GUIDE.md">Full Setup Guide</a> •
  <a href="#-commands">Commands</a> •
  <a href="#-audio-filters">Audio Filters</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-author--credits">Author & Credits</a>
</p>

---

> ⚖️ **Copyright & Attribution Notice:** Authored and maintained by **Mohsinali Momin**. Read the full [Copyright Notice](./COPYRIGHT-NOTICE.md) and [License](./LICENSE).

---

## 🌟 Features

<table>
  <tr>
    <td width="50%">
      <h3>🤖 Discord Music Bot</h3>
      <ul>
        <li><b>Lavalink v4 Powered:</b> Ultra-low latency, crystal-clear audio streaming via Kazagumo and Shoukaku.</li>
        <li><b>Slash & Prefix Commands:</b> Full support for Discord slash interactions (<code>/</code>) and custom text prefixes.</li>
        <li><b>13 Studio Audio Filters:</b> 8D, BassBoost, Nightcore, Vaporwave, Slowed + Reverb, and more.</li>
        <li><b>24/7 Voice & Reconnect:</b> Auto-reconnect to voice channels with Lavalink session state recovery.</li>
        <li><b>Personal Playlists & Liked Songs:</b> Save tracks with <code>/like</code> and load custom personal playlists on demand.</li>
        <li><b>Cluster & Sharding Ready:</b> Hybrid sharding built with <code>discord-hybrid-sharding</code>.</li>
      </ul>
    </td>
    <td width="50%">
      <h3>💻 Modern Web Dashboard</h3>
      <ul>
        <li><b>Next.js 16 & React 19:</b> Dark purple studio aesthetic with fluid animations and responsive mobile UI.</li>
        <li><b>Real-Time Socket.IO Sync:</b> Instantaneous player state, live queue reordering, and track scrubbing.</li>
        <li><b>Discord OAuth Login:</b> Secure <code>next-auth</code> session flow verifying server manage permissions.</li>
        <li><b>Command Palette (Ctrl + K):</b> Instant server navigation and quick song searches anywhere.</li>
        <li><b>Room Management:</b> Pin favorite servers, view recent rooms, and customize bot behavior per guild.</li>
        <li><b>Guild Leaderboard:</b> Track top played songs and community listening trends.</li>
      </ul>
    </td>
  </tr>
</table>

---

## 📋 Requirements

| Requirement | Version / Specification | Notes |
| :--- | :--- | :--- |
| **Node.js** | `>= 20.19.0` (Recommended: **Node.js 24**) | Required for both bot core and web dashboard |
| **npm** | `>= 10.0.0` | Node Package Manager |
| **Discord Application** | Developer Portal Bot & OAuth Application | Bot Token, Client ID, and Client Secret |
| **MongoDB** | `>= 6.0` (Local or MongoDB Atlas) | Shared database for settings, playlists & history |
| **Lavalink Server** | Lavalink **v4.x** | Requires plugins for your search sources (YouTube, Spotify, etc.) |

---

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/mohsinmomin440/Kreo.git
cd Kreo
```

### 2. Install Dependencies
```bash
# Install bot dependencies
npm ci

# Install dashboard dependencies
npm ci --prefix dashboard
```

### 3. Setup Environment Variables
Create your local `.env` and `dashboard/.env.local` configuration files:

**Windows (PowerShell):**
```powershell
Copy-Item .env.example .env
Copy-Item dashboard/.env.example dashboard/.env.local
```

**Linux / macOS:**
```bash
cp .env.example .env
cp dashboard/.env.example dashboard/.env.local
```

### 4. Discord Developer Portal Setup
1. In the [Discord Developer Portal](https://discord.com/developers/applications), select your application.
2. Under **Bot**, enable **Server Members Intent** and **Message Content Intent**.
3. Under **OAuth2 > General**, add your redirect URI:
   ```text
   http://localhost:3000/api/auth/callback/discord
   ```

### 5. Build & Launch

```bash
# Build the web dashboard
npm run build --prefix dashboard

# Start both bot and dashboard concurrently
npm start
```

* 🌐 **Dashboard:** Visit [http://localhost:3000](http://localhost:3000)
* 🎧 **Discord:** Join a voice channel in your server and type `/play` or `>play`

---

## 📜 All NPM Scripts

| Command | Action |
| :--- | :--- |
| `npm start` | Launches bot and built dashboard together in production mode |
| `npm run dev` | Runs bot and dashboard concurrently with hot-reload enabled |
| `npm run start:bot` | Runs only the Discord bot cluster manager (`devrock.js`) |
| `npm run start:dash` | Runs only the Next.js production dashboard |
| `npm run dev:dash` | Runs the dashboard in Next.js development mode |
| `npm test` | Executes the complete regression test suite with mocked services |
| `npm run check:services` | Performs an interactive health check on Discord, MongoDB & Lavalink |

---

## 🎛️ Audio Filters

Enhance your music experience with 13 real-time DSP audio filters:

| Filter | Description |
| :--- | :--- |
| `8D Audio` | Immersive spatial audio rotating smoothly across left and right channels |
| `BassBoost` | Deep low-frequency amplification for heavy basslines |
| `Deep Bass` | Sub-bass harmonic saturation |
| `Treble Boost`| Enhanced high-frequency clarity for acoustic and vocal tracks |
| `Nightcore` | Increased tempo, pitch, and energy |
| `Daycore` | Slowed tempo with dropped pitch for a mellow groove |
| `Slowed + Reverb` | Lo-fi chill aesthetic with spatial reverberation |
| `Vaporwave` | Retro pitch-shifted nostalgic sound |
| `Chipmunk` | Fun high-pitched octave transformation |
| `Karaoke` | Vocal band suppression for sing-along sessions |
| `Soft` | Relaxing low-pass filter reducing harsh high frequencies |
| `China` | Subtle pentatonic resonance emulation |
| `Vibrato` | Dynamic audio pitch modulation |
| `Reset` | Immediately disables active DSP filters back to pure flat audio |

---

## ⌨️ Command Cheatsheet

Use `/help` or your server prefix (default `>help`) to browse available commands:

```text
🎵 Music
   ├── /play <query|url>       Stream songs from YouTube, Spotify, Soundcloud, etc.
   ├── /pause & /resume        Pause or resume the active track
   ├── /skip & /forceskip      Skip the current song or vote skip
   ├── /queue                  Inspect the live queue with interactive pagination
   ├── /volume <1-150>         Adjust output volume safely
   ├── /seek <time>            Jump directly to any point in the track
   ├── /loop <track|queue|off> Set loop state
   ├── /shuffle                Randomize queue order without interrupting current song
   ├── /autoplay               Continuously play similar tracks when queue finishes
   ├── /lyrics                 Fetch synchronized lyrics for the playing track
   ├── /sleep <minutes>        Set a sleep timer to gracefully stop playback
   └── /history                View recently played tracks in the server

🎚️ Filters
   └── /filter <type>          Apply or reset DSP audio filters

❤️ Favourites & Playlists
   ├── /like                   Add the playing track to your personal liked collection
   ├── /showliked              Browse your personal liked songs
   ├── /playliked              Enqueue all liked tracks into the voice channel
   ├── /pl-create <name>       Create a custom cloud playlist
   ├── /pl-add <name> <song>   Add a song to your playlist
   └── /pl-play <name>         Play an entire custom playlist

⚙️ Configuration & Server
   ├── /247                    Keep the bot connected in voice channel continuously
   ├── /setprefix <prefix>     Change text command prefix for this server
   └── /ignore <channel>       Ignore commands from specific text channels

🛠️ Utility & Info
   ├── /help                   Explore all commands with interactive dropdowns
   ├── /ping                   Check API latency and websocket response times
   ├── /stats                  View RAM, CPU, Lavalink nodes, and uptime stats
   └── /invite                 Generate an authorization invite link
```

---

## 🏗️ Architecture

```text
       ┌────────────────────────┐
       │   Browser Client UI    │
       └───────────┬────────────┘
                   │  Discord OAuth (NextAuth)
                   ▼
       ┌────────────────────────┐
       │  Next.js 16 Dashboard  │
       └───────────┬────────────┘
                   │  Bridge Protocol (HMAC Signed Tickets)
                   ▼
       ┌────────────────────────┐
       │   devrock.js Bridge    │
       │   & Cluster Manager    │
       └───────────┬────────────┘
                   │
         ┌─────────┴─────────┐
         ▼                   ▼
┌─────────────────┐ ┌─────────────────┐
│   Discord Bot   │ │  Lavalink Node  │
│   Worker Nodes  │ │   (Audio DSP)   │
└────────┬────────┘ └─────────────────┘
         │
         ▼
┌─────────────────┐
│  MongoDB Cloud  │
└─────────────────┘
```

---

## 🔒 Security & Privacy

* **Strict Guild Scoping:** Dashboard users can only interact with guilds where they hold authorized Discord permissions.
* **Bridge Authentication:** Communication between the Next.js API and the bot cluster requires a shared `DASHBOARD_BRIDGE_SECRET`.
* **Short-Lived Socket Tokens:** Socket.IO client connections use expiring signed tickets to prevent unauthorized event listening.
* **Safe Credential Handling:** All private tokens, connection strings, and keys are stored exclusively in non-committed `.env` files.

---

## 👤 Author & Credits

* **Project Creator & Maintainer:** **Mohsinali Momin**
  * 🌐 **GitHub:** [@mohsinmomin440](https://github.com/mohsinmomin440)
  * 📦 **Repository:** [https://github.com/mohsinmomin440/Kreo](https://github.com/mohsinmomin440/Kreo)
* **AI Pair Programmer:** [Claude](https://github.com/claude) (`noreply@anthropic.com`)

---

## 📄 License

This project is licensed under the terms of the custom **Kreo Source-Available License 1.0**.
Normal noncommercial use and private modification are permitted. Commercial use, resale, and public redistribution of modified versions require prior written permission.
See the full [LICENSE](./LICENSE) and [COPYRIGHT-NOTICE.md](./COPYRIGHT-NOTICE.md) for complete details.

<p align="center">
  <b>⭐ If you like Kreo, please consider giving it a star on <a href="https://github.com/mohsinmomin440/Kreo">GitHub</a>! ⭐</b>
</p>
