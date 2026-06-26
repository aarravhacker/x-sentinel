# Hacker Discord Bot

A powerful multi-functional Discord bot with 900+ commands designed for moderation, entertainment, utility, and server management. Built with advanced security systems including anti-nuke, anti-raid, anti-spam, and real-time threat detection.

---

## Features

### Security System (300+ commands)
- **Anti-Nuke** — Multi-stage protection with behavioral analysis, risk scoring, trust system, and snapshot rollback
- **Anti-Raid** — Join velocity tracking, raid group detection, and auto-revocation
- **Anti-Spam** — Duplicate detection, flood protection, emoji/caps filtering, word blacklisting
- **Anti-Link** — Phishing detection, domain blacklisting, rate limiting, link analytics
- **Anti-Bot** — Bot detection with auto-action and velocity tracking
- **Lockdown** — Channel/role-specific, scheduled, and emergency lockdown modes
- **Trust System** — 5-level trust scoring (Newcomer to Veteran)
- **Snapshot & Rollback** — Pre-destruction snapshots for server state recovery
- **Decoy Protection** — Honeypot detection for reconnaissance

### Moderation (90+ commands)
- Kick, Ban, Mute, Warn, Timeout
- Mass actions and bulk operations
- Voice moderation
- Case tracking system

### Auto-Moderation (40+ commands)
- Word filter with presets
- Spam and flood detection
- Caps lock filtering
- Emoji spam detection
- Mass mention protection

### Music System (60+ commands)
- YouTube/SoundCloud search and playback
- Queue management with loop/shuffle
- Audio filters (bass boost, nightcore, vaporwave, 8D, etc.)
- 24/7 mode and autoplay
- Lavalink integration with Shoukaku

### Economy System (40+ commands)
- Balance, daily rewards, work system
- Shop and inventory
- Level-based progression

### Dashboard (55K+ lines)
- Discord OAuth authentication
- Real-time security monitor
- Guild control panel
- Embed builder
- Economy dashboard

### Additional Systems
- **Welcome/Goodbye** — Custom messages, auto-role assignment, embed customization
- **Reaction Roles** — Self-assignable roles with multiple modes
- **Tickets** — Support ticket system with transcripts
- **Leveling** — XP system, level roles, leaderboards
- **Giveaways** — Automated giveaway management
- **Polls** — Poll creation and management
- **Reminders** — Scheduled reminders
- **Images** — Image generation and manipulation
- **AI Chat** — Gemini-powered AI chat system

---

## Tech Stack

| Technology | Purpose |
|-----------|---------|
| **Node.js** (>=18) | Runtime environment |
| **Discord.js v14** | Discord API wrapper |
| **Express.js** | Dashboard web server |
| **SQLite3** | Primary database |
| **Knex.js** | Query builder & migrations |
| **Shoukaku** | Lavalink music client |
| **@discordjs/voice** | Voice channel connection |
| **Winston** | Logging system |
| **Gemini AI** | AI chat functionality |
| **EJS** | Dashboard templates |
| **Passport.js** | OAuth authentication |

---

## Installation

### Prerequisites
- Node.js 18 or higher
- npm or yarn
- Python (for yt-dlp music support)
- Lavalink server (for music features)

### Step-by-Step Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/aarravhacker/x-sentinel.git
   cd x-sentinel
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   ```
   Edit `.env` with your configuration (see [Environment Setup](#environment-setup))

4. **Run database migrations**
   ```bash
   npm run migrate
   ```

5. **Start the bot**
   ```bash
   # Production
   npm start

   # Development (with auto-reload)
   npm run dev
   ```

6. **Start the dashboard** (optional, separate terminal)
   ```bash
   npm run dashboard
   ```

---

## Environment Setup

Create a `.env` file in the project root with the following variables:

```env
# Discord Bot Configuration (Required)
DISCORD_TOKEN=your_bot_token_here
CLIENT_ID=your_client_id_here
CLIENT_SECRET=your_client_secret_here
OWNER_ID=your_discord_user_id

# Dashboard Configuration
DASHBOARD_PORT=3000
DASHBOARD_SECRET=your_dashboard_secret_key
DASHBOARD_CALLBACK_URL=http://localhost:3000/auth/callback

# AI Configuration (Optional)
GEMINI_API_KEY=your_gemini_api_key
AI_MODEL=gemini-2.0-flash

# Lavalink Configuration (Optional - for music)
LAVALINK_HOST=localhost
LAVALINK_PORT=2333
LAVALINK_PASSWORD=youshallnotpass
LAVALINK_SECURE=false
```

### How to Get These Values

1. **DISCORD_TOKEN** — Go to [Discord Developer Portal](https://discord.com/developers/applications) → Your App → Bot → Token
2. **CLIENT_ID** — Discord Developer Portal → Your App → General Information → Application ID
3. **CLIENT_SECRET** — Discord Developer Portal → Your App → OAuth2 → Client Secret
4. **OWNER_ID** — Your Discord user ID (enable Developer Mode in Discord, right-click your profile → Copy ID)

---

## Usage

### Bot Commands

The bot supports both prefix commands (`!`) and slash commands (`/`).

| Category | Example Commands |
|----------|-----------------|
| **Security** | `!antinuke`, `!antiraid`, `!lockdown`, `!securitystatus` |
| **Moderation** | `!kick`, `!ban`, `!mute`, `!warn`, `!purge` |
| **Music** | `!play`, `!skip`, `!stop`, `!queue`, `!volume` |
| **Utility** | `!help`, `!ping`, `!serverinfo`, `!userinfo`, `!calc` |
| **Economy** | `!balance`, `!daily`, `!work`, `!shop` |
| **Fun** | `!joke`, `!8ball`, `!ship`, `!meme` |
| **Admin** | `!createchannel`, `!createrole`, `!slowmode` |

### Dashboard

Access the web dashboard at `http://localhost:3000` when the bot is running. Features include:
- Real-time security monitoring
- Guild configuration management
- Embed builder
- Member and channel management

---

## Project Structure

```
x-sentinel/
├── src/
│   ├── commands/           # All bot commands (900+)
│   │   ├── security/       # Anti-nuke, anti-raid, anti-spam, etc.
│   │   ├── moderation/     # Kick, ban, mute, warn
│   │   ├── music/          # Play, skip, queue, filters
│   │   ├── economy/        # Balance, daily, shop
│   │   ├── admin/          # Channel/role management
│   │   ├── utility/        # Help, info, tools
│   │   ├── fun/            # Games, memes, jokes
│   │   └── ...
│   ├── dashboard/          # Web dashboard (Express + EJS)
│   ├── db/                 # Database connection & repositories
│   ├── events/             # Discord event handlers (21 events)
│   ├── handlers/           # Command & event loaders
│   ├── utils/              # Security engine, logger, helpers
│   └── index.js            # Bot entry point
├── web-ui/                 # Next.js marketing website
├── lavalink/               # Lavalink configuration
├── knexfile.js             # Database configuration
├── package.json
└── .env.example
```

---

## Database

SQLite is used by default (auto-created on first run). The bot includes the following tables:

- `guilds` — Per-guild configuration
- `security_logs` — Security event logging
- `security_actions` — Behavioral action records
- `security_incidents` — Incident tracking
- `security_snapshots` — Guild state snapshots
- `security_trust` — Trust scores per user
- `modlogs` — Moderation logs
- `users` — User data (economy/levels)
- `tickets` — Support tickets
- `reaction_roles` — Reaction role assignments
- `welcome` — Welcome/goodbye config
- `automod` — Auto-moderation rules
- `giveaways` — Giveaway system
- `polls` — Poll system

---

## Warning

> **NEVER share your bot token publicly.** If your token is exposed, regenerate it immediately in the [Discord Developer Portal](https://discord.com/developers/applications). A compromised token can give full control of your bot to attackers.

---

## Future Improvements

- [ ] PostgreSQL support for production scaling
- [ ] Redis caching for high-traffic guilds
- [ ] REST API for external integrations
- [ ] Webhook-based logging to external services
- [ ] Multi-language support (i18n)
- [ ] Plugin system for community extensions
- [ ] Rate limiting optimization for large guilds
- [ ] Automated testing suite
- [ ] Docker containerization
- [ ] CI/CD pipeline with GitHub Actions

---

## Author

All code and systems are created by **aarravhacker**.

---

## License

ISC

---

<p align="center">Built with Discord.js v14</p>
