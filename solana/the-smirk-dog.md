---
token: The Smirk Dog
ticker: RIVER
network: solana
risk_score: 19
status: low
date: 2026-11-03
---

# The Smirk Dog (RIVER) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-smirk-dog-sol)

---

## Audit Summary

The Smirk Dog (River) is a standard SPL Token-2022 asset with both mint and freeze authorities successfully revoked. The liquidity is fully burned, ensuring the pool cannot be rug-pulled by the creator. No adverse flags were reported by third-party registries, and the token exhibits standard operational parameters.

> **Final Recommendation:** The token is currently in a secure state with no administrative backdoors. Holders should continue to monitor the top 10 holder distribution to ensure concentration does not increase significantly, which could impact market volatility.

Verify the current supply and authority status periodically using a block explorer to confirm that no unexpected changes have occurred, although the current revocation status makes this highly unlikely.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance metrics show 28.91% concentration among the top 10 holders. 7.6 External liquidity is $10,378, with 100% of LP tokens burned, preventing liquidity withdrawal. The… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is non-mutable, and no authority exists to modify token parameters. The token state is fixed and cannot be altered by any external… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 65.5% of supply. Of that, 36.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 28.9% in wallets, 0.0% in other contracts. 80 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

80 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $15K (DexScreener, all pools). 24h trading volume $135K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $15K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GrGCEe...pump`](https://solscan.io/account/GrGCEeQU7FGA9Xky9ogpinxoMfexUbMTL27zhJ82pump) |
| **Network** | Solana |
| **Price** | $0.00004214 |
| **24h Volume** | $135.2K |
| **Liquidity** | $15.3K |
| **Volume / Liquidity** | 8.8× |
| **Token Age** | 2d |
| **Top-10 Holders** | 65.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1285 buys / 1002 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/erdrrdkngcq4dujknta11oogdz9kawyttrp9gps8z3jy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-smirk-dog-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
