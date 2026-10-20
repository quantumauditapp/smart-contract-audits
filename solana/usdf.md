---
token: USDF
ticker: USDF
network: solana
risk_score: 0
status: low
date: 2026-10-20
---

# USDF (USDF) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usdf-sol)

---

## Audit Summary

USDF is a Solana SPL Token-2022 mint exhibiting a highly secure technical configuration, including revoked mint and freeze authorities and 100% burned liquidity. While technical risks are minimal, third-party registries flag high holder correlation and high market cap per holder. Note that native RPC data for holder distribution was unavailable, though secondary facts confirm low concentration among sellable wallets.

> **Final Recommendation:** Monitor the high holder correlation flagged by third-party registries, as this can indicate coordinated trading activity despite the low individual wallet concentration. No technical action is required regarding authorities, as the mint and freeze functions are permanently disabled.

Verify the continued stability of the liquidity pool and ensure no new un-burned pools are created by the same deployer. The token is technically sound for standard interactions given the current state of revoked authorities and burned liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program (7.1) with no active transfer hooks or fees (7.2). Access control is robust as both the mint and freeze authorities are permanently revoked (7.3). The… |
| **Governance / Economics** | 10/10 | Low | Economic security is high with 100% of pool liquidity burned, ensuring the creator cannot withdraw the underlying assets (7.4, 7.6). Holder concentration is exceptionally low, with the top 10… |
| **Upgrades** | 10/10 | Low | The mint is non-upgradable as all administrative authorities have been nullified (7.7). Metadata is marked as immutable, preventing any post-launch changes to the token's branding or symbol (7.7).… |

## Security Findings

_🟢 1 Low · ⚪ 11 Informational_

### `L-01` — High Holder Correlation  *(Severity: Low · Status: Unresolved)*

A third-party risk registry flags 'High holder correlation', which may indicate that multiple top wallets are controlled by the same entity or group.

**Recommendation:** Monitor large transfer patterns for signs of synchronized selling across different wallet addresses.


### `I-01` — Mint Authority Revoked  *(Severity: Informational · Status: Resolved)*

The fact block confirms 'Mint Authority: revoked (None)'. No new tokens can be minted to dilute current holders.

**Recommendation:** No action required; the supply is fixed.


### `I-02` — Freeze Authority Revoked  *(Severity: Informational · Status: Resolved)*

The fact block confirms 'Freeze Authority: revoked (None)'. The issuer cannot freeze user accounts or block transfers.

**Recommendation:** No action required; the token is non-freezable.


### `I-03` — Liquidity Permanently Burned  *(Severity: Informational · Status: Resolved)*

100.0% of the pool's LP tokens are burned, meaning the liquidity can never be withdrawn by the creator.

**Recommendation:** No action required; the pool is permanent.


### `I-04` — Metadata Immutable  *(Severity: Informational · Status: Resolved)*

The fact 'metadata_mutable: False' indicates that the token name, symbol, and URI cannot be changed.

**Recommendation:** No action required; branding is permanent.


### `I-05` — Low Holder Concentration  *(Severity: Informational · Status: Resolved)*

The top 10 holders that can sell hold only 6.61% of the supply, significantly reducing the risk of a single-whale dump.

**Recommendation:** No action required; distribution is decentralized.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 6.8% of supply. Of that, 0.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 6.6% in wallets, 0.0% in other contracts. 3,443 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,443 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.6M (DexScreener, all pools). 24h trading volume $159K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.3685 — it does not hold a peg. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.6M of DEX liquidity across 1 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`thKNTw...pump`](https://solscan.io/account/thKNTwBkTGX4UzQ2VHfP2BScCzJNh4HzkaYFuS7pump) |
| **Network** | Solana |
| **Price** | $0.3685 |
| **24h Volume** | $158.7K |
| **Liquidity** | $1.65M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2d |
| **Top-10 Holders** | 6.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 82030 buys / 1440 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/alpgkneqieu6amogmet5qkqz4j2w1wbfpotgyihdq9gg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usdf-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
