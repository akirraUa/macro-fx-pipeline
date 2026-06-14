# COT Reading — Detailed Method

## Which report

Use **TFF (Traders in Financial Futures)**, not Legacy. Legacy splits into commercial/non-commercial, which lumps hedge funds together with pension funds — useless for reading intent. TFF separates the players by type.

## The four categories

| Category | Who | How to use |
|---|---|---|
| **Leveraged Funds** | Hedge funds, CTAs | **Primary signal.** Fastest to react to a narrative shift, first to leave the crowd. Read these first. |
| **Asset Managers** | Pension funds, insurers | **Confirmation.** Slow, long-horizon. A reversal here is significant but lags weeks. |
| **Dealer/Intermediary** | Market makers | **Ignore.** Always opposite the speculators by obligation (providing liquidity). No signal. |
| **Non-reportable** | Small traders / retail | **Contrarian at extremes only.** |

## The three numbers that matter

Absolute net position alone says little. What matters:

1. **COT Index (52-week percentile):**
   ```
   COT Index = (current net − period min) / (period max − period min) × 100
   ```
   - Above 90 = crowd is long → contrarian downside risk
   - Below 10 = crowd is short → squeeze potential
   - 40–60 = neutral, no signal

2. **Week-over-week delta (Δ):** the *pace and conviction* of position change. A large single-week Δ = conviction entry, not a drift.

3. **Open Interest:** rising → new money entering, trend confirmed. Falling → positions closing, trend exhausting.

## Reading order (always)

1. LF net + sign → direction
2. LF Δ + COT Index → conviction & crowding
3. AM direction over 3–4 weeks → confirmation
4. OI → new money vs liquidation
5. Cross-check against the macro narrative

## Worked patterns

**Crowded long → reversal risk.** LF Index > 90. Crowd packed long. Any negative catalyst triggers cascade liquidation. Contrarian short setup (but timing needs a trigger — crowded can stay crowded for months).

**Crowded short → squeeze.** LF Index < 10. Everyone short. A positive catalyst forces a short squeeze. Contrarian long setup.

**LF vs AM divergence.** LF reverse (e.g. go short) while AM still hold the old direction (long). LF are usually right earlier — this is an early reversal signal, 2–4 weeks ahead of AM.

**OI falling on a sharp move.** Price moves hard but OI drops → it's longs meeting shorts at the exit (contracts vanish), i.e. a washout/liquidation, not fresh conviction. Often precedes a reversal.

**OI rising with a new position.** LF build a short AND OI rises → these are new, convicted shorts, not just old longs closing. The strongest confirmation pattern.

## Key distinction

"Reducing a long" ≠ "building a short." An Asset Manager net +280K cutting to +270K is *distributing*, not flipping bearish. Watch the direction of travel, not just the sign.

## Top mistakes

- Reading absolute net instead of percentile (50K could be a yearly high or mid-range).
- Treating "crowded" as an immediate reversal — it's a risk flag, not timing.
- Using Legacy instead of TFF.
- Reading COT without macro context — crowded long in a bull regime is normal; the same crowded long as the narrative breaks is a trap.
