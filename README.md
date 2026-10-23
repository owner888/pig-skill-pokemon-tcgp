# Pokémon TCG Pocket Automation Skill for pig

An autonomous agent skill for **Pokémon TCG Pocket** (`jp.pokemon.pokemontcgp`) powered by [pig](https://pigagent.dev).

Built on a two-tier architecture:
- **System 1 (Jev Fast-Loop)**: Sub-100ms state polling and transition detection in pure PHP, avoiding costly multimodal roundtrips for routine animation waits.
- **System 2 (Multimodal LLM)**: Strategic card play, energy attachment, bench placement, and tactical battle decisions.

---

## Capabilities

### Mode 1: Daily Automation
- **Free Booster Packs**: Automatically claims 12h/24h free booster packs with swipe-to-rip gesture and full card reveals.
- **Wonder Pick (得卡挑战)**: Detects free picks or low-stamina picks, handles shuffle animations, and selects cards.
- **Daily Missions & Store**: One-click claim for daily mission badges and free shop items.

### Mode 2: PVE Solo Battle
- **Pre-battle Setup**: Automatically deploys active and benched Basic Pokémon.
- **Turn Priority Loop**:
  1. Attach Energy from Energy Zone to Active/Bench attacker.
  2. Bench Basic Pokémon & evolve active/bench Pokémon.
  3. Play Trainer / Item cards (Professor's Research, Poké Ball, Potion).
  4. Execute attack when energy cost is fulfilled.
  5. Pass turn (`End Turn`).
- **Promotion Handling**: Promotes optimal benched Pokémon when the active Pokémon is knocked out.
- **Victory Loop**: Skips victory/defeat rewards and loops back to solo stage selection.

---

## Installation

Install directly into your global `pig` agent environment:

```bash
pig install https://github.com/owner888/pig-skill-pokemon-tcgp.git
```

Or install locally for the current project:

```bash
pig install -l https://github.com/owner888/pig-skill-pokemon-tcgp.git
```

To verify installation in pig:

```text
/skills
```

You should see `pokemon-tcgp` listed under installed package skills.

---

## Usage

Connect your Android device via USB (or Wi-Fi debugging via `/android connect <ip:port>`), then simply instruct pig:

```text
"帮我跑一下宝可梦 TCGP 的日常，把免费卡包和得卡挑战领了"
```

or for PVE battles:

```text
"帮我用 pokemon-tcgp 技能挂机刷几局单人对战"
```

---

## License

MIT
