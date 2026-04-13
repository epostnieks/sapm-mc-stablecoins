# SAPM Monte Carlo — Stablecoins / Shadow Banking / Reserve Opacity Trap

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Stablecoins / Shadow Banking (Reserve Opacity Trap).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **2.53** |
| β_W mean | 2.56 |
| β_W std | 0.39 |
| **90% CI** | **[2.0, 3.3]** |
| 99% CI | [1.8, 3.6] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$141.5B/yr** |
| Π (revenue) | $56.0B/yr |

**β_W = 2.53** means the stablecoins / shadow banking industry destroys **$2.53 in system
welfare for every $1.00 in revenue** — across 6 channels and 100,000 Monte Carlo draws.

**Classification**: Class 2 — Intractability

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-stablecoins.git
cd sapm-mc-stablecoins
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 2.53` and `ΔW median : $141.5B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_illicit_finance | $48.9B | [$34.2B, $69.9B] | Lognormal |
| C2_systemic_contagion | $28.0B | [$17.4B, $45.2B] | Lognormal |
| C3_shadow_banking_credit | $21.0B | [$14.7B, $30.0B] | Lognormal |
| C4_regulatory_capture | $4.3B | [$3.6B, $5.0B] | Lognormal |
| C5_human_trafficking_scams | $12.5B | [$9.2B, $17.0B] | Lognormal |
| C6_governance_institutional | $25.0B | [$17.9B, $35.0B] | Lognormal |
| **Total ΔW** | **$141.5B** | **[$110.3B, $182.5B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 1.5 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0190%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Stablecoins / Shadow Banking (Reserve Opacity Trap)*.
> GitHub: epostnieks/sapm-mc-stablecoins.
> https://github.com/epostnieks/sapm-mc-stablecoins
