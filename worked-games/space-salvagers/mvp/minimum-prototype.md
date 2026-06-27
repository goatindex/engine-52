# Salvage Run — Minimum Prototype

*v0.1 — the first evidence-gathering instrument for the Engine 52 pattern language. Two crews, one wreck, six turns. Built against Pattern Language v0.1.*

> **v0.2 playtest note (2026-06-27).** A five-run synthetic playtest validated two balance
> changes worth promoting into the next revision: **cap selling at one per crew member per
> turn**, and **expose three sites per turn** (not two) to stop the first one or two seats
> claiming everything. Two structural lessons also landed: reactor *tension lives at the
> mid-game Tremor*, not the Final Collapse (end-game cards are worthless, so the Final is
> always over-fed); and the *cross-crew economy needs a reciprocal mechanic* — a one-way
> price drew zero trades because aiding a rival is never worth it. Full record:
> `../playtests/2026-06-27-harness-tier3-report.md`.

---

## What this document is

This is not the salvage-crews worked example. It is the **minimum two-team prototype**: the smallest playable thing that exercises the engine's untested hypotheses — the inter-team economy, card travel and provenance, the three-tier goal tension, and torn-half contracts. The setting is a deliberately thin skin; the numbers are first guesses and are flagged for tuning. Every rule cites the pattern it instantiates, so playtest results feed straight back into the language's Evidence Register.

**Register:** boxed tabletop — zero adjudication bandwidth, every rule self-enforcing (Pattern 1).
**Players:** 6–8, as two crews of 3–4. **Time:** ~90 minutes. **Table:** any table plus a score pad.

## The story, in one paragraph

A derelict megafreighter has broken orbit and is coming apart. Two rival salvage crews have docked. Twelve salvage sites will be exposed as the wreck shears open — but the reactor is failing, and if it breaches while anyone is aboard, nobody collects. Strip the wreck, outbid your rivals, and keep the reactor stable enough to get out alive.

## Components (the Facilitator's Kit — Pattern 25)

Per crew:
- 1 standard 52-card deck — **the two crews' decks must have different back colours** (provenance, Pattern 12)
- 1 single-hole punch
- 1 sheet of small round stickers
- 1 fine-tipped permanent marker

Shared:
- this rules document, including the Site Schedule
- a score pad and pencil
- *(no-tear / no-punch variant, Pattern 24: square stickers stand in for punches, a sticker cut diagonally stands in for a tear; mechanically identical)*

A missing tool is a missing rule. Do not start without the punches and stickers.

## Setup

1. **Decks.** Each crew takes one deck, removes the two jokers, and sets them aside face up — they are not part of the economy (Pattern 23).
2. **Suits as roles (Pattern 7).** Each crew member takes one full suit, 13 cards:

   | Suit | Role | What the role does |
   |---|---|---|
   | ♠ Spades | **Breaker** | force: cuts open sealed sites |
   | ♣ Clubs | **Wrench** | engineering: extraction and the reactor |
   | ♥ Hearts | **Medic** | crew: clears mishaps, keeps people working |
   | ♦ Diamonds | **Broker** | finance: trade, contracts, the only cross-crew voice |

   *Three-player crew:* one player takes both ♠ and ♦ (Breaker-Broker). Both crews must use the same arrangement.

   > *Design note (ROLES THAT PLAY DIFFERENTLY, candidate pattern 30).* The Broker currently bundles two kinds of decision: **planning** (look-ahead, lending facilitation, recall) and **logistics** (trade, the feeder/market, converting depletion into supply). If this game grows past the MVP, split it: a **Planner** seat that operates on THE ASSIST (28) and the recovery piles, and a **Logistician** seat that works the market and owns de-escalation on the spend-destination ladder (27). Most crews want one or the other, set by whether the pressure is planning or supply — not both in one seat. The MVP keeps them fused because at six turns and one cross-crew voice the split would cost more teach than it earns; this is a deliberate Scale-0 compression, not an oversight.
3. **Turn-zero swap (Pattern 8).** Each role has a band it collects: **Breaker — face cards (J Q K); Wrench — ranks 2–5; Medic — ranks 6–10; Broker — Aces.** Before turn one, each player gives each teammate one card from *that teammate's* band (you choose which). Every pair of teammates transacts exactly once. Hands end at 13 cards, visibly shaped by role: the Breaker bristles with face cards, the Wrench holds the low grist.
4. **Secret goals.** Each player secretly chooses one individual goal from the list for their role (see Goals) and writes its number hidden on the score pad fold.
5. Put the Site Schedule where both crews can read it. Choose a start crew by any fair method.

## Goals — three tiers (Patterns 4, 5, 6)

- **Shared (gated):** the reactor must survive the Final Collapse at the end of turn 6. **If it does not, nobody wins** — the lower tiers only count if the shared goal is met.
- **Crew:** most Salvage Points (SP) wins. SP totals are kept **hidden** — each crew tracks its own column on a folded score pad, revealed at the end (no public competitive track, Pattern 6).
- **Individual (secret, worth 5 SP to your crew *and* the MVP title if met):

  | Role | Choose one |
  |---|---|
  | Breaker | (B1) End the game holding 3+ face cards. (B2) Personally commit the single highest-rank card to a crisis. |
  | Wrench | (W1) End with 3+ punched cards in your own hand. (W2) Be the player who commits the final card that meets a crisis threshold. |
  | Medic | (M1) Clear 3+ seals during the game. (M2) End the game with no sealed cards anywhere in your crew. |
  | Broker | (K1) End with 3+ cards of the *other crew's* back colour in your crew's hands. (K2) Hold both halves of an executed contract at game end. |

## The card lifecycle sentence (Pattern 9)

> **In this game, working a salvage site returns the card punched; feeding the reactor spends the card forever; trades and payments send the card to the other crew.**

Every system below states which verb it uses. An **unmarked card is a coin; a marked card is an object** (Pattern 13) — systems say which they accept.

## The mark grammar (Patterns 16, 17)

Three player-applied marks, fixed meanings, all marks on **faces only — backs are never marked** (Pattern 19, Resolution A: a hard rule).

| Mark | Name | Meaning (invariant) |
|---|---|---|
| **Punch** | *stress* | Permanent capability change: this card is **Worn**. A Worn card counts **half rank (round up)** at salvage sites, but gains value elsewhere (see Scars as Powers). |
| **Sticker** | *seal* | Removable status: this card is jammed in the wreck. A sealed card cannot be played for any purpose until a Medic clears it. |
| **Ink** | *tag* | Information only: words that tell, never do. When you extract at a site, tag one committed card with the site's name. Tags never change a card's function. |

**Witnessed marking (Pattern 18):** announce, then mark, in view of the table. An unannounced mark is void.

**Terminal form (Pattern 21):** a card carries at most **three marks**. At its third mark it becomes a **Relic**: name it aloud and tag it with that name. A Relic can no longer be played at sites or sold — but it counts **double rank** at a crisis, where it is spent with ceremony.

**Scars as powers (Pattern 20):** Worn cards count half at sites, but the Black-Market Sale pays **rank + 2 per punch**, and the two **Deep Sites** on turns 5–6 accept *only* Worn cards at full rank. Late game has an appetite for ruin.

## The three systems

### System 1 — The Wreck (verb: return, punched)

The Site Schedule exposes **two sites per turn, twelve total**. Each site states a suit appetite and a rank threshold. **A site can be claimed once, by one crew** — sites are a race.

To **Work a site** (one action): players from one crew together commit cards from their hands totalling the threshold in the named suits. Face cards count 11, Aces count 1 (Aces are capital, not muscle). Sealed cards cannot be committed; Worn cards count half.

If the threshold is met: the crew scores the site's SP, **every committed card is punched and returned to its owner's hand**, and one committed card (committers' choice) is tagged with the site's name. **Mishap:** the single lowest-rank committed card takes a **seal** instead of returning available.

No site's appetite is satisfiable from one suit, and the late sites exceed what most single hands can carry — committing is a team act (Pattern 5).

#### Site Schedule (v0.1 numbers — tune in playtest)

| Turn | Site | Appetite | SP |
|---|---|---|---|
| 1 | Cargo Bay | 12+ total: ♣ and ♠ only | 4 |
| 1 | Med Locker | 10+ total: ♥ and ♣ only | 3 |
| 2 | Crew Quarters | 14+ total: ♥ and ♠ only | 4 |
| 2 | Vault Door | 16+ total: ♠ and ♦ only, must include a face card | 6 |
| 3 | Hydroponics | 14+ total: ♥ and ♣ only | 5 |
| 3 | Bridge | 18+ total: all four suits represented | 7 |
| 4 | Drive Core | 20+ total: ♣ and ♠ only | 8 |
| 4 | Captain's Safe | 15+ total: ♦ and any, must include an Ace | 7 |
| 5 | **Deep Hold** | 16+ total: **Worn cards only**, full rank | 9 |
| 5 | Armoury | 20+ total: ♠ and ♣ only | 8 |
| 6 | **Deep Reactor Shaft** | 18+ total: **Worn cards only**, full rank | 10 |
| 6 | Stateroom | 22+ total: all four suits represented | 9 |

### System 2 — The Market (verbs: travel, and spend)

During the Council phase, crews may trade — and **only the Brokers may speak across crews** (Pattern 15). Anything is tradeable: cards (which keep their marks and their back colour — history travels with the object, Pattern 12), promises, SP transfers (recorded openly), and contracts.

- **Crew-to-crew trade (travel):** traded cards go to the other crew's hands. The receiving crew can read every tag and punch — provenance is intel.
- **Black-Market Sale (spend, one action):** remove one card from the game permanently (back in the box, face up). Score its rank in SP, **+2 per punch** on it. Coins and objects both accepted; Relics refused.
- **Torn-half contracts (Pattern 22):** to seal a cross-crew deal, a Broker tears one of their own cards in half at the handshake; each crew keeps half. The rank torn is the stake. When the deal's condition is met, the halves are reunited and the deal executes. If a crew breaks the deal, the wronged crew reveals its half at game end: **the breaker loses SP equal to the stake; the wronged crew gains it.** The torn card is spent forever.

### System 3 — The Reactor (verb: spend forever)

The reactor demands feeding **twice: at the end of turn 3 (Tremor) and the end of turn 6 (Final Collapse).**

- **Tremor (end of turn 3):** the two crews together must commit cards totalling **rank 24+, including at least one ♥ and one ♣ from each crew.** Committed cards are **spent — torn and boxed.** If unmet: every player immediately takes a seal on their highest unmarked card, and the Final Collapse threshold rises by 6.
- **Final Collapse (end of turn 6):** together, **rank 36+ (or 42+ if the Tremor was failed), at least two suits from each crew.** Relics count double rank here. If unmet: **the reactor breaches — nobody wins** (Pattern 4, gated).

Contributions are made openly, one card at a time, alternating crews — everyone sees who fed the reactor and who held back (Pattern 5: the marks and the torn pile keep the receipts).

The thresholds are deliberately beyond any one crew's comfortable spare capacity (Pattern 5). v0.1 numbers; tune so that a single crew *can* technically carry a failed partner — at ruinous cost.

### The jokers (Pattern 23)

The first time a crew claims a site **using cards from three or more different players**, that crew takes one of its jokers into any member's hand. A joker is a one-shot wildcard: any suit, rank 10, usable at a site or a crisis, **spent** after use. Two per crew, maximum.

## Turn structure (×6)

1. **Expose** — read out this turn's two sites from the schedule.
2. **Council (3 minutes)** — intra-crew planning, constrained: *you may say what you can do; you may not tell another player what to do* (Pattern 15, boxed resolution). Brokers (only) may cross the table to negotiate, trade, and tear contracts.
3. **Actions** — starting with the start crew and alternating crews, each player takes **two actions** in any order: **Work** (commit to a site with teammates), **Sell** (Black-Market, one card), **Mend** (Medic only: play any ♥ — it takes a punch — to clear one seal anywhere in your crew), **Deal** (execute a prepared trade or contract reunion), or **Pass**.
4. **Crisis** — end of turns 3 and 6 only: feed the reactor.
5. **Cleanup** — punched cards return to hands; pass start crew to the other side.

## End and scoring

If the Final Collapse was met: each crew totals SP — sites + sales + contract penalties/awards + 5 per met individual goal. **Highest SP wins.** The individual with the most personally-generated SP (sites they committed to count split evenly) is MVP. If the reactor breached: read the debrief questions anyway; the playtest data is the real score.

## Budget arithmetic (Pattern 9 check)

13 cards × ~2 plays × 6 turns = up to 12 card-plays per player, against 13 held. Work returns cards (punched), so the loop sustains; the reactor spends ~3–5 cards per player across the session; sales and contracts drain a few more. Expected end-state: hands of 7–10 heavily-marked cards — ruin visible by the midpoint, every surviving card a biography by the end (Pattern 3). If playtest shows hands collapsing before turn 5, raise site SP and lower crisis thresholds before touching the lifecycle mix.

## What this prototype tests

The point of playing this is to move stars in the pattern language (Appendix B protocol). Record, per session:

| Hypothesis under test | Pattern | What to watch |
|---|---|---|
| Cards travelling between crews creates a provenance/intel layer worth having | 12, 19 | Did anyone *read* a traded card's marks and act on them? Did back colours matter? |
| Role identity survives card travel at this volume | 12 vs 7 | By turn 6, did hands still feel like roles? |
| Coin/object boundary is parseable at the table | 13 | Did players start naming marked cards? Disputes about what a card "is"? |
| Three-tier goals stay coherent; the gate stabilises semi-coop | 4, 5 | Did anyone sandbag the reactor? Was carrying a defector possible and bitter? |
| Hidden SP keeps the leader illegible | 6 | Any bash-the-leader or kingmaking talk? |
| Torn halves work as contracts | 22 | Were contracts made? Broken? Did the physical halves matter? |
| Three-mark terminal form paces the endgame | 21 | When did the first Relic appear? Did Relics cluster at the crises? |
| The mark grammar parses at a glance | 16, 17 | Time spent reading state vs deciding, late game |
| The swap teaches roles cold | 8 | Could a new player say what their role wanted by turn 2? |
| Shrinking hands keep a floor of agency | 14 | Was any player benched by an empty or sealed-up hand? |

**Playtest report:** date, player count, register experience of the group, which rules were misread, the watch-list above, and the three numbers that felt most wrong. File reports in the repo under `worked-games/space-salvagers/playtests/`.

---

*Built against Pattern Language v0.1. Numbers in the Site Schedule and crisis thresholds are hypotheses, not tuning. The PvE single-crew trainer (environment deck simulating a rival crew) is deferred until this two-crew economy is validated — see project backlog.*
