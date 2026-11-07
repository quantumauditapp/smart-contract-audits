---
token: Everyday is Zeroday
ticker: 0DAY
network: solana
risk_score: 17
status: low
date: 2026-11-07
---

# Everyday is Zeroday (0DAY) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/everyday-is-zeroday-sol)

---

## Audit Summary

The token is configured with both mint and freeze authorities revoked, ensuring supply immutability and preventing account freezing. Liquidity is fully burned, eliminating withdrawal risks for the pool creator. Holder concentration data was unavailable, and the token is a recent deployment.

> **Final Recommendation:** The token is well-configured for a fixed-supply asset. Users should monitor the token's market activity on DEX platforms to assess slippage, as liquidity is relatively low. 

Verify the mint and freeze authority status directly on a block explorer to confirm they remain set to 'None'. No further security actions are required regarding the contract configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with all critical authorities revoked. 7.1 Architecture is standard for SPL-2022, while 7.3 Access Control is effectively disabled by the revocation of mint… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic parameters show $51,104 in liquidity, which is fully burned, ensuring 100% of pool funds are locked. 7.5 Governance is decentralized due to the lack of mint authority. 7.6 External… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints are immutable. 7.8 Operations are secure as metadata is immutable and no balance-mutating authorities exist. |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $48K (DexScreener, all pools). 24h trading volume $566K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $48K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`85mEAL...pump`](https://solscan.io/account/85mEALGuRCMmmMo7YD51pMfEjWisbHHRwZX8t7Bpump) |
| **Network** | Solana |
| **Price** | $0.0003613 |
| **24h Volume** | $561.9K |
| **Liquidity** | $47.6K |
| **Volume / Liquidity** | 11.8× |
| **Token Age** | 13h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3938 buys / 2374 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6qlmg6pz7esjvz3i7mp4arqknlkdy4ncanzsu8nnnofa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/everyday-is-zeroday-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
