---
token: CURVE
ticker: CURVE
network: solana
risk_score: 17
status: low
date: 2026-09-29
---

# CURVE (CURVE) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/curve-sol)

---

## Audit Summary

The CURVE token mint is an SPL Token-2022 asset with its mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts. However, the token's metadata is mutable, allowing for changes to its name, symbol, or image post-launch. The DEX pair is very new, having been created today, and holder concentration data was unavailable, preventing a full assessment of distribution risk. The token also exhibits a high volume/liquidity ratio, which can be a signal of artificial trading activity.

> **Final Recommendation:** Before engaging with this token, users should be aware of the mutable metadata and the very new pair age. Verify the token's current metadata (name, symbol, image) on-chain to ensure it aligns with expectations, and monitor for any changes. Given the extremely young age of the DEX pair, exercise extreme caution and consider waiting for a more established trading history to assess market stability and community behavior. Be mindful of the high volume/liquidity ratio, which may suggest artificial trading activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The CURVE token is an SPL Token-2022 asset with a total supply of 986,428,418.499783 tokens with 6 decimals. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can… |
| **Governance / Economics** | 7/10 | Low | The token's DEX pair is extremely new, having been created 0 days ago, which means there is no track record to assess team or holder behavior. Current liquidity stands at $386,200, with a 24-hour… |
| **Upgrades** | 8/10 | Low | The mint and freeze authorities for the token have been revoked, preventing any further changes to the token's supply or the ability to freeze holder accounts. While the token utilizes Token-2022… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | 2.0% (immutable) |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

DEX pair was created 0 days ago. Insufficient track record to assess team or holder behaviour.

**Recommendation:** Exercise caution due to the lack of historical data. Consider waiting for the pair to establish a longer track record before making significant investments.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by `metadata_mutable: True`.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding. Monitor for any changes to the token's name, symbol, or image.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $395K (DexScreener, all pools). 24h trading volume $2.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $395K of DEX liquidity across 13 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7ioeSg...Nbbh`](https://solscan.io/account/7ioeSgzfSKHMnpgfPpgRFsekMBGiu9oi6t6GeqYtNbbh) |
| **Network** | Solana |
| **Price** | $0.0005929 |
| **24h Volume** | $2.06M |
| **Liquidity** | $383.8K |
| **Volume / Liquidity** | 5.4× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8122 buys / 5546 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7pu2ytszmwg5qhmxxv4qb4ie7gcghy3kyjbgwfdfmmpb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/curve-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
