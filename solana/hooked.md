---
token: Hooked
ticker: HOOKED
network: solana
risk_score: 0
status: low
date: 2026-10-01
---

# Hooked (HOOKED) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hooked-sol)

---

## Audit Summary

The Hooked SPL token mint has its mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts. However, its metadata is mutable, allowing for changes to branding post-launch. Holder concentration data was unavailable from chain-native RPC, and no critical or high-severity issues were identified.

> **Final Recommendation:** Holders should monitor the token's metadata for any unexpected changes to its branding, such as its name, symbol, or image. Before relying on the token's off-chain representation, verify its current metadata state on-chain. If holder concentration data becomes available, assess it to understand potential market manipulation risks from large holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | 7.1 Architecture & 7.3 Access Control: The Hooked token is an SPL token operating on the Solana network. Its mint authority is revoked, ensuring no new tokens can be minted, and its freeze authority… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic: The token exhibits healthy trading patterns with a 24-hour volume of $638,137 against a liquidity of $128,677, resulting in a normal Volume/Liquidity Ratio of 4.96. A significant… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades: The mint authority and freeze authority for the Hooked token are both revoked, meaning these critical controls cannot be re-enabled or transferred, providing a high degree of… |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch. The fact block indicates 'metadata_mutable: True' and 'Third-party risk registry signals: Mutable metadata'.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Hooked (HOOKED), rank #3629.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

96.9% of the pool's LP is burned or time-locked. 96.9% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 2.6% is held, unlocked, by 5 address(es) other than the pool's creator. This assessment covers the main pool, which holds 67% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $174K (DexScreener, all pools). 24h trading volume $557K (CoinGecko, all markets, daily snapshot). 24h trading volume $922K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $174K of DEX liquidity across 17 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`C1mBfB...PngE`](https://solscan.io/account/C1mBfBoDkwWfd6uTFZp62ARHLjeVp3bDpCDMfMZtPngE) |
| **Network** | Solana |
| **Price** | $0.001465 |
| **24h Volume** | $589.3K |
| **Liquidity** | $116.2K |
| **Volume / Liquidity** | 5.1× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1699 buys / 2002 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/c7r9jxwivymbyr2jj5yslieitugjpjqxweg7hpu8nwuk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hooked-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
