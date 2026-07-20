# Venue manager

The Fleet Hub supervises your RetroBat cabinets, identifies players, drives tournaments and screens. **Offline-first**: the hub listens to cabinets, it never commands them — without network or hub, every cabinet keeps working, and the license never turns a cabinet off.

## Install

1. **Buy the license** that fits on [nelfetech.com/salles](https://nelfetech.com/salles.html) — licensing is counted **per equipped cabinet**, hub included.
2. **Install the hub** on one machine of the venue's local network (the front-desk PC is fine): unzip the release — like APIExpose, everything ships as **a single executable at the root**, `RetroBat.Hub.exe`, with its `wwwroot` folder next to it.
3. **Double-click `RetroBat.Hub.exe`**, then open **http://localhost:12400** in a browser: that's the venue console (My venue, Players, tournaments, leaderboard, Settings). All configuration and venue state live next to the exe (`appsettings.json`, the `state\` folder — back that folder up, it holds your scores, license and keys). The optional Windows installer adds auto-start with the session.
4. **Activate the key** in Settings (first entry = activation; then works 14 days without internet).
5. **Enroll your cabinets**: use the "🔍 Discover cabinets" button in Settings (the hub scans the local network), or type the cabinet address `http://cabinet-IP:12345`. Restart the hub to connect them.

In **My venue**, the ✏️ pencil next to a cabinet's name **renames** it ("Bar bartop", "Cockpit"…) — the name is immediate and kept. The **Quit the game** button cleanly closes the running game, whether it runs under RetroArch **or** a standalone emulator (MAME, PCSX2…).

## Player identification

- **Cabinet QR**: enable `CabinetBadgeOverlay` in the cabinet's APIExpose configuration — the check-in QR and cabinet number appear at the bottom-right of the screen, and disappear while a player is checked in. A printable **sticker sheet** exists too.
- The player **scans the cabinet's QR with their phone** (or types the cabinet number) and enters their player code. Re-scan = leaving.
- Create badges at the desk via the players page — anonymous identities, no personal data.

## Venue screens

On each physical display, open `screen.html?name=bar-screen` (one name per display). From the console you choose what **every** screen shows: leaderboard, tournament screen, fleet mosaic… A screen **keeps its content** — podium included — until you change it.

!!! tip "Announcing a player"
    Route a screen to a player's **public card** (`…/retrocreator/card/TheirPseudo`): avatar, honors and top 3 show up big — perfect to present a champion or invite a player to a cabinet.

## Online rankings (optional)

Your venue can join the public rankings: the hub signs every score batch (venue-specific key) and pushes them whenever internet is available — never the other way round: gameplay depends on nothing. Enrollment uses the hub's public key (visible in the console); badged players then find their "verified venue" marks on their online account.

**Fill in your venue's profile** (city, region, country, chain) at enrollment: it is what places your players in the rankings at every scale — champions of the venue, the city, the chain, the region, the country and the world.

## Roles and moderation

On the online platform, a venue can delegate scoped **roles** to NelfeTech accounts:

- **owner** — all rights on the venue;
- **moderator** — can **hide an inappropriate nickname** on public rankings (it then shows `##;-)##`);
- **organizer** — **announces events** to players who follow the venue (never a command to the cabinets).

The matching tools appear in the **Config** tab of that account. (Roles are assigned platform-side.)

## Tournaments

See the [organizer guide](organisateur.md) — and before any event, the golden rule: **check the game's signals, then test round**.
