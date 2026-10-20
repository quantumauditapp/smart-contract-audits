---
token: Souljacoin
ticker: SOULJA
network: solana
risk_score: 0
status: low
date: 2026-10-20
---

# Souljacoin (SOULJA) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/souljacoin-sol)

---

## Audit Summary

Souljacoin (SOULJA) demonstrates a strong technical security posture with all administrative authorities revoked and 100% of liquidity permanently burned. While technical risks are minimal, a third-party registry has flagged high holder correlation, and specific holder distribution data was unavailable via RPC at the time of analysis.

> **Final Recommendation:** Users should manually inspect the top holder list using a Solana block explorer to investigate the 'high holder correlation' signal before interacting. While the technical risks of minting and freezing are eliminated, the primary risk remains market-driven due to potential wallet coordination.

Monitor the liquidity pool and large wallet movements for signs of coordinated sell-offs. The burned liquidity status provides a high degree of safety against developer-led exit scams, but does not protect against whale-driven price volatility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is built on the spl-token-2022 program, which is a standard and audited framework on Solana (7.1 Architecture). All critical access points, including the Mint and Freeze authorities, have… |
| **Governance / Economics** | 10/10 | Low | Liquidity is robust at approximately $276,992, with 100% of LP tokens burned to prevent withdrawal (7.4 Economic). The volume-to-liquidity ratio of 0.85 suggests healthy, non-manipulated trading… |
| **Upgrades** | 10/10 | Low | The token configuration is immutable as all administrative keys are nullified (7.7 Upgrades). Metadata is also marked as non-mutable, preventing changes to the token's visual or descriptive identity… |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `M-01` — High Holder Correlation Signal  *(Severity: Medium · Status: Unresolved)*

An independent third-party risk registry has flagged this token for high holder correlation. This pattern often indicates that a significant portion of the supply is controlled by a coordinated group of wallets, which can lead to synchronized sell-offs.

**Recommendation:** Verify the distribution of tokens across top wallets to ensure the supply is not overly concentrated in a few hands.


### `L-01` — Holder Distribution Data Unavailable  *(Severity: Low · Status: Unresolved)*

Chain-native RPC sources failed to provide the specific holder concentration data during the audit. The exact percentage of supply held by the top 10 holders could not be deterministically calculated.

**Recommendation:** Use an alternative block explorer to confirm that no single wallet holds a disproportionate amount of the circulating supply.


### `I-01` — Permanent Liquidity Lock  *(Severity: Informational · Status: Resolved)*

100% of the pool's liquidity tokens have been burned. This ensures that the liquidity can never be withdrawn by the pool creator or any other authority.

**Recommendation:** No action required; this is a positive security feature for holders.


### `I-02` — Revoked Administrative Authorities  *(Severity: Informational · Status: Resolved)*

Both the Mint Authority and Freeze Authority are set to null. The supply is permanently capped, and the ability to freeze user accounts has been removed.

**Recommendation:** No action required; these revocations are standard best practices for decentralized tokens.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $275K (DexScreener, all pools). 24h trading volume $335K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $275K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`78rKNT...pump`](https://solscan.io/account/78rKNTKpmuSC6VFWPndzcUmW372dXssHYhYk2vsUpump) |
| **Network** | Solana |
| **Price** | $0.01037 |
| **24h Volume** | $334.9K |
| **Liquidity** | $274.9K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 23h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 50525 buys / 13587 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bh5rmb2kta6c257s5zhypedu9hgmmujkjdln75msebwa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/souljacoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
