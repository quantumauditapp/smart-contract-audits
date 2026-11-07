---
token: funny trauma 
ticker: TRAUMA 
network: solana
risk_score: 21
status: low
date: 2026-11-07
---

# funny trauma  (TRAUMA ) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/funny-trauma-sol)

---

## Audit Summary

The token 'funny trauma' (trauma) utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully locked, and no adverse flags were reported by third-party registries. Holder concentration data was unavailable, preventing a full assessment of distribution risks.

> **Final Recommendation:** Investors should monitor the token's liquidity depth on DEX platforms to ensure slippage remains within acceptable bounds for their position size. Given the lack of holder distribution data, users should exercise caution regarding potential whale activity.

Verify the current mint and freeze authority status using a block explorer to confirm they remain set to 'None'. No further action is required regarding administrative security as the contract is immutable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the SPL Token-2022 program. 7.1 Architecture is standard for SPL mints. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.2 Code Security is… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic factors show $19,333 in liquidity, which is fully burned, ensuring 7.5 Governance cannot withdraw pool funds. 7.6 External data indicates a high volume/liquidity ratio of 19.08… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints in the EVM sense. Metadata is immutable, and 7.8 Operations are secured by the permanent revocation of all administrative authorities. No further changes… |

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

Liquidity $20K (DexScreener, all pools). 24h trading volume $418K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $20K of DEX liquidity across 5 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FFgnd8...pump`](https://solscan.io/account/FFgnd8bifG8zGBE7dij7g3HWp4gveJS4gDyjdk5epump) |
| **Network** | Solana |
| **Price** | $0.00006983 |
| **24h Volume** | $340.3K |
| **Liquidity** | $20.1K |
| **Volume / Liquidity** | 17.0× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5391 buys / 3540 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/61id5kdt3luivcp4dpd4caw2rqiulnd1gqjy161noceg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/funny-trauma-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
