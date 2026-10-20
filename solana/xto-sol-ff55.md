---
token: XTO
ticker: XTO
network: solana
risk_score: 0
status: low
date: 2026-10-20
---

# XTO (XTO) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-sol-ff55)

---

## Audit Summary

The XTO token exhibits a highly secure technical configuration with all administrative authorities revoked and 100% of liquidity permanently burned. The primary risk identified is a third-party registry signal regarding high holder correlation, though direct concentration remains low at 4.41% for the top 10 sellable wallets. Third-party registry data for rug-pull flags was checked, but only correlation signals were present.

> **Final Recommendation:** Monitor the top holder wallets for coordinated sell-offs, as the high correlation signal suggests they may be controlled by a single entity or group. Since the liquidity is 100% burned and the mint authority is revoked, the token is protected against common 'rug pull' mechanics like liquidity removal or infinite minting.

Verify the current holder distribution on-chain periodically to ensure no new large clusters emerge. Treat the token as a fixed-supply asset with no administrative intervention possible.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint utilizes the spl-token-2022 program with no active extensions such as transfer hooks or fees (7.1). Access control is fully decentralized as both the mint and freeze authorities are revoked… |
| **Governance / Economics** | 10/10 | Low | Economic health is supported by $154,173 in DEX liquidity and a normal volume/liquidity ratio of 3.17 (7.4). Holder concentration is exceptionally low, with the top 10 sellable wallets holding only… |
| **Upgrades** | 10/10 | Low | The token is immutable as all administrative keys are nullified, ensuring no future changes to the mint logic (7.7). Metadata is also marked as non-mutable, protecting the token's branding and… |

## Security Findings

_🟢 1 Low · ⚪ 9 Informational_

### `L-01` — High Holder Correlation  *(Severity: Low · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation. This suggests that multiple top wallets may be controlled by the same individual or group, potentially masking the true level of supply concentration.

**Recommendation:** Analyze the transaction history between the top 10 wallets to identify coordinated movements before taking large positions.


### `I-01` — Mint Authority Revoked  *(Severity: Informational · Status: Resolved)*

The mint authority is set to null. This ensures that no additional tokens can ever be minted, protecting holders from supply dilution.

**Recommendation:** No action required; this is a positive security state.


### `I-02` — Freeze Authority Revoked  *(Severity: Informational · Status: Resolved)*

The freeze authority is set to null. The creator cannot freeze user accounts or block transfers, ensuring the token remains permissionless.

**Recommendation:** No action required; this is a positive security state.


### `I-03` — Liquidity Permanently Burned  *(Severity: Informational · Status: Resolved)*

100% of the pool's LP tokens have been burned. This means the liquidity in the DEX pool can never be withdrawn by the creator or any other party.

**Recommendation:** No action required; this significantly reduces the risk of a liquidity rug pull.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 5.1% of supply. Of that, 0.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.4% in wallets, 0.0% in other contracts. 2,568 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,568 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $152K (DexScreener, all pools). 24h trading volume $488K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $152K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3rF2NS...pump`](https://solscan.io/account/3rF2NSivMQcHgKJfSQST2SHESmsHr6vHbzfkVgG2pump) |
| **Network** | Solana |
| **Price** | $0.003171 |
| **24h Volume** | $487.9K |
| **Liquidity** | $152.2K |
| **Volume / Liquidity** | 3.2× |
| **Token Age** | 3d |
| **Top-10 Holders** | 5.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 88264 buys / 21775 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2aewsofkaipyotedsswvdl5pacmb9gvk9dtg5w8uhhgj)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-sol-ff55)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
