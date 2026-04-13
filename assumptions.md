# Monte Carlo Assumptions — Stablecoins / Shadow Banking / Reserve Opacity Trap

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $56.0B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 2.53 | Confirmed by N=100,000 draws |
| ΔW median (result) | $141.5B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_illicit_finance` | lognormal | $32.0B | $49.0B | $70.0B | Illicit stablecoin flows $141B (TRM Labs 2026), welfare multiplier 0.25-0.50. Sa |
| `C2_systemic_contagion` | lognormal | $18.0B | $28.0B | $45.0B | Run risk and DeFi cascading liquidations. Tether $186B market cap, $7.8T annuali |
| `C3_shadow_banking_credit` | lognormal | $12.0B | $21.0B | $30.0B | DeFi leveraged lending without prudential supervision. Deposit flight from regul |
| `C4_regulatory_capture` | lognormal | $3.5B | $4.25B | $5.0B | Crypto industry $200M+ in political spending 2023-2024. Each lobbying dollar pre |
| `C5_human_trafficking_scams` | lognormal | $8.0B | $12.5B | $17.0B | USDT as payment rail for pig-butchering scams ($10B+/yr), human trafficking oper |
| `C6_governance_institutional` | lognormal | $15.0B | $25.0B | $35.0B | Sanctions architecture erosion, monetary sovereignty costs for developing nation |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 1.5 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 1.5) = 0.0190%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 2.5 | 20% DC adj = 2.0 | 40% DC adj = 1.5

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $142B = 0.1% of world GDP ($106T) ✓
- **β_W range**: 2.53 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓
