# Development status — 2026-11-20

**Overall:** Experimental. `v0.2.0-dev6` is an internal test candidate, not an accepted release.

| Area | Evidence / status |
| --- | --- |
| Local process detection | Owner reports successful detection of NieR:Automata on Windows |
| Outfit switching and return | Owner reports the normal start/exit scenario worked in a MAS test clone |
| Additional dialogue | Owner confirms the dev6 lines were spoken |
| Visual disappearance/return | **Known visual failure**: brief sprite flicker still appears (V-01) |
| Natural timing/expressions | **Not accepted**: needs UX refinement (UX-01) |
| Automated unit tests | Maker 93/93 pass; independent Checker 33/33 pass in a simulated Python 3 environment |
| Real Ren'Py SDK probe | Owner reports pass, but full terminal evidence is not attached |
| GUI reproducibility | Limited owner smoke tests; video recorded but not reviewed |
| Release approval | **None** |

## Known open engineering issues

- **V-01:** visual sprite flicker during both leave and return transitions.
- **UX-01:** overly abrupt movement and post-transition pacing.
- **F-01:** repeated empty-desk scene after persistent restore failure.
- **F-02:** deferred hairstyle recovery can hold up a subsequent game-start event.
- **F-03:** process-detection errors can interact with manual outfit selection.
- **S-01:** interrupted dialogue may leave scene activity state inconsistent.

## Evidence boundary

Unit tests and display-list mocks cannot prove that Ren'Py renders clean animation frames. Owner observations are useful validation but are not a substitute for independent video/frame and crash-recovery testing.

The next authorized engineering discussion is analysis of the existing video and a narrow corrective plan. Public runtime code distribution remains pending an explicit readiness review and third-party IP compliance check.
