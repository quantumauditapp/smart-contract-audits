---
token: Paranoid mode
ticker: PARANOID
network: solana
risk_score: 1
status: low
date: 2026-10-31
---

# Paranoid mode (PARANOID) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/paranoid-mode-sol)

---

## Audit Summary

The PARANOID token mint is well-secured with both mint and freeze authorities permanently revoked. Liquidity is highly protected, with 99.4% of pool assets locked. Third-party risk registry data is unavailable, and metadata remains mutable.

> **Final Recommendation:** The token demonstrates strong security posture regarding authority control and liquidity locking. Holders should monitor the metadata for any unexpected changes given the mutable status.

Verify the current metadata state via block explorer to ensure it aligns with expected branding. No further on-chain action is required to mitigate authority-based risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.1 Architecture is standard, with no complex extensions or… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by 99.4% of liquidity being locked. 7.5 Governance is decentralized as no single entity holds a majority of the supply. 7.6 External market data shows a 6-day pair… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints. 7.8 Operations are standard, though metadata remains mutable, allowing for potential branding changes. No other mutable extensions are active. |

## Security Findings

_🟢 1 Low · ⚪ 7 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be changed by the original creator at any time.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 27.0% of supply. Of that, 7.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.6% in wallets, 0.0% in other contracts. 1,029 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as PARANOID (PARANOID), rank #6174. 1,029 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

99.4% of the pool's LP is burned or time-locked. 99.3% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 0.6% is held, unlocked, by 3 address(es) other than the pool's creator. This assessment covers the main pool, which holds 89% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $61K (DexScreener, all pools). 24h trading volume $43K (CoinGecko, all markets, daily snapshot). 24h trading volume $463K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $61K of DEX liquidity across 13 pools. Launch: 6 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`22rWiy...pq6X`](https://solscan.io/account/22rWiyDiY9GgxSrFiWC2vX1GxNxjkvrRPmZJDzv9pq6X) |
| **Network** | Solana |
| **Price** | $0.0003655 |
| **24h Volume** | $443.7K |
| **Liquidity** | $54.5K |
| **Volume / Liquidity** | 8.1× |
| **Token Age** | 6d |
| **Top-10 Holders** | 27.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3814 buys / 3094 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/5diq3hfj6qtcjxhag1xvbisluqjhnue24ykkzlkmjooh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/paranoid-mode-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
