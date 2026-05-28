# Shinonome Discord Bot

A Python-based Discord bot built with `discord.py`, featuring a virtual economy, casino-style mini games, role-based gameplay, wanted system, and MySQL-backed persistence.

## Features

- Slash command based Discord bot
- User balance, level, EXP, and leaderboard system
- Daily, hourly, beg, rescue, transfer, and red packet economy commands
- Blackjack mini game with interactive Discord UI
- E-card duel mini game
- Role system: civilian, criminal, and police
- Robbery, wanted level, arrest, jail, bail, and bounty-related gameplay
- Good citizen certificate system
- Minecraft-style random death message command
- Admin commands for balance, levels, blacklist, logs, feature toggles, and recovery tools
- MySQL database persistence
- Railway deployment configuration included

## Tech Stack

- Python 3.12
- discord.py 2.3.2
- PyMySQL
- DBUtils
- python-dotenv
- MySQL
- Railway

## Project Structure

```text
.
|-- bot.py
|-- bot_modules/
|   |-- admin_commands.py
|   |-- config.py
|   |-- db.py
|   |-- economy_repo.py
|   |-- game_repo.py
|   |-- rob_repo.py
|   |-- user_repo.py
|   |-- wanted_repo.py
|   |-- commands/
|   |   |-- blackjack.py
|   |   `-- duel.py
|   `-- runtime/
|       `-- events.py
|-- data/
|   |-- minecraft_death_messages_zh_tw.json
|   `-- minecraft_items_zh_tw.json
|-- requirements.txt
|-- railway.toml
`-- README.md
```

## Requirements

- Python 3.12+
- MySQL database
- Discord bot token

## Environment Variables

Create a `.env` file for local development:

```env
DISCORD_TOKEN=your_discord_bot_token
MYSQL_URL=mysql://user:password@host:3306/database
```

Alternatively, the database connection can be configured with separate variables:

```env
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASS=your_password
DB_NAME=discord_bot
```

Railway MySQL variables are also supported:

```env
MYSQLHOST=
MYSQLPORT=
MYSQLUSER=
MYSQLPASSWORD=
MYSQLDATABASE=
```

## Local Setup

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the bot:

```bash
python bot.py
```

## Railway Deployment

This repository includes `railway.toml`.

Railway start command:

```bash
python -u bot.py
```

Deployment steps:

1. Create a Railway project.
2. Connect this GitHub repository.
3. Add a MySQL database service.
4. Set required environment variables, especially `DISCORD_TOKEN`.
5. Deploy the project.

## Main Commands

### General

- `/help` - Show command overview
- `/balance` - View balance and user stats
- `/level` - View level and EXP
- `/leaderboard` - Balance leaderboard
- `/lvleaderboard` - Level leaderboard

### Economy

- `/daily` - Daily reward
- `/hourly` - Hourly reward
- `/beg` - Beg for coins
- `/rescue` - Rescue reward when balance is zero
- `/transfer` - Transfer coins to another user
- `/redpacket` - Send a red packet

### Games

- `/bj` - Blackjack
- `/duel` - E-card duel
- `/casino_stats` - Economy and casino statistics

### Role and Wanted System

- `/role_choose` - Choose a role
- `/rob` - Rob another player
- `/wanted_status` - View your wanted and jail status
- `/wanted_list` - View wanted players
- `/wanted_buyout` - Clear wanted level by paying coins
- `/bail` - Pay bail to leave jail
- `/good_citizen` - Manage good citizen certificate
- `/good_citizen_list` - View users with active certificates
- `/break_citizen` - Break another user's certificate

### Admin

- `/adminhelp` - Show admin command list
- `/give` - Give coins
- `/take` - Deduct coins
- `/setlevel` - Set user level
- `/ban` - Add user to blacklist
- `/unban` - Remove user from blacklist
- `/admin_logs` - View transaction logs
- `/admin_feature_toggle` - Enable or disable features

## Notes

- Do not commit `.env` or any real token/password to GitHub.
- The bot automatically creates and migrates required MySQL tables on startup.
- Some comments or legacy text may contain encoding artifacts, but the Python source can still compile and run.
