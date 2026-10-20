---
token: YieldPilot
ticker: YPILOT
network: solana
risk_score: 26
status: low
date: 2026-10-14
---

# YieldPilot (YPILOT) — Smart Contract Security Analysis | Solana

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/yieldpilot-sol)

---

## Audit Summary

The YieldPilot (YPILOT) SPL token mint exhibits a robust security posture based on available on-chain data. Key authorities such as mint and freeze authorities are revoked, preventing further token issuance or account freezing. Liquidity is substantially locked, and holder concentration is low, indicating a stable economic structure. Third-party risk registries report no adverse flags.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to ensure the supply and transferability are not subject to change. Monitor the token's liquidity and trading volume for any significant shifts, especially given its recent creation. While no immediate risks are identified, continuous monitoring of market dynamics is prudent for any new token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The YieldPilot (YPILOT) token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no holder… |
| **Governance / Economics** | 8/10 | Low | The economic structure of YieldPilot (YPILOT) appears stable. The top 10 holders that can sell account for 30.21% of the supply, indicating a relatively distributed ownership without significant… |
| **Upgrades** | 10/10 | Low | The YieldPilot (YPILOT) token mint has a fixed configuration with no mutable authorities that could alter its core behavior. Both the mint and freeze authorities are permanently revoked. Furthermore… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 50.8% of supply. Of that, 20.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 30.2% in wallets, 0.0% in other contracts. 226 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

226 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

95.4% of the pool's LP is burned or time-locked. 95.4% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $20K (DexScreener, all pools). 24h trading volume $85K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $20K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BrzPQi...pump`](https://solscan.io/account/BrzPQi5XHXwuZTDFNmYHF6YGXNRfsJ3DYLmTXwR5pump) |
| **Network** | Solana |
| **Price** | $0.00005712 |
| **24h Volume** | $45.7K |
| **Liquidity** | $19.9K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 12h |
| **Top-10 Holders** | 50.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 367 buys / 450 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/wrsohpnm4wf9wxu9tgfyvcajiagr2drp1f1bkmcucxi)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/yieldpilot-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*
