---
name: macro-fx-pipeline
description: Analyze FX pairs, currencies, or macro-driven instruments through a structured three-level institutional pipeline (macro reality → COT positioning → trap & liquidity). Use this skill whenever the user asks to analyze a currency pair (EUR/USD, USD/JPY, etc.), build or evaluate a macro trade thesis, interpret a COT report, assess central bank divergence, or asks "what do you think about [pair/currency]" in a trading context — even if they don't explicitly name the three levels. Also trigger when the user shares COT data, macro dashboards, or asks about positioning, rate differentials, or trade invalidation conditions.
---

# Macro FX Pipeline

A structured analysis framework for macro-driven FX trading. Every analysis flows through three sequential levels. Never conclude from one level alone — each level confirms, contradicts, or adds nuance to the previous.

## Core principles

- **Sequence matters.** Always go Level 1 → 2 → 3. Level 1 sets the structural thesis; Levels 2 and 3 modify timing and risk, they do not replace it.
- **Positioning and crowd narrative are modifiers, not signals.** A crowded COT position (Level 2) or an "obvious" retail narrative (Level 3) adjusts *how and when* to act on the Level 1 thesis — they are not standalone entry signals.
- **State data gaps explicitly.** If a level lacks input data, say exactly what's needed (e.g. "need latest TFF report" or "need current core PCE") rather than guessing.
- **Direct tone.** Concrete numbers, concrete conditions. Skip basic concept explanations unless asked — apply the structure to the data.

## When data is needed

If current market data is required and tools are available, fetch it: central bank rates, CPI/core PCE/HICP, PMIs, yield spreads, COT reports, price levels. If no tools, work with user-provided data and flag what's missing.

---

## Level 1 — Macro Reality

Establishes the structural (weeks–months) driver. Work through:

1. **Business cycle phase** for each relevant economy: expansion / overheating / slowdown / pre-recession. Use PMI (read manufacturing separately from services — divergence between them often matters more than the composite), GDP growth, unemployment trajectory.

2. **Each central bank's dominant pain** — inflation vs growth/employment. Critically, identify **which inflation gauge is each bank's official mandate target**:
   - Fed → core PCE
   - ECB → headline HICP
   This determines how the same shock (e.g. oil) transmits into different bank actions. A shock to a headline gauge hits a headline-mandate bank harder and faster than a core-mandate bank. This asymmetry is often the crux of an FX thesis.

3. **Yield spread** (10Y base vs 10Y counter) — direction and recent trend. Widening → capital flows toward the base currency for yield.

4. **OIS / market pricing** — not just the next meeting, but the 6–12 month trajectory. A meeting can be 97% "hold" while the market simultaneously reprices year-end toward hikes/cuts — that repricing is the real signal.

5. **Latest data** — does it change CB policy or is it already priced? Check headline vs core separately.

**Level 1 output:** direction + which channel it transmits through (rate differential / risk-flow & safe-haven / trade balance). If multiple geopolitical or macro scenarios are live, map each separately — the same outcome (e.g. currency weakness) can run through different channels in different scenarios, each with its own leading indicators.

See `references/transmission-mechanics.md` for the detailed channel-by-channel logic, including how oil shocks split across central banks.

---

## Level 2 — Smart Money (COT)

Use the **TFF report** (Traders in Financial Futures), never Legacy. Five steps, always in order:

1. **Leveraged Funds — direction.** Net position and sign.

2. **LF — conviction.** Weekly delta (Δ) plus COT Index (52-week percentile):
   ```
   COT Index = (current net − period min) / (period max − period min) × 100
   ```
   Index < 10% or > 90% = crowded. This is **not a reversal signal by itself** — it's a flag for sharp counter-move risk on an unexpected catalyst.

3. **Asset Managers — confirmation.** Read direction over the last 3–4 weeks, not the absolute number. AM are slow; their turn lags but confirms a structural shift. LF turned but AM haven't = early signal, higher risk.

4. **Open Interest — money in or out.** OI rising while position builds → new conviction money. OI falling on a sharp net change → washout/liquidation, not a new trend (classic setup for a reversal).

5. **Cross-check with Level 1.** Does positioning confirm, contradict, or *lead* the macro thesis (LF entered before the market repriced the macro)?

**Level 2 output:** confirms / contradicts / leads relative to Level 1, plus an explicit crowding flag if COT Index is at an extreme.

See `references/cot-reading.md` for the full reading method, category definitions, and worked patterns.

---

## Level 3 — Trap & Liquidity

1. **Obvious retail conclusion.** What does the crowd think after the latest big headline? Did that scenario actually play out, or was it "sell the news" / "buy the rumor"?

2. **Retail sentiment** (where available). Extreme skew (>60/40) is contrarian. Near neutral = no signal; don't force one.

3. **Technical levels & liquidity.** Where do key levels (swing points, recent highs/lows) sit relative to current price? Same side or both sides? Does that align with the Level 1/2 direction?

4. **Binary catalysts.** CB meetings, geopolitical resolutions, major data in the coming days/weeks. How does each interact with Level 2 crowding — if LF are at an extreme, a catalyst favoring the other side produces a squeeze.

**Level 3 output:** whether liquidity and crowd positioning align with or oppose the direction; a concrete list of trigger events with dates.

---

## Final Synthesis

Always close with this structure:

- **Thesis:** direction + transmission channel(s).
- **Structural invalidation:** a specific macro event or data point (not a price level) that breaks Level 1.
- **Tactical note:** near-term binary catalysts and how they could cause a temporary counter-move *without* invalidating the structural thesis. If positioning (Level 2) is crowded, a sharp squeeze on a catalyst may be a *better entry after* it — especially if the squeeze itself is the mechanism Level 1 predicts will strengthen the thesis (e.g. one CB easing after a shock clears, widening divergence).
- If the thesis holds in **both** geopolitical outcomes (through different channels), say so explicitly and give distinct monitoring indicators for each channel.

## Output format

Keep it tight. For a full analysis use this skeleton:

```
LEVEL 1 — MACRO REALITY
[cycle / CB pain + mandate gauge / spread / pricing / data → direction + channel]

LEVEL 2 — SMART MONEY (COT)
[5 steps → confirms/contradicts/leads + crowding flag]

LEVEL 3 — TRAP & LIQUIDITY
[retail / sentiment / levels / catalysts → align or oppose]

SYNTHESIS
Thesis: ...
Structural invalidation: ...
Tactical note: ...
```

For a single-level question (e.g. "just read this COT"), answer only that level but note which level it is and that it's one input to the full picture.
