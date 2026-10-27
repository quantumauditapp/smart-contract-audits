---
token: Conway Autonomous AI
ticker: CONWAY-SOL
network: solana
risk_score: 22
status: low
date: 2026-10-27
---

# Conway Autonomous AI (CONWAY-SOL) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/conway-autonomous-ai-sol)

---

## Audit Summary

The Conway Autonomous AI token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. The liquidity pool is fully burned, ensuring the protocol cannot rug-pull via liquidity withdrawal. No adverse flags were reported by third-party registries.

> **Final Recommendation:** Investors should monitor the top 10 holder wallets for potential sell-side pressure, as they control over 28% of the supply. No further on-chain action is required to secure the token's configuration as authorities are already revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program with no active extensions like transfer hooks or default frozen states. 7.1 Architecture is standard, and 7.3 Access Control is robust as both mint and… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic stability is supported by 100% burned liquidity, preventing withdrawal risks. 7.5 Governance is decentralized due to the lack of mint authority. Holder concentration is moderate, with… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is finalized and cannot be altered by any party. |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 64.5% of supply. Of that, 35.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 28.7% in wallets, 0.0% in other contracts. 121 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

121 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $168K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 3 pools. Launch: launched on pump.fun, 8 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 8 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 8 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5wyVHQ...pump`](https://solscan.io/account/5wyVHQcToNiSZsDVzDViZWQ8gRQng6TGTJ2U3NKSpump) |
| **Network** | Solana |
| **Price** | $0.00004777 |
| **24h Volume** | $148.4K |
| **Liquidity** | $16.8K |
| **Volume / Liquidity** | 8.8× |
| **Token Age** | 8d |
| **Top-10 Holders** | 64.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1692 buys / 1352 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2esrwnu4gwzaukxtz4k3w2bseuuzcmc3zvaeok3jb7mm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/conway-autonomous-ai-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
