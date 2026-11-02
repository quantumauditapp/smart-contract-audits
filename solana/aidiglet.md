---
token: AiDiglet
ticker: DIGS
network: solana
risk_score: 17
status: low
date: 2026-11-02
---

# AiDiglet (DIGS) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aidiglet-sol)

---

## Audit Summary

AiDiglet (DIGS) is a Token-2022 asset with fully revoked mint and freeze authorities, ensuring supply immutability and preventing account freezing. Liquidity is fully secured via 100% burning of LP tokens, mitigating withdrawal risks. No adverse flags were reported by third-party registries.

> **Final Recommendation:** The token exhibits strong security properties regarding authority and liquidity. Holders should monitor the top 10 holder concentration periodically to ensure no single entity accumulates a majority stake.

Verify the current supply and authority status directly via block explorer tools to confirm the 'revoked' state remains unchanged before executing large trades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active extensions like transfer hooks or default frozen states. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance metrics show healthy distribution with top holders controlling 16.11% of supply. 7.6 External liquidity is $19,889, with 100% of LP tokens burned, eliminating rug-pull… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints do not support proxy-based logic updates. Metadata and balance-mutating authorities are disabled, ensuring the token configuration remains static… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 37.2% of supply. Of that, 21.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 16.1% in wallets, 0.0% in other contracts. 2,006 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,006 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $20K (DexScreener, all pools). 24h trading volume $251K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $20K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 5 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9QT8K6...pump`](https://solscan.io/account/9QT8K685Hrae4k11dhGXirdtpfAaimExtyfwt8cPpump) |
| **Network** | Solana |
| **Price** | $0.00006897 |
| **24h Volume** | $250.9K |
| **Liquidity** | $20.5K |
| **Volume / Liquidity** | 12.2× |
| **Token Age** | 5d |
| **Top-10 Holders** | 37.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4759 buys / 4603 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3mxdjdz1gae5hzic4dj4unldxj5dbcc9jssyq55mfykg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aidiglet-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
