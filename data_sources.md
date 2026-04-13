# Data Sources — Stablecoins / Shadow Banking Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Stablecoins / Shadow Banking: Reserve Opacity Trap) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_illicit_finance`

Illicit stablecoin flows $141B (TRM Labs 2026), welfare multiplier 0.25-0.50. Sanctions evasion (Russia A7A5 $72-100B), ransomware, fraud, narcotics. Sources: TRM Labs, Chainalysis, UNODC.

*Full citations: paper §4 (available SSRN).*

### `C2_systemic_contagion`

Run risk and DeFi cascading liquidations. Tether $186B market cap, $7.8T annualized DeFi volume. USDC depeg precedent (March 2023, SVB). Sources: BIS, Fed Carapella et al. 2022, S&P.

*Full citations: paper §4 (available SSRN).*

### `C3_shadow_banking_credit`

DeFi leveraged lending without prudential supervision. Deposit flight from regulated banking ($1.5T potential, Brookings 2025). Procyclical credit expansion. Sources: Brookings, Fed, BIS.

*Full citations: paper §4 (available SSRN).*

### `C4_regulatory_capture`

Crypto industry $200M+ in political spending 2023-2024. Each lobbying dollar preserves ~$15 in extraction space. Delayed BSA enforcement, weakened GENIUS Act. Sources: OpenSecrets, FEC filings.

*Full citations: paper §4 (available SSRN).*

### `C5_human_trafficking_scams`

USDT as payment rail for pig-butchering scams ($10B+/yr), human trafficking operations. SE Asia compound scam centers. Sources: UNODC 2024, FBI IC3, Chainalysis.

*Full citations: paper §4 (available SSRN).*

### `C6_governance_institutional`

Sanctions architecture erosion, monetary sovereignty costs for developing nations, institutional trust degradation. Sources: OFAC, Treasury, IMF.

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $56.0B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Stablecoins / Shadow Banking (Reserve Opacity Trap)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.
