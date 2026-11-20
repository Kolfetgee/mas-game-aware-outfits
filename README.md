# MAS Game-Aware Outfits

**Experimental fan-made submod concept for Monika After Story (MAS).**

[Русская версия](README_RU.md) | [Roadmap](docs/ROADMAP.md) | [Development status](docs/STATUS.md) | [Credits and IP](docs/IP_AND_CREDITS.md)

> **Development preview, not a release.** The current prototype is not publicly distributed or recommended for installation. Visual transitions still have a reproducible problem; compatibility and fault recovery are not fully verified.

## The idea

Monika already shares your desktop. What if she could respond naturally when you start or finish a game, without taking over your attention?

**MAS Game-Aware Outfits** explores small, optional, context-aware interactions between Monika After Story and games running on the same computer. The first prototype detects whether *NieR:Automata* is running on Windows. When appropriate, it queues a short MAS dialogue, temporarily changes Monika's outfit to an independently installed 2B spritepack, and attempts to restore her previous appearance after the game closes.

The goal is not to turn MAS into a general-purpose assistant or to pretend that Monika can see gameplay when she cannot. The goal is subtle, believable reactions that respect existing MAS events and the player's choices.

## What exists today

The internal `v0.2.0-dev6` prototype includes:

- Local Windows process detection for `NieRAutomata.exe` (not gameplay inspection).
- Start/exit event handling through the normal MAS event queue.
- A conditional costume switch using a separately installed `hatana_2b` spritepack.
- Session-only tracking intended to preserve and restore a prior outfit and hairstyle, while respecting manual changes.
- Automatically advancing dialogue and an experimental three-expression return sequence.
- No background daemon, game injection, networking, telemetry upload, or screen recording.

These features describe experimental behavior, **not a verified stable release**. On November 20, 2026, the project owner reported successful game detection, clothing changes, and dialogue in a dedicated MAS test installation. However, a short visible sprite flicker persists during the disappearance/return transitions, and the motion still feels unnatural. Other fault scenarios remain unresolved. A recorded test video has not yet been analyzed.

## High-level design

```text
Windows process state
        |
        v
  start/exit detection
        |
        v
MAS event queue and eligibility checks
        |
        v
short dialogue -> hide -> optional outfit change -> show -> follow-up
        |
        v
restore previous appearance after game exit (if still safe)
```

All visual scenes must run in MAS's normal event context. A process-name check must never be presented as knowledge of gameplay, game outcomes, or on-screen activity.

## Where the project is going

1. **Make the existing scenario reliable.** Diagnose flicker using recorded video, refine timing, maintain normal MAS event compatibility, and address recovery and manual-override edge cases.
2. **Make interactions configurable.** Explore a small, documented event-rule interface for additional games and outfits, only after the core behavior is reliable.
3. **Make reactions less intrusive.** Support context-sensitive expressions, brief comments, and intentional silence.
4. **Explore optional local observation.** Any richer game-event awareness would require explicit, revocable user consent, limited sources, confidence-aware signals, and privacy-first defaults. It does **not** exist in this prototype.
5. **Research long-term context.** Optional context or memory is a distant research direction, not a promise or a claim of machine consciousness.

See [the roadmap](docs/ROADMAP.md) for boundaries and non-goals.

## Requirements and availability

The current experimental work targets Windows and the owner's MAS 0.12.20 development build using Ren'Py 6.99 / Python 2.7. It depends on a working installation of MAS and the appropriate third-party outfit spritepack. These dependencies and their assets are **not bundled** here.

There are **no public releases or supported installation instructions** yet. Do not treat a development snapshot as stable or modify your main MAS installation based on this documentation.

## Privacy and design principles

- React only to signals actually observed; treat missing or unreliable signals as unknown.
- Never guess ownership of an outfit after a restart.
- Keep user-selected clothing and hair above automatic changes.
- Never interrupt an active MAS event to force a costume scene.
- Do not capture screens, record gameplay, or send data externally without a separate explicit opt-in design and implementation.
- Silence is a valid response; a notification is not always the best interaction.

## Unofficial fan work and credits

This is an independent, non-commercial fan project and is **not affiliated with, sponsored, or endorsed by Team Salvato, the Monika After Story team, Square Enix, or PlatinumGames**. All respective characters, games, trademarks, and third-party outfit assets belong to their owners.

Please play and complete the original [Doki Doki Literature Club](https://ddlc.moe/) before using DDLC fan-made mods. The submod requires an independently obtained MAS installation; it does not replace or distribute the original game.

No official DDLC/MAS artwork, dialogue, music, game files, 2B spritepack artwork, or other third-party assets are supplied in this repository. See [credits and IP considerations](docs/IP_AND_CREDITS.md) and the current [Team Salvato IP Guidelines](https://teamsalvato.com/ip-guidelines).

## Project status, source, and contributions

This repository currently documents an **unreleased prototype and its direction**. The experimental source has not been approved for public redistribution; in particular, any in-character dialogue must be reviewed for compliance with the current Team Salvato guidance on generative AI.

Issues and design feedback may be welcome as development resumes, but this is not a feature-complete public release. No open-source license is granted here until a license for original, redistributable project code is selected; third-party rights are never covered by such a license.

Maintained by **Kolfetgee**.
