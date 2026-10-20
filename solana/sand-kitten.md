---
token: Sand Kitten
ticker: SNDK
network: solana
risk_score: 44
status: medium
date: 2026-09-30
---

# Sand Kitten (SNDK) — Smart Contract Security Analysis | Solana

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sand-kitten-sol)

---

## Audit Summary

The Sandisk - Backpack Securities (SNDK) token is an SPL Token-2022 mint with its critical mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts. However, the token's metadata is mutable, allowing for potential changes to its name, symbol, or image post-launch. Holder distribution data was unavailable, preventing a full assessment of supply concentration.

> **Final Recommendation:** Before interacting with this token, holders should monitor the on-chain metadata for any changes to the token's name, symbol, or image. While core authorities are revoked, the upgradable transfer fee should be tracked to ensure it remains within acceptable limits. Due to unavailable holder distribution data, it is advisable to monitor on-chain holder activity for any signs of high concentration or large whale movements.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is implemented using the spl-token-2022 program, benefiting from modern SPL extensions. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted… |
| **Governance / Economics** | 7/10 | Low | The token has a total DEX liquidity of $277,901, with 100.0% of the pool's liquidity locked for good in Raydium's LP locker, preventing rug pulls from liquidity withdrawal. The 24-hour volume is… |
| **Upgrades** | 6/10 | Medium | The critical mint and freeze authorities are revoked, which significantly reduces upgrade-related risks. However, the token's metadata is mutable, meaning its name, symbol, or image can be altered… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 3.0% · upgradeable |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token's metadata_mutable flag is set to True. This means that the token's name, symbol, or image can be changed by an authority after launch, potentially leading to brand confusion or misrepresentation. (Fact: metadata_mutable: True)

**Recommendation:** Verify metadata against off-chain expectations before trusting branding. Monitor for any changes to the token's name, symbol, or image.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $501K (DexScreener, all pools). 24h trading volume $2.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $501K of DEX liquidity across 6 pools. Launch: 5 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8t5C4A...X7x2`](https://solscan.io/account/8t5C4AWDg4CroMChxdo7rG2e8nJM31QG2GG7Czx9X7x2) |
| **Network** | Solana |
| **Price** | $0.007738 |
| **24h Volume** | $427.5K |
| **Liquidity** | $204.3K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 5d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 818 buys / 876 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dtrbpr4myid2s8wryckgidtqgu5r5uaw89cby9vv5be8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sand-kitten-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-30*
