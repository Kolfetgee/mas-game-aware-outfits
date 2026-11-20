# Roadmap — MAS Game-Aware Outfits

Roadmap items are research and engineering directions, **not commitments or release dates**. The current internal experiment is `v0.2.0-dev6`; no release has been approved.

## Stage A — Stable NieR prototype (current priority)

- Analyze the owner's recorded test video and reproduce the remaining disappearing/returning flicker (V-01).
- Make outfit transitions and the post-return dialogue feel natural (UX-01).
- Keep the existing MAS event queue and idle behavior intact.
- Handle known edge cases: repeated failed restores (F-01), deferred hairstyle recovery (F-02), process-detection errors vs. manual outfit changes (F-03), and interrupted dialogue/scene cleanup (S-01).
- Re-test in the actual target Ren'Py/MAS build, not only static mocks.
- Produce a safe rollback and minimal installation procedure before any public build.

## Stage B — Extensible local game rules (not implemented)

- Define an explicit per-game process/scene rule format.
- Separate game recognition, outfit selection, and dialogue choreography.
- Make rules optional and easy to disable or remove.
- Consider additional games only after reliability is established.

## Stage C — Event-reactive interactions (research)

- Prefer short reactions, expressions, or silence over frequent interruptions.
- Track only credible event signals; never infer a victory, defeat, or other activity from the game executable being open.
- Investigate a minimal local observer with clear user controls and consent.

## Stage D — Optional richer context (long-term research)

- Explore local-only, user-approved signals such as selected window or explicit game events.
- Evaluate privacy-preserving context and memory separately; neither is part of current code.
- Avoid unsupported claims that the character has consciousness or unrestricted perception.

## Explicit non-goals for the current prototype

- No general-purpose assistant or MAI/LLM integration.
- No OS service/daemon, network reporting, or gameplay injection.
- No screen, microphone, or camera capture.
- No official game art or third-party spritepack redistribution.
- No public stable release until visual, recovery, compatibility, and IP requirements are met.
