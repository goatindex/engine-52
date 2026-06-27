# Salvage Run — Playtest Report (synthetic, harness tier-3)

**Date:** 2026-06-27
**Instrument:** the LLM playtest-harness (`D:\playtest-harness`), Salvage Run ported as the
`space_salvagers` game module against minimum-prototype v0.1.
**Players:** 6 — two crews of 3 (Breaker-Broker fused, Wrench, Medic per crew) + 1 facilitator.
**Register experience of the group:** synthetic. Every seat is a `claude-sonnet-4-6` agent
(tier 3 — the cheaper tiers can't sustain this kind of game). Treat all findings through
that lens: agents are more rule-compliant, more cooperative, and less socially adversarial
than humans. Social/negotiation and "bash-the-leader" signals are *under*-represented here.
**Runs:** four sessions, seeds 1–4, campaign `salvagers-c1`. Seeds 1–2 were instrument
shakedown (the harness port had bugs that masked the game); seeds 3–4 are the clean reads.

---

## TL;DR for the design

The game **runs and is winnable**: by seed 3 both reactor crises were met through genuine
multi-seat contribution and a crew won on hidden SP. But two of the prototype's *headline
untested hypotheses did not get exercised at all*, and one strong emergent balance problem
appeared:

1. **The inter-team economy never happened.** Zero cross-crew trades and zero torn-half
   contracts across **all four runs**. The single mechanic the prototype most wanted to
   test (Patterns 12, 19, 22) produced **no behaviour to observe**.
2. **Selling beats salvaging.** The Black-Market Sale became the dominant action
   (28 then 39 sales vs. 12–15 site-works), i.e. agents cashed out their hands rather than
   working the wreck — the opposite of the intended core loop.
3. **The three-tier gated goal (Pattern 4/5) works** once players can actually act — this
   is the prototype's clearest *positive* result.

Everything that blocked seeds 1–2 was **instrument** error (harness port bugs), now fixed
and verified; see the appendix so you don't mistake those for design failures.

---

## Hypotheses under test — verdicts (the Evidence Register update)

Mapped to the minimum-prototype's "What this prototype tests" table.

| Hypothesis | Pattern | Verdict | Evidence |
|---|---|---|---|
| Cross-crew card travel creates a provenance/intel layer | 12, 19 | **UNTESTED** — no trades occurred | 0 `deal` in 4 runs |
| Torn-half contracts work | 22 | **UNTESTED** — none were ever torn | 0 `tear_contract` in 4 runs |
| Three-tier gated goals; gate stabilises semi-coop | 4, 5 | **SUPPORTED** | seeds 3–4: both crises met, reactor survived, crew won |
| Hidden SP keeps the leader illegible | 6 | **Weakly supported** | no bash-the-leader talk; SP stayed hidden (but agents barely metagame) |
| Three-mark terminal form paces the endgame | 21 | **Partial** | Relics appeared, but mark-counting was misread (see F010) |
| Mark grammar parses at a glance | 16, 17 | **Mostly yes** once feedback existed | few mark disputes after the port fix |
| The swap teaches roles cold | 8 | **NOT genuinely tested** | the harness auto-resolves the swap; no human-learning signal |
| Shrinking hands keep a floor of agency | 14 | **Contradicted** | selling + first-mover lockout *benched* seats (F005, F007) |
| Coin/object boundary is parseable | 13 | **No problem observed** | agents didn't dispute marked-vs-unmarked once feedback worked |

**Net:** the gate (4/5) earns a star; the inter-team economy (12/19/22) earns **nothing yet**
— not refuted, simply never elicited; agency-floor (14) earns a *negative* mark.

---

## Design findings & recommendations (for the spec)

These are about *Salvage Run*, not the harness. Ledger ids in `salvagers-c1`.

### F006 (major, social) — the Broker economy never activates
Across four games no crew ever traded a card or tore a contract. The other crew is visible
only as a hand-count; nothing in the turn structure *invites* the Brokers to talk, and the
Council's "Brokers may cross the table" is a permission, not a prompt or an incentive.
**Recommend:** give the cross-crew exchange a *reason to exist* — e.g. a site or contract
that can only be satisfied with a card of the other crew's back colour, a per-turn "market
window" the facilitator explicitly opens, or a standing buyer/price for foreign cards. As
written, the entire inter-team layer is inert.

### F005 (major, balance) — selling dominates the salvage loop
Black-Market Sale was the most-used action by a wide margin (39 sales in seed 4). It is
costless, role-unrestricted, and always available, so any seat shut out of a site just
cashes out. This crowds out the work-the-wreck loop the game is named for.
**Recommend:** make selling compete with salvaging — cap it (once per crew per turn), lower
the payout, raise site SP, or make sold cards count *against* a goal. Right now the optimal
line is "sell, don't salvage."

### F007 (major, balance) — first-mover site lockout
Two sites per turn, each claimable in one action by one crew, means the first one or two
acting seats take both sites and everyone later passes (or sells — see F005). Combined with
the fused Breaker-Broker holding 26 cards, early seats dominate.
**Recommend:** expose more sites per turn, allow a second crew to contest/partial-claim, or
let a site accumulate contributions across the round so later seats can still participate.

### F012 (observation, balance) — snowball: inconclusive, watch it
Seed 3 was a blowout for the first-acting crew (154–93); seed 4 was close with the *second*
crew ahead (145–131). No clear runaway-leader effect yet. **Recommend:** more seeds before
acting; do not tune for a snowball that may not exist.

### Smaller items
- **F008 (mishap is a solved puzzle):** "lowest committed card is sealed" just trains players
  to bring a throwaway. Make *which* card is risked a real choice (committer picks, with a
  cost), or seal a *random* committed card.
- **F009 (post-Tremor 42 threshold):** felt like a foregone conclusion when the Tremor failed.
  Now mostly moot (the Tremor passes easily — see "numbers" below) but revisit the jump.
- **F010 (Relic legibility):** state plainly that *each* punch is a mark, so three punches
  alone make a Relic; players miscounted.
- **F011 (role downtime):** Wrench/Medic idle when their suit is unwanted. The turn-zero
  swap helps only weakly at 3-per-crew (2 cards swapped). Consider a fuller swap or a
  role-agnostic fallback action.

---

## The three numbers that felt most wrong

1. **Black-Market payout (rank + 2/punch)** — too generous; it made cash-out beat salvage.
2. **Reactor thresholds (Tremor 24 / Final 36)** — too *low*: the Final Collapse cleared
   116 vs 36 in seed 3. The gate functions but currently lacks the intended *tension*; with
   cooperative agents it was never in doubt. (Caveat: humans may hoard more — but the margin
   was huge.)
3. **Two sites per turn** — too few for six players; it is the root of the first-mover
   lockout and pushes idle seats into selling.

---

## Appendix — instrument (harness) issues, now FIXED

Seeds 1–2 *breached the reactor and looked like balance failures, but were port bugs.* Do
not read them as design signal. All fixed and verified by seed 3 (facilitator deny-churn
fell 24 → 7 → 2; reactor fed 0 → 9 times). Recorded in the ledger as F001–F004:

- **F001** players got no feedback on rejected actions and a validator quirk reversed correct
  facilitator denials → fixed with a per-seat feedback channel + legality in the validator.
- **F002** the reactor crisis was a separate phase players couldn't tell they were *in* (they
  waited for a prompt they already had) → fixed by folding feeding into the normal turn and a
  harness-wide change that now tells every agent its current phase.
- **F003** card ids used pip numbers (King = "…-13") misread as rank 13 (K = 11) → fixed with
  rank-label ids.
- **F004** multi-player site work was opaque (players expected to accumulate partial cards) →
  fixed with explicit rules + a worked example + the feedback channel.

---

*Filed by the synthetic playtest harness. Raw artifacts: `D:\playtest-runs\space_salvagers-t3-{1..4}`
and the campaign ledger `D:\playtest-runs\salvagers-c1\ledger.yaml`. v0.1 numbers are
hypotheses, not tuning — the above are recommendations for v0.2, not verdicts.*
