# Design Exploration — Follow-up Analysis

*A companion to the "Design Exploration — Updated" working notes. Four analytical
layers on the five proposed patterns (THE BREATHING HAND, SPEND HAS A DESTINATION,
THE ASSIST, CLOCKS MAKE TIME VISIBLE, ROLES THAT PLAY DIFFERENTLY) and the
toggleable-subsystem set. None of these proposals is in `pattern-language.md` yet;
this document prepares them for entry under the Appendix B protocol rather than
asserting them. Written against pattern-language v0.1.*

The four layers, in order:

- **A — Simulation test plan.** What observation moves each proposed pattern up
  or down the S-track. The §8-of-the-exploration "how does a hypothesis earn its
  mark" gap, answered in the existing S0–S4 vocabulary.
- **B — SPEND HAS A DESTINATION, reworked.** The destination ladder with a
  default-routing rule so the elegance doesn't become a per-spend decision tax.
  Drop-in Alexandrian form.
- **C — Complexity budget.** What the proposed "minimum prototype" actually asks
  one player to track, and a thinner teaching configuration below it.
- **D — Failure modes.** The un-fun / broken state of each proposal, with the
  early-warning signal each would throw in the harness.

A running theme: A and D converge on the same short instrumentation list, which
is a good sign the analysis is closing rather than sprawling.

---

## A — Simulation test plan for the proposed patterns

The exploration notes correctly observe that patterns enter at hypothesis
confidence but never say what *promotes* one. The S-track (Appendix B.8) is the
machinery; this is the content for it — per proposed pattern, the signal that
would earn S1, what would *refute* the therefore (and so deny or drop the mark),
and which harness metric carries it.

Conventions, consistent with Appendix D: every entry to date is **adjacent**
(no worked engine build exists), so the harness can take any of these to **S2**
at most; S3+ needs a real `games/engine52/` module. Metric status: **✅** exists
in the harness today, **🟡** exists for TAG (the cooperative-facilitated game) and
usable as a proxy, **🔨** needs new instrumentation.

| Proposed pattern | Core claim (the *therefore*) | Earns S1 if… | Refutes / drops if… | Carrying metric |
|---|---|---|---|---|
| **THE BREATHING HAND** | Hand size is a designed per-role curve, not a fixed allotment | Hands diverge by role in the intended directions and no seat hits a dead hand | Hands converge (differentiation cosmetic) **or** a role collapses to no-legal-play | per-seat hand-size-over-time 🔨; dead-state proxy `forfeit_count` + stall ✅ |
| **SPEND HAS A DESTINATION** | A recoverability ladder keeps the economy flowing *and* preserves the drama of loss | Spend spreads across rungs; no stall-from-starvation; permanent spends rare and weighty | Spend collapses to one rung (all-safe → no drama, or all-permanent → starvation/stall) | spend-destination distribution 🔨; stall detection ✅ |
| **THE ASSIST** | A cheap bounded lend creates coordination without quarterbacking | Lends happen, participation stays balanced, **the weakest seat receives net inflow** | Lends converge on one voice-directed recipient **or** the move is never used | `participation_imbalance` ✅, `community_action_share` ✅; lend-target + weakest-seat-inflow 🔨 |
| **Toggle: action-triggered marks** | Suffering happens to cards automatically, not as a step | Marks accrue as consequence and the table tracks them | Mark-inflation — everything marked, signal flat (cf. TERMINAL FORM 21) | mark-rate-per-card 🔨 |
| **Toggle: forced consequences** | Failure imposes a card action the player didn't choose | Consequences land and adjudicate cleanly | Griefing / dispute / forfeit spike | `ruling_verdicts` deny-rate ✅, `forfeit_count` ✅ |
| **Toggle: public-discard intel** | Spent piles are readable intel that shifts decisions | A player **reads a pile and changes a decision** | Piles ignored — the intel claim silently fails | decision-change detector 🔨 (the hard one) |
| **CLOCKS MAKE TIME VISIBLE** | Pacing independent of any team's speed; the shared tier gets a backbone | Endgame arrives *via the clock*; cross-session pacing variance narrows | Endgame still by depletion/accident; or too many clocks → tracking tax (errors/time rise) | termination reason ✅, rounds-to-end variance ✅, shared-clock trajectory 🟡 (TAG's CR *is* a shared clock) |
| **ROLES THAT PLAY DIFFERENTLY** | Decision-type differentiation is the durable anti-quarterbacking defense | Each role's exclusive move is used by that role; no spectator seats; balance holds with a strong player present | Exclusive moves unused (roles still resource-only); imbalance high despite playbooks | `participation_imbalance` ✅, per-seat action distribution ✅; exclusive-move usage rate 🔨 |

**What's closest to confirmable now.** THE ASSIST, CLOCKS, and ROLES are already
covered or proxied by the cooperation metrics the harness computes for TAG
(participation balance, community/solo share, the CR shared-clock trajectory,
per-seat action distribution). Run against TAG-as-stand-in they can reach S1–S2
immediately; the rest wait on a worked engine build or the new instrumentation.

**The new-instrumentation shortlist** (also the answer to D's warning signs):

1. **spend-destination distribution** — which rung each spend lands on. Direct
   analogue of the harness's existing action-distribution + community/solo split.
2. **mark-rate-per-card** — to catch mark-inflation against the TERMINAL FORM (21)
   cap.
3. **"was this information acted on"** — a generic decision-change detector. This
   is the genuinely hard one, and it is *not* Engine-52-specific: it is the same
   unanswered question the harness has about whether facilitator rulings and other
   public information are read or ignored. Solve it once, generically.

These three are the highest-leverage harness work because they make every *future*
proposed pattern self-validating rather than entering on faith.

---

## B — SPEND HAS A DESTINATION, reworked with default-routing

The exploration's strongest single idea, refining CARD LIFECYCLE (9). The risk it
carries: "for every spending action, declare its destination" is a decision *on
every spend* — a per-turn decision tax of exactly the kind one-shot teach budgets
(§7-of-the-analysis) cannot afford. The fix is the move the engine already borrows
from fate-deck games (Malifaux, Castle Falkenstein): the destination is a property
of the **card or action**, not a player choice each time. Declaration becomes the
weighty exception — which is where the drama belongs anyway.

### The destination ladder

Recoverability increases down the rungs:

| Destination | What happens | Recovers how | Theme it serves |
|---|---|---|---|
| Permanent (sacrifice) | Torn / surrendered / burned. Gone for the session. | Never. | Irreversible cost, ritual, treaty (TORN HALVES, 22). |
| Tapped / exhausted | Card stays, turned, spent for now. | Untaps on a reset, heal, or repair trigger. | Fatigue, cooldowns, capacity that returns. |
| Team pile | Discard only your team draws from. | Your team redraws it later (salvage, recall). | Internal stockpile, institutional memory. |
| System pile | Pile tied to the system that consumed it. | Redraws only within that system. | Domain economies; a system that feeds itself. |
| Global feeder | Facilitator-managed pool. | Facilitator tops up feeders, markets, other teams. | Open economy, trade, scarcity you can buy out of. |

### The default-routing rule

1. **Every card carries a default sink**, set by its suit/type (printed as an
   "exhaust to ___" line). Most cards sink to *tapped* or *system pile*.
2. **Every system action carries a default sink** for the cards it consumes; the
   action's sink overrides the card's when they differ.
3. **On a normal spend, nobody declares anything** — the card routes to its sink
   automatically. The ladder is invisible at this speed.
4. **Declaration is a deliberate move, in exactly two cases:**
   - **Voluntary escalation** — a player pushes a spend *one rung toward
     permanent* to buy a stronger effect or honour the fiction (burn the card for
     the finishing blow). Rare, chosen, weighty.
   - **Forced escalation** — a failure or hard outcome pushes a spend one rung
     toward permanent automatically. This *is* the "forced consequences" toggle,
     now wired into the economy rather than floating beside it.
5. **De-escalation** — making a card *more* recoverable than its default, pulling
   it back up the ladder — is never free and never default. It requires a role or
   system that grants it, and that grant is the **Logistician's exclusive lever**
   (ROLES THAT PLAY DIFFERENTLY).

### Drop-in pattern block (Alexandrian form)

> **SPEND HAS A DESTINATION (proposed — prototype first)**
>
> *A refinement of CARD LIFECYCLE (9); the permanent rung is SPEND AS SACRIFICE
> (11). Default routing keeps it frictionless; ROLES THAT PLAY DIFFERENTLY owns
> de-escalation.*
>
> **"Spend" is a choice of where a card goes — but a consumable economy needs the
> drama of permanent loss *and* a way to keep cards flowing, and if every spend
> must be declared the ladder's elegance becomes a per-turn decision tax.** Treat
> every spend as permanent and the table starves; treat none as permanent and the
> drama evaporates; make players narrate every spend's fate and the engine's
> tightest constraint — one-shot teach budget (§7) — is blown on bookkeeping.
>
> Conditions vary the live rungs. A fast convention one-shot may run only two
> (tapped vs. permanent); an institutional megagame lights all five and leans on
> the global feeder for inter-team trade (CARDS THAT TRAVEL, 12). The boxed
> register prints sinks on the cards; facilitated registers can let control
> re-route a sink as a ruling.
>
> Therefore: **give each card and each system action a default sink on the
> recoverability ladder, so normal spending routes automatically and silently.
> Reserve declaration for two weighty cases — a player voluntarily escalating one
> rung toward permanent for effect, and a failure forcing that escalation. Make
> de-escalation a granted power, never a default: the lever one role owns.**
>
> *Completed by: SPEND AS SACRIFICE (11, the permanent rung), CARDS THAT TRAVEL
> (12, via the global feeder), ROLES THAT PLAY DIFFERENTLY (de-escalation). Wired
> to the forced-consequences toggle (escalation). Facilitator-managed rungs depend
> on REGISTER BEFORE RULES (1) and THE FACILITATOR'S KIT (25).*

### Worked examples

| Situation | Routing | Player decision? |
|---|---|---|
| Gunner plays an attack card | Default sink *tapped* → untaps on reset | **None** — automatic |
| Gunner *burns* it for a finishing blow | Voluntary escalation → *permanent* | **Declared** — rare, weighty |
| Logistician runs a salvage action | Action sink *team pile* (overrides card sinks) → team redraws later | **None** — automatic |
| Logistician spends their exclusive recall move | De-escalation: pulls a card from *system pile* up to *team pile* | **Granted** — only this role can |
| A play fails, forced-consequences toggle ON | Forced escalation → the failed card sinks one rung toward permanent | **None** — imposed |

The reframe ties three layers together — economy, the forced-consequences toggle,
and the role layer — instead of leaving the ladder a standalone declaration tax.

---

## C — Complexity budget

The exploration's stated minimum prototype (echoing §10 of the analysis): *one
team, three systems with different card appetites and different spend destinations,
the three-mark grammar, THE ASSIST live, one clock.* Here is what that actually
asks one player to hold:

| # | Surface | What the player tracks | Load |
|---|---|---|---|
| 1 | Breathing hand | Your suit hand **+ its role breathe-rate** | M |
| 2 | Three systems | Which cards each of 3 systems wants (3 appetite mappings) | H |
| 3 | Spend destinations | Where spent cards go — recoverable vs. permanent, which pile feeds back | M |
| 4 | Three-mark grammar | What 3 marks mean and when each applies (CLOSED MARK GRAMMAR, 16) | M |
| 5 | THE ASSIST | The once-per-turn lend move | L |
| 6 | One clock | Reading the shared track as it ticks | L |

**The finding: the "minimum" prototype is not minimal.** Six live subsystems, two
at high load, sits at the *upper* edge of a learnable first session — measured
against a tight PbtA playbook (your whole decision space on one sheet) or a clean
trick-taker. The risk is not any single surface; it is the sum. A first table can
spend its whole cognitive budget *learning the engine* and never reach the
behaviours the prototype exists to observe — coordination, the breathing economy,
weighty spends. This is ONE-SHOT TEACH COST (§6.7 of the analysis) applied to the
prototype itself.

**Two recommendations.**

1. **Define a Scale-0 teaching configuration below the current "minimum."** Hand +
   **one** system + spend-as-binary (recoverable vs. permanent, ladder hidden) +
   THE ASSIST + one clock. Defer the three-mark grammar and multi-system appetites
   to session two. That is four surfaces, max load M — learnable in ten minutes
   and still exercising the two highest-value hypotheses (THE ASSIST, the breathing
   hand). It is also the cleanest first S-track run: fewer confounds per session.

2. **Make complexity budget a first-class concept in the pattern language.** Each
   worked configuration declares its **surface count and total load**, the way it
   already declares its register (1) and lifecycle sentence (9). A governance rule
   — *"a teaching configuration declares its surfaces and caps at four, with no
   more than one High-load surface"* — turns the subtractive discipline already
   applied to clocks ("prefer one primary clock") into a uniform principle. Right
   now that discipline is applied to clocks and nowhere else; spend-destinations
   get "declare every time" (fixed in B) and playbooks get four building blocks
   with no "pick one."

For reference, the full engine stacks all five ladder rungs live + three toggles +
up to five clock types + four playbook building blocks + the cross-team feeder +
CARDS THAT TRAVEL. That is an institutional-larp configuration and entirely
legitimate — but it should be *named as the top of a scale*, with Scale-0 at the
bottom, so no one ships the larp as a first game by accident.

---

## D — Failure modes

The exploration is strongly generative (what to add, why it is good). The most
trustworthy moments are its flashes of "how this goes wrong" — mark-inflation on
kickers, "visible piles imply visible standing, risky in competitive." This makes
that systematic: one un-fun / broken state per proposal, the early-warning signal
it throws, and the cheapest guard.

| Proposal | Un-fun / broken state | Early-warning sign (metric) | Cheapest guard |
|---|---|---|---|
| **THE BREATHING HAND** | A role's hand contracts to unplayable (the gunner stuck with no legal play); or "breathing" is bookkeeping nobody feels | A seat repeatedly has no legal play (`forfeit_count` ↑, stall) | EVERY HAND PLAYABLE (24) as a **hard floor** + a minimum-hand backstop draw |
| **SPEND HAS A DESTINATION** | Decision fatigue (pre-B); or spend collapses to one rung — all-safe (no drama) or all-permanent (starvation); or the ladder is accounting theatre no one feels | Spend distribution skewed to one rung; stall-from-starvation (spend-dist 🔨 + stall ✅) | Default-routing (B); make **permanent always a choice, never a default**; cap permanent-spend frequency |
| **THE ASSIST** | Quarterbacking via directed lends ("everyone lend to Sam"); or a dead mechanic never used | Lend-target convergence on one seat; **or** zero lends (`participation_imbalance`, `community_action_share`) | ROLES THAT PLAY DIFFERENTLY (the **real** defense — see note) + cap: lends can't all target one seat per round |
| **Toggle: action-triggered marks** | Mark-inflation — every card marked, the signal goes flat | Mark rate approaching 100% (mark-rate 🔨) | Mark **budgets**; keep some systems that prefer unmarked cards (OBJECT OR COIN, 13); TERMINAL FORM (21) cap |
| **Toggle: forced consequences** | Griefing vector; disputes over imposed actions | Deny/dispute + forfeit spike (`ruling_verdicts` ✅, `forfeit_count` ✅) | WITNESSED MARKING (18) adjudication; default OFF; only ON where the fiction wants weight |
| **Toggle: public-discard intel** | Ignored clutter (intel claim fails); or paranoia / visible standing in competitive (tension with NO LEGIBLE LEADER, 6) | Piles never referenced before a decision (decision-change detector 🔨) | Default OFF; restrict to coop/larp register; **test that it is read before committing it** |
| **CLOCKS MAKE TIME VISIBLE** | Clock ignored — endgame still by accident; or too many clocks = tracking tax | Termination reason ≠ clock; rising errors/time (termination ✅, rounds-variance ✅) | "One primary clock" — promote from preference to a **hard cap in teaching configs** |
| **ROLES THAT PLAY DIFFERENTLY** | Exclusive move too fiddly → ignored → roles collapse back to resource-only; or so strong it becomes mandatory → one role pilots | Exclusive-move usage near zero; **or** one role dominates the action distribution (`participation_imbalance` ✅, per-seat dist ✅) | The exploration's own line — *"simple to execute even where consequences are deep"* — promoted to a **test**; power-budget the move |

**Two structural notes carried from the table.**

- **THE ASSIST depends on ROLES to be safe.** The once-per-turn-per-player bound
  caps each *lender* but not *convergence*: a dominant voice doesn't touch cards,
  it just directs four lends toward one recipient. The real anti-quarterbacking
  defense is decision-type differentiation (ROLES) — a leader cannot out-play a
  seat whose exclusive move they do not possess. So THE ASSIST should be sequenced
  *with* ROLES, not before it; shipping the lend without the playbook ships the
  quarterbacking vector without its counterweight.

- **Nearly every guard is either "default OFF / make it a choice" or one of the
  metrics in section A.** The two failure modes not yet observable —
  mark-inflation and public-intel-ignored — are exactly the two new-instrumentation
  items from A. A and D point at the identical short build list, which is the
  reassuring sign that the failure surface is bounded and measurable rather than
  open-ended.

---

## The through-line

The highest-leverage move is not adding or rewording any single pattern — it is
closing the design↔evidence loop the S-track already frames. A gives the
hypothesis→signal mapping; D gives the failure signals; both reduce to one small
harness build list:

1. spend-destination distribution
2. mark-rate-per-card (against the TERMINAL FORM cap)
3. a generic "was this information acted on" detector

Build those into a real `games/engine52/` module and every future proposed
pattern becomes self-validating on the S-track instead of entering on faith. That
module — even at Scale-0 — is a better next artifact than drafting any further
pattern, because it is the thing that lets the language earn its marks.
