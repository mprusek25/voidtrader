# 🪐 Void Trader
> **Play now → [daxiceek.tech](https://daxiceek.tech/)**

A vector-graphics space trading and combat game set in a procedurally generated galaxy. Navigate star systems, manage supply and demand, run delivery contracts, dogfight pirates, and survive the void — all in your browser with no install required.

## 🎮 Gameplay
You pilot a lone ship in a seeded galaxy of infinite stations. The map is procedurally generated from a unique seed — deterministic and persistent between sessions via `localStorage`.

**The core loop:**
1. **Explore** open space until you discover a station (radar range: 6,000 ls)
2. **Dock** — align with a docking pad and slow below 20 ls/s, then press `E`
3. **Trade** — buy commodities cheap, sell them where they're scarce
4. **Take a contract** — accept a delivery job from the contract board at the docked station
5. **Deliver** — fly to the destination station; collect your reward on docking
6. **Repeat** — spend credits on fuel, hull repairs, and a shield module

**Distance is real.** 1 game unit = 1 light-second. The HUD shows coordinates in `ls` / `kls` / `ly` dynamically. Inter-system travel takes time — use **COSMIC mode** to cruise at up to 1,200 ls/s, then switch to **MANEUVERING mode** for precise docking.

**Survival checklist:**
- Keep fuel above 0 — or broadcast a distress beacon (pirates respond too)
- Repair hull damage at any station
- Install an energy shield (`5,000 CR`) and activate it with `Q` in dangerous zones

## 🕹️ Controls
| Key | Action |
|-----|--------|
| `W` | Main thruster |
| `S` | Emergency brake |
| `A` / `D` | Rotate ship |
| `SPACE` | Fire laser |
| `E` | Dock at nearest pad |
| `Q` | Toggle energy shield |
| `J` | Open Hyperdrive menu |
| `M` | Toggle stellar map |
| `H` | Hide / show controls overlay |
| `ESC` | Pause menu |
| `Arrow keys` | Alternative thrust / rotate |
| `1` | Switch to MANEUVERING mode |
| `2` | Switch to COSMIC mode |

## ⚙️ Features
### 🚀 Flight & Speed Modes
Two distinct flight modes switchable on the fly:

| Mode | Max Speed | Thrust | Rotation | Cruise Floor |
|------|-----------|--------|----------|--------------|
| **MANEUVERING** | 320 ls/s | 520 | 3.4 rad/s | none |
| **COSMIC** | 1,200 ls/s | 420 | 2.0 rad/s | 380 ls/s |

Maneuvering mode is for docking, combat and precise flying. Cosmic mode for long-distance cruising. A **trajectory warning system** alerts you if your current heading puts you on a collision course within 1,800 ls.

### ⚡ Hyperdrive
Press `J` to open the Hyperdrive menu. Select any **previously discovered** station and jump directly to it — costs ⅔ of your max fuel. A wormhole animation plays on entry and exit. You spawn within 900 ls of the target at zero velocity.

### 🛒 Trading & Economy
Six commodities, each with independent buy/sell prices per station:

| Commodity | Base Buy Price |
|-----------|---------------|
| FUEL | 12 CR/u |
| ORE | 45 CR/u |
| FOOD | 8 CR/u |
| MEDS | 90 CR/u |
| PARTS | 130 CR/u |
| TECH | 220 CR/u |

Sell price = 80% of buy price. Buy out a station's stock and prices rise as it regenerates over real time.

### 📋 Contract System
Every station generates 2–4 delivery contracts. Accept a job, buy the required cargo, then fly to the destination station and dock to collect your reward.

Reward scales with distance and cargo quantity:
```
reward = distance × 0.04 + qty × 30 + random(0–1000)
```

### 🔫 Laser Combat
- **Fire rate:** 0.18 s cooldown per shot
- **Range:** 700 ls
- **Damage:** 35 HP per hit
- **Heat:** each shot adds 14 heat — reach 100% and the cannon locks for **2.2 seconds**
- **Energy:** each shot costs 6 energy (regens at 14/s)
- Pirates respect **safe zones** (1,500 ls radius) around stations — combat only happens in open space

### 🛡️ Energy Shield
Purchase at any station for 5,000 CR. Toggle with `Q`. Blocks laser hits, meteor impacts and swarm rocks while active. Drains 35 energy/s — go offline when energy is low.

### 🪐 Stations & Orbiting Bodies
Non-home stations are procedurally placed in chunks (8,000 ls apart). Each orbiting station has:
- A **central star** with a glowing halo
- The **station structure** (4 radial arms, hexagonal core, 4 docking pads) orbiting the star
- A small **planet body** visible beneath the structure

Stations are hidden until you enter their 6,000 ls radar radius.

### 🌌 Stellar Map
Press `M` (or tap MAP on mobile) for a zoomable overhead map. Shows:
- Discovered stations (square blips)
- Enemies (triangle blips)
- Cargo drops (diamond blips)
- Active contract destination (highlighted)
- Black holes (circle blips)
- Your ship (centre arrow)

Scroll to zoom. Press `M` again to close.

### ☄️ Meteors
Occasional lone rocks drift through open space (spawns 1–2 every 18–40 s, max 3 active). Collision deals damage proportional to rock size and splits it into fragments. Use shield or evade.

### 💥 Asteroid Swarms
Rare high-velocity rock formations. A **5-second warning** appears on screen with approach direction arrows. Activate shield or change heading to evade. Rocks deal up to 40+ HP on impact.

### 🕳️ Black Holes
Gravitational singularities with a 600 ls pull radius and a 180 ls event horizon. Getting too close pulls your ship in. Crossing the event horizon **teleports** you to a random location with critical hull and fuel damage.

### 🆘 Distress System
Run out of fuel? A distress modal appears after 3 seconds. Options:
- **Send beacon** — rescue spawns you near a discovered station with 25 fuel (pirates may follow within ~3 s)
- **Drift** — do nothing and hope

### 🚢 Stranded Ships
Random merchant vessels appear in open space with a pulsing SOS ring. Approach and choose:
- **Deliver Parts** (requires 5× PARTS in cargo) → +1,500 CR, +5 karma
- **Escort to station** → follow them to any station → +2,000 CR, +2 karma, scales with karma
- **Loot** → drops random cargo → −10 karma

### ⚔️ Boss Fight (Alien Presence)
Bounty stations have a **★ BOUNTY BOARD**. Pay 2,000 CR to accept — triggers an alien boss:
- **600 HP**, 3 phases (behaviour escalates as HP drops)
- Phase 1: 1 projectile per 1.8 s
- Phase 2: 2 projectiles per 1.2 s
- Phase 3: 3 projectiles per 0.6 s, 60% speed boost
- **Kill reward: 15,000 CR**

Alien tech fragments drop on kill and can be sold at bounty stations.

### ⚖️ Karma System
Tracks moral choices. Displayed in the ship HUD. Affects escort payouts and future dialogue. Helping raises karma; attacking stranded ships or looting lowers it.

### 💀 Death & Respawn
On death, 25% of your cargo is jettisoned as retrievable signal drops in space. You respawn at HOME STATION with 50% hull and 60% fuel. The active contract is cancelled.

### 💾 Save System
- Auto-saves every 30 seconds
- Manual save via **ESC → Save & Quit**
- Saves ship position, velocity, credits, cargo, hull, fuel, shield, kills, karma, seed, and all discovered stations
- Seed is stored separately — your galaxy persists across sessions


## 👥 Created by
| Name | Role |
|------|------|
| **daxiceek** | Main Scripter, Legend |
| **qnazdarek** | Legend of Ideas, Scripter |
| **pavliqqqqqq** | Master of Ideas, Main Scripter |

## 📦 Credits
- AI assistance: **Gemini & Claude AI**

## 🛠️ Built With
- HTML
- CSS
- JavaScript

*This game was made with love, blood, sweat and an ungodly number of hours of hard work.*
