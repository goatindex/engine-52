# Engine 52

*A multi-team game engine built on standard 52-card decks divided by suit, with within-session destructive modification — legacy at session speed, on components you can destroy without guilt and replace at any corner shop.*

## Project documents

- **[Pattern Language](../../wiki/Pattern-Language)** — the normative design system (v0.1): 25 patterns across three scales, network map, generative sequence, evolution protocol (Appendix B), and Evidence Register (Appendix C).
- **[Design Analysis](../../wiki/Design-Analysis)** — the founding analysis: design-space location, comparable games, novelty assessment, strengths, gaps, known dilemmas, and the original 20 design questions (§7) that the patterns tease out.
- **[Annotated Bibliography](../../wiki/Annotated-Bibliography)** — the single source of truth for references and precedents. Citation keys here are used by the pattern language's Evidence Register. New references enter here first.
## Worked games

Games built on the engine live under [worked-games/](worked-games/), one folder per setting, each with its own `mvp/` and `playtests/`. Worked examples are the mines the pattern language is refined from (Appendix B protocol).

- **[space-salvagers](worked-games/space-salvagers/)** — *Salvage Run* v0.1: boxed register, gated shared goal, punch-heavy economy, hidden scores. [Prototype](worked-games/space-salvagers/mvp/minimum-prototype.md) · [reference card](worked-games/space-salvagers/mvp/reference-card.md).
- **[haunted-hospitals](worked-games/haunted-hospitals/)** — *Spirit Ward* v0.1: facilitated register (one Control player), ghost pandemic as public health. The only test of BACKS THAT WHISPER Resolution B. [Prototype](worked-games/haunted-hospitals/mvp/minimum-prototype.md) · [reference card](worked-games/haunted-hospitals/mvp/reference-card.md).
- **[wasteland-racing](worked-games/wasteland-racing/)** — *Scrap Circuit* v0.1: post-apocalyptic race league. Deliberate stress test: no gate, public scoreboard, spend-heavy shrinking hands. [Prototype](worked-games/wasteland-racing/mvp/minimum-prototype.md) · [reference card](worked-games/wasteland-racing/mvp/reference-card.md).

### Playtest coverage matrix

The three prototypes deliberately spread the engine's variables so playtest data triangulates the whole pattern language:

| Axis | Salvage Run | Spirit Ward | Scrap Circuit |
|---|---|---|---|
| Register (P1) | boxed | facilitated (Control) | boxed, convention pace |
| Shared tier (P4) | hard gate | dominant gate, public track | weighted commons, **no gate** |
| Leader legibility (P6) | hidden SP | public shared / hidden standing | **fully public** (stress test) |
| Lifecycle mix (P9) | return-marked heavy | sticker/status heavy | **spend-heavy, shrinking arc** |
| Travel volume (P12) | low, Broker-gated | high, Control-mandated | medium, poaching |
| Backs (P19) | A: faces only | **B: ghost sigils on backs** | A under load (face-down commits; punch-leak finding) |
| Scars as powers (P20) | sell bonus, Deep Sites | drained ♥ double in rites | full rank + Fame in races |
| Ink (P17) | free tags | Control-applied | **closed word list** |
| Jokers (P23) | earned wildcards | Control injects | comeback rewards |
| Shrinkage (P14) | mild | minimal (texture not loss) | **designed arc + floor rule** |

## How the pieces relate

The **Design Analysis** raised the questions; the **Pattern Language** answers them normatively (Appendix A in the pattern language maps each §7 question to its patterns); the **Bibliography** carries the evidence both lean on. Worked examples, when built, will cite the pattern-language version they were designed against and feed playtest evidence back into the stars (Appendix B protocol).

## Status

- Pattern Language: **v0.1** — mostly hypothesis-stage (see star confidence marks); first evidence-gathering act is the minimum prototype (one team, three systems, three marks, six turns).
- Worked examples: none yet. Planned: salvage-crews (tabletop register), pandemic-hospitals (larp/megagame register).

## Conventions

- Pattern names in SMALL CAPS style refer to the Pattern Language by number, e.g. CLOSED MARK GRAMMAR (16).
- Citation keys in [brackets] refer to the Annotated Bibliography.
- v0.x pattern names are cheap to change; from v1.0 renames require deprecation notes.
