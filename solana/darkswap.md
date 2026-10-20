---
token: DarkSwap
ticker: DARK
network: solana
risk_score: 5
status: low
date: 2026-10-08
---

# DarkSwap (DARK) — Smart Contract Security Analysis | Solana

> **Risk Score: 5/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/darkswap-sol)

---

## Audit Summary

The DarkSwap (DARK) token mint has its mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts. However, the token's metadata remains mutable, allowing changes to its name, symbol, or image post-launch. Information regarding pool liquidity locking was unavailable, preventing a full assessment of liquidity risk.

> **Final Recommendation:** Holders should monitor the token's metadata on-chain to ensure its name, symbol, and image remain consistent with expectations. Before relying on the token's branding, verify that the current metadata aligns with official project information. Due to unavailable data, monitor the pool's liquidity status for any locking or burning events.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The DarkSwap (DARK) token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no holder accounts can be frozen. It does… |
| **Governance / Economics** | 7/10 | Low | Holder concentration is low, with the top 10 holders that can sell possessing only 11.95% of the total supply. The token has substantial liquidity at $424,475 USD, with a 24-hour volume of $2,732,612… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, meaning core token parameters like supply and account freeze status cannot be altered. While the token uses the Token-2022 program, it does… |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 15.5% of supply. Of that, 3.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 11.9% in wallets, 0.0% in other contracts. 8,039 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as DarkSwap (DARK). 8,039 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.4M (DexScreener, all pools). 24h trading volume $7.8M (CoinGecko, all markets, daily snapshot). 24h trading volume $14.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.4M of DEX liquidity across 16 pools. Launch: 6 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7KEPAp...6kH3`](https://solscan.io/account/7KEPApdbBMByrmqihz3bht2uMhFQcatjfSFQCKq66kH3) |
| **Network** | Solana |
| **Price** | $0.006822 |
| **24h Volume** | $2.69M |
| **Liquidity** | $425.8K |
| **Volume / Liquidity** | 6.3× |
| **Token Age** | 6d |
| **Top-10 Holders** | 15.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10948 buys / 11621 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/aeqaczb73pue7bf7nyzedkv9xns78ckrhpbyu8uldhds)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/darkswap-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
