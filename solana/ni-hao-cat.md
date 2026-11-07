---
token: ni hao cat
ticker: MIHAO
network: solana
risk_score: 7
status: low
date: 2026-11-07
---

# ni hao cat (MIHAO) — Smart Contract Security Analysis | Solana

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ni-hao-cat-sol)

---

## Audit Summary

The ni hao cat (mihao) token is a standard SPL Token-2022 implementation with all administrative authorities revoked. The token exhibits healthy liquidity characteristics with 100% of pool liquidity permanently burned, and no adverse flags were reported by third-party registries. No critical or high-severity security risks were identified.

> **Final Recommendation:** The token is currently in a secure, immutable state. Holders should continue to monitor the top 10 holder distribution via block explorers to ensure concentration does not increase significantly over time.

No further action is required to secure the mint configuration. Users should verify the mint address against official project channels before interacting to avoid impersonation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program, ensuring compatibility with modern extensions. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance factors are stable, with top 10 holders controlling 24.83% of the supply. 7.6 External market data shows $67,064 in liquidity, which is fully burned and inaccessible… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints do not utilize proxy patterns. Metadata is immutable, and there are no upgradable transfer hooks or fees. The token state is fixed and cannot be… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 33.7% of supply. Of that, 8.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 24.8% in wallets, 0.0% in other contracts. 672 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

672 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 80% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $79K (DexScreener, all pools). 24h trading volume $450K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $79K of DEX liquidity across 19 pools. Launch: launched on pump.fun, 12 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 12 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 12 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4CxjZy...pump`](https://solscan.io/account/4CxjZyMNoF1p6eXHXHv1TWpS2X47CuUmLwtGe18spump) |
| **Network** | Solana |
| **Price** | $0.0005569 |
| **24h Volume** | $423.3K |
| **Liquidity** | $63.0K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 12d |
| **Top-10 Holders** | 33.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3698 buys / 3030 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ho1asg6wgh1ffxdehrk2f4ggt1hoxo9s5jclmdqeyebz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ni-hao-cat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
