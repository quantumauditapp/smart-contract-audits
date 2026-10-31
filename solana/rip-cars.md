---
token: Rip Cars
ticker: CARS
network: solana
risk_score: 67
status: high
date: 2026-10-31
---

# Rip Cars (CARS) — Smart Contract Security Analysis | Solana

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/rip-cars-sol)

---

## Audit Summary

The Rip Cars token (CARS) operates on the standard SPL Token program. The primary security risks identified include an active mint authority capable of diluting supply and high holder concentration. Third-party risk registry data is unavailable for this assessment.

> **Final Recommendation:** Investors should monitor the mint authority address (5n1kEkZ68h2Wb6TPB88GPgvjv5tAoLyGGPSJCwoTWkLm) for potential supply inflation. Verify the current mint authority status on-chain before committing capital.

Given the high holder concentration, users should be aware of potential price volatility resulting from large-scale sell-offs. Ensure that any liquidity provision is performed through verified DEX interfaces.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token utilizes the standard SPL Token program (7.1 Architecture). Access control is currently centralized, as the mint authority remains active (7.3 Access Control). The freeze authority has been… |
| **Governance / Economics** | 6/10 | Medium | The top 10 holders control 72.20% of the supply, indicating significant concentration (7.4 Economic). Liquidity is healthy at $259,328 with a stable volume/liquidity ratio of 0.77 (7.6 External).… |
| **Upgrades** | 6/10 | Medium | The token metadata is mutable, allowing for potential changes to branding (7.7 Upgrades). No other upgradeable extensions are active. Operational security relies on the current mint authority holder… |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 5n1kEkZ68h2Wb6TPB88GPgvjv5tAoLyGGPSJCwoTWkLm. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 72.20% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor top holder wallet activity for signs of coordinated liquidation.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `L-01` — Pool Liquidity Not Locked  *(Severity: Low · Status: Unresolved)*

The fact block indicates that liquidity lock status is unknown, meaning it cannot be confirmed as protected from withdrawal.

**Recommendation:** Exercise caution as liquidity may be withdrawable by the pool creator.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 74.4% of supply. Of that, 2.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 18.4% in wallets, 53.8% in other contracts. 1,012 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Rip Cars (CARS), market cap $3M, rank #1950. 1,012 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $394K (DexScreener, all pools). 24h trading volume $28K (CoinGecko, all markets, daily snapshot). 24h trading volume $317K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $394K of DEX liquidity across 6 pools. Launch: 97 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CARSsx...meta`](https://solscan.io/account/CARSsxWPkpQWvfyRBwfGMGvysJBHdHGfE46X5MNgmeta) |
| **Network** | Solana |
| **Price** | $0.168 |
| **24h Volume** | $201.0K |
| **Liquidity** | $259.3K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 74.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 484 buys / 332 sells |

## Security Flags (2/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/3szfyfczcgxe6zptqqbfnkf24smakwchxp3au68hnyij)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/rip-cars-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
