---
description: Repository Information Overview
alwaysApply: true
---

# Arma Bot Information

## Summary
Arma Bot is a Discord bot designed to complement the TrustyAdminTools mod for Arma Reforger servers. It receives webhook events from Arma servers, providing real-time monitoring, administration capabilities, and player tracking in Discord. The bot integrates with BattleEye RCON for server administration and supports multiple server configurations.

## Structure
```
arma-bot/
├── src/
│   └── index.js              # Main bot application (1168 lines)
├── .env.example              # Environment variables template
├── servers.json.example      # Server configuration template
├── package.json              # Project dependencies and scripts
├── README.md                 # Project documentation
└── .gitignore               # Git ignore rules
```

## Language & Runtime
**Language**: JavaScript (Node.js)  
**Version**: Node.js >= 16.9.0  
**Package Manager**: npm

## Dependencies

**Main Dependencies**:
- **discord.js** (^14.18.0) - Discord API client library
- **express** (^4.18.2) - Web framework for webhook server
- **axios** (^1.6.7) - HTTP client for API requests
- **dotenv** (^16.5.0) - Environment variable management
- **buffer-crc32** (^0.2.13) - CRC32 checksum calculation

**Development Dependencies**:
- **nodemon** (^3.0.3) - Auto-restart on file changes

## Build & Installation

**Install dependencies**:
```bash
npm install
```

**Environment setup**:
```bash
cp .env.example .env
# Edit .env with Discord token, channel IDs, and server configuration
```

**Server configuration**:
```bash
cp servers.json.example servers.json
# Edit servers.json with Arma server addresses, ports, and RCON passwords
```

## Main Files & Entry Points

**Application Entry**: `src/index.js` - Main bot application containing:
- Discord client initialization with gateway intents
- Express webhook server (listens on `SERVER_PORT` and `SERVER_IP`)
- Webhook endpoint at `/webhook` for handling Arma server events
- Slash command handlers (playerlist, banlist, kick, ban, chatglobal, server management, etc.)
- RCON integration for server administration
- Event handlers for Discord interactions

**Configuration Files**:
- `.env` - Discord token, chat/alert channel IDs, guild ID, webhook server settings
- `servers.json` - Multi-server configuration (address, port, RCON password, active server selection)

## Usage

**Start the bot**:
```bash
npm start
```

**Development mode with auto-reload**:
```bash
npm run dev
```

**Key Features**:
- Real-time player count status updates
- Webhook server for receiving TrustyAdminTools events
- Slash commands for player management, bans, kicks, and chat
- Message commands (e.g., `!status6` for server status)
- Teamkill detection and reporting
- Server event logging to Discord
- Multi-server support with easy switching
