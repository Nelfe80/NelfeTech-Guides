# Venue manager

The Fleet Hub supervises your RetroBat cabinets, identifies players, drives tournaments and screens. **Offline-first**: the hub listens to cabinets, it never commands them — without network or hub, every cabinet keeps working, and the license never turns a cabinet off.

## Install

1. **Buy the license** that fits on [nelfetech.com/salles](https://nelfetech.com/salles.html) — licensing is counted **per equipped cabinet**, hub included.
2. **Install the hub**: a single executable on one machine of the venue's local network.
3. **Activate the key** in the admin console (first entry = activation; then works 14 days without internet).
4. **Enroll your cabinets**: each RetroBat+APIExpose cabinet is added by its local address from the console.

## Player identification

- **Cabinet QR**: enable `CabinetBadgeOverlay` in the cabinet's APIExpose configuration — the check-in QR and cabinet number appear at the bottom-right of the screen, and disappear while a player is checked in. A printable **sticker sheet** exists too.
- The player **scans the cabinet's QR with their phone** (or types the cabinet number) and enters their player code. Re-scan = leaving.
- Create badges at the desk via the players page — anonymous identities, no personal data.

## Venue screens

On each physical display, open `screen.html?name=bar-screen` (one name per display). From the console you choose what **every** screen shows: leaderboard, tournament screen, fleet mosaic… A screen **keeps its content** — podium included — until you change it.

## Online rankings (optional)

Your venue can join the public rankings: the hub signs every score batch (venue-specific key) and pushes them whenever internet is available — never the other way round: gameplay depends on nothing. Enrollment uses the hub's public key (visible in the console); badged players then find their "verified venue" marks on their online account.

## Tournaments

See the [organizer guide](organisateur.md) — and before any event, the golden rule: **check the game's signals, then test round**.
