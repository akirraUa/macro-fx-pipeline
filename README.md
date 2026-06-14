# Macro AI Agent for Claude

> A structured, institutional-grade analysis framework for macro-driven FX trading — packaged as a [Claude Agent Skill](https://docs.claude.com).

Every FX analysis flows through **three sequential levels**. No level concludes alone: each one confirms, contradicts, or adds nuance to the previous. The framework forces the question retail analysis skips — not *what* the trade is, but *how* the macro transmits into price, *when* the effect exhausts, and *what specifically* would break the thesis.


---

## The pipeline at a glance

```mermaid
flowchart LR
    subgraph L1["LEVEL 1 — MACRO REALITY"]
        direction TB
        A1[Business cycle phase] --> A2[CB dominant pain<br/>+ mandate gauge]
        A2 --> A3[Yield spread<br/>10Y base − 10Y counter]
        A3 --> A4[OIS / forward pricing<br/>6–12m trajectory]
        A4 --> A5[Latest data:<br/>priced or not?]
    end

    subgraph L2["LEVEL 2 — SMART MONEY (COT)"]
        direction TB
        B1[Leveraged Funds<br/>direction] --> B2[LF conviction<br/>Δ + COT Index]
        B2 --> B3[Asset Managers<br/>3–4w direction]
        B3 --> B4[Open Interest<br/>money in / out]
        B4 --> B5[Cross-check<br/>vs Level 1]
    end

    subgraph L3["LEVEL 3 — TRAP & LIQUIDITY"]
        direction TB
        C1[Obvious retail<br/>conclusion] --> C2[Retail sentiment<br/>skew]
        C2 --> C3[Technical levels<br/>& liquidity]
        C3 --> C4[Binary catalysts<br/>+ dates]
    end

    L1 -->|"direction + channel"| L2
    L2 -->|"confirms / contradicts / leads"| L3
    L3 --> SYN[["SYNTHESIS<br/>thesis · invalidation · tactical note"]]

    style L1 stroke:#C8A96E,stroke-width:2px
    style L2 stroke:#C8A96E,stroke-width:2px
    style L3 stroke:#C8A96E,stroke-width:2px
    style SYN fill:#C8A96E,color:#0a0a0a,stroke:#C8A96E
```

**Core rule of sequence:** Level 1 sets the structural (weeks–months) thesis. Levels 2 and 3 modify *timing and risk* — they never replace the thesis. A crowded COT position or an "obvious" retail narrative adjusts *how and when* to act, not *whether* the Level 1 read is correct.

---

## How the levels interact (decision logic)

The value isn't in the three boxes — it's in what each level does to the one before it. The two highest-leverage interactions:

```mermaid
flowchart TD
    START([Level 1 sets a direction]) --> Q1{Level 2: is COT<br/>at an extreme?<br/>Index &gt;90 or &lt;10}

    Q1 -->|"No — 40–60 neutral"| NEUTRAL[No positioning signal.<br/>Trade the L1 thesis on its own timing.]
    Q1 -->|"Yes — crowded same side as L1"| CROWD[Crowding flag:<br/>sharp counter-move risk<br/>on an unexpected catalyst]

    CROWD --> Q2{Level 3: is there a near-term<br/>binary catalyst favoring<br/>the OTHER side?}
    Q2 -->|"Yes"| SQUEEZE[Expect a SQUEEZE.<br/>Often a BETTER ENTRY *after* it —<br/>especially if the squeeze is the<br/>mechanism L1 predicts.]
    Q2 -->|"No"| HOLD[Crowded can stay crowded<br/>for months. Wait for a trigger.]

    NEUTRAL --> SYN([Synthesis])
    SQUEEZE --> SYN
    HOLD --> SYN

    style START stroke:#C8A96E,stroke-width:2px
    style SQUEEZE fill:#C8A96E,color:#0a0a0a,stroke:#C8A96E
    style SYN fill:#C8A96E,color:#0a0a0a,stroke:#C8A96E
```

### The crux: the mandate-gauge asymmetry

The single idea that separates this framework from "ECB dovish, Fed hawkish → short EUR": **the same shock transmits differently because each central bank targets a different inflation gauge.**

- **Fed → core PCE** (strips energy/food). An oil move barely touches its reaction function.
- **ECB → headline HICP** (includes energy). Oil feeds straight in.

```mermaid
flowchart TD
    OIL{Oil shock}
    OIL -->|"SPIKE"| SP_ECB[ECB headline rises →<br/>forced to hike into weak growth]
    OIL -->|"SPIKE"| SP_FED[Fed core unchanged →<br/>can stay on hold]
    SP_ECB --> SP_NET[Divergence NARROWS<br/>ECB catches up hawkishly]
    SP_FED --> SP_NET

    OIL -->|"COLLAPSE / ceasefire"| CL_ECB[ECB headline falls →<br/>hawkish rationale evaporates → eases]
    OIL -->|"COLLAPSE / ceasefire"| CL_FED[Fed core unchanged →<br/>holds]
    CL_ECB --> CL_NET[Divergence WIDENS<br/>in favor of USD]
    CL_FED --> CL_NET

    style OIL fill:#C8A96E,color:#0a0a0a,stroke:#C8A96E
    style CL_NET stroke:#C8A96E,stroke-width:2px
    style SP_NET stroke:#C8A96E,stroke-width:2px
```

Counterintuitive result: a structural **USD-bullish / EUR-bearish** thesis can be *stronger in the oil-collapse scenario* than in the oil-spike scenario — because of which gauge each bank is bound to. Full channel-by-channel logic in [`references/transmission-mechanics.md`](references/transmission-mechanics.md).

---

## What each level produces

| Level | Inputs | Output |
|---|---|---|
| **1 — Macro Reality** | Cycle phase, CB pain + mandate gauge, yield spread, OIS trajectory, latest data | Direction **+ which channel** it transmits through (rate differential / risk-flow / trade balance) |
| **2 — Smart Money (COT)** | TFF report: LF direction & conviction, AM, Open Interest | **Confirms / contradicts / leads** the L1 thesis, plus an explicit crowding flag |
| **3 — Trap & Liquidity** | Retail conclusion, sentiment skew, technical levels, binary catalysts | Whether liquidity & crowd **align or oppose**; a dated list of triggers |
| **Synthesis** | All of the above | Thesis · **structural invalidation** (a data event, not a price level) · tactical note |

---

## Installation

This is a Claude Agent Skill — a folder containing a `SKILL.md` plus reference files that Claude loads on demand.

```bash
git clone https://github.com/akirraUa/macro-fx-pipeline.git
```

Then place the `macro-fx-pipeline/` folder into the skills directory your Claude setup reads (e.g. your Claude Code / Agent skills path). Claude triggers it automatically whenever you ask to analyze a pair, read a COT report, or evaluate a macro thesis — no manual invocation needed.

The skill is self-contained:

```
macro-fx-pipeline/
├── SKILL.md                          # the framework + when-to-trigger logic
└── references/
    ├── cot-reading.md                # TFF method, COT Index, worked patterns
    └── transmission-mechanics.md     # channel-by-channel macro→price logic
```

---

## Usage examples

Anything that matches the trigger conditions activates the pipeline:

- `"What do you think about EUR/USD here?"` → full three-level analysis
- `"Read this COT for me: [data]"` → Level 2 only, flagged as one input to the full picture
- `"How does an oil ceasefire hit EUR/USD?"` → transmission-channel reasoning
- `"Is my short EUR/USD thesis still valid after this NFP?"` → checks the print against the structural invalidation, separates priced-in from new

The output stays tight and opinionated — concrete numbers, concrete invalidation conditions, no hedged filler.

---

## Design principles

- **Sequence matters.** Always L1 → L2 → L3. Positioning and narrative are modifiers, not standalone signals.
- **State data gaps explicitly.** If a level lacks input, the skill says exactly what's needed rather than guessing.
- **Invalidation is a macro event, not a price level.** The thesis breaks when a specific data point or CB action breaks it — not when a candle touches a line.

---

## License

[MIT](LICENSE) — use it, fork it, adapt your own levels.
