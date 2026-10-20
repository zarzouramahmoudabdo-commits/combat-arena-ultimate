# Combat Arena Ultimate — prototype 0.4

Original 2D shooter prototype built from scratch for mobile browsers and future Android packaging.

## Currently implemented
- Canvas-based side-scrolling arena and multiple platforms.
- Touch buttons and keyboard controls.
- Infinite ammunition and unlimited jetpack thrust.
- Three weapon types and pickups (rifle, shotgun, energy blaster, health).
- AI enemies, enemy projectiles, health, score, kills, death and respawn.
- Pause/resume and restart.

## Controls
- Desktop: A/D or arrows to move; Space/Up/W to fly; J/Enter to fire; Q to switch weapon.
- Mobile: use on-screen movement, fly, fire, and switch buttons.

## Run locally
Requires Node.js 20+.

```bash
npm install
npm run build
```

For a local browser development server:

```bash
npm run start
```

## Android
Push to GitHub and open Actions. The workflow builds a debug APK artifact. Test on a real phone before distributing.

## Not implemented yet
Actual local Wi-Fi multiplayer, online matchmaking, team mode, bot navigation across platforms, final art/audio, and release signing. These require separate implementation and real-device testing. This prototype is not yet a complete Mini Militia-scale game.


## Version 0.2 gameplay additions
- Three selectable maps: Military Base, Jungle Outpost, and Secret Lab.
- Four weapons: assault rifle, shotgun, energy blaster, and heavy machine gun.
- Grenades with bounce, fuse, explosion damage, and knockback effects.
- Infinite ammunition and continuous jetpack thrust remain enabled.
- Weapon, health, and grenade pickups with respawning.
- Map selection from the game header.

## Current limitations
- Local Wi-Fi multiplayer is not implemented yet.
- The current opponents are basic local AI, not networked players.
- Test gameplay and Android packaging on real devices before distribution.


## Version 0.3 additions
- Expanded arsenal to 10 weapons: assault rifle, shotgun, energy blaster, heavy machine gun, sniper rifle, burst rifle, flame caster, plasma cannon, dual pistols, and railgun.
- Four throwable types: fragmentation grenade, smoke grenade, tear-gas grenade, and sticky grenade. Use **G** to throw and **T** to cycle types (or the touch buttons).
- Armor pickups reduce incoming damage and are shown as a blue shield outline. Health and armor pickups respawn.
- Added generated Web Audio weapon reports, impact/throw/explosion sounds, and a death sound. These are synthesized effects, not recordings of real firearms; licensed recorded sound assets would be needed for authentic recordings.
- Smoke and tear-gas clouds linger in the arena; tear gas damages characters in the cloud. Sticky grenades attach to enemies.

## Testing note
The JavaScript syntax and ZIP integrity are checked, but this version has not yet been fully play-tested in a browser or built into an Android APK. Sounds require a user gesture to unlock audio on mobile browsers.


## Version 0.4 additions
- Added Classic and Survival Waves modes; survival advances in waves after eliminations and adds enemies as difficulty increases.
- Added Easy, Normal, and Hard difficulty options with different enemy durability and incoming damage/fire cadence.
- Added persistent local profile via browser storage: XP, level, credits, lifetime eliminations, and best score. Each elimination grants XP/credits; leveling grants a bonus.
- Added sound mute toggle, profile stats on the start screen, and wave/level HUD.
- Improved sticky grenade attachment tracking, hit/death rewards, and screen-shake feedback.
- The three maps and ten weapons remain available, with armor, pickups, and grenade types.

## Multiplayer status (honest limitation)
This version still does **not** contain phone-to-phone Wi-Fi or internet multiplayer. It remains a single-player offline game against AI. A real multiplayer release needs a networking/signaling layer, player synchronization, lobby/room UI, disconnect handling, and tests on two physical devices; no fake multiplayer button is presented as working.

## Test status
`node --check www/js/game.js` passed. The ZIP is checked separately. A full Vite production build and Android APK build are not claimed unless they successfully run in this environment.


## v0.5 — experimental peer-to-peer co-op
- Added a WebRTC data channel for direct peer-to-peer player state and shot-event exchange.
- Manual offer/answer exchange is used for signaling; no matchmaking or signaling server is bundled.
- Both players must open the same build and complete the exchange using the 🌐 جماعي panel. Host creates an offer and sends it to the guest; guest pastes it and joins, then sends the generated answer back; host pastes the answer and applies it.
- A public STUN service is configured to help establish connections. Network/firewall/NAT restrictions may prevent connections. This is experimental co-op and has not been validated on two physical phones in this environment. Game simulation and enemy state are still local on each device; it is not authoritative competitive multiplayer.
- This version's profile key changed to v0.5 to avoid silently overwriting prior version data.
