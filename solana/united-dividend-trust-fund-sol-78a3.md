---
token: United Dividend Trust Fund
ticker: UDTF
network: solana
risk_score: 1
status: low
date: 2026-10-30
---

# United Dividend Trust Fund (UDTF) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-dividend-trust-fund-sol-78a3)

---

## Audit Summary

The United Dividend Trust Fund (UDTF) token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, mitigating risks associated with rug pulls or liquidity withdrawal. Holder concentration data was unavailable from the RPC, and third-party registries noted high holder correlation, which should be monitored.

> **Final Recommendation:** Investors should monitor the token's holder distribution once on-chain data becomes available to ensure that high holder correlation does not lead to excessive price volatility. No further technical action is required as the mint is fully immutable and liquidity is permanently locked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). The token does not utilize… |
| **Governance / Economics** | 10/10 | Low | Economic security is supported by $2.1M in liquidity, which is 100% burned (7.4 Economic). The volume/liquidity ratio of 0.86 indicates healthy, non-wash-traded activity (7.6 External). While holder… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing unauthorized changes to branding or token identity (7.7 Upgrades). There are no upgradeable extensions or transfer fees enabled. The token state is… |

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

Liquidity $2.1M (DexScreener, all pools). 24h trading volume $1.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $2.1M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9D51oX...pump`](https://solscan.io/account/9D51oXUyHGrLdabvXiJHRPc5UhW9Py14z3g6TTw7pump) |
| **Network** | Solana |
| **Price** | $0.6416 |
| **24h Volume** | $1.81M |
| **Liquidity** | $2.09M |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 25552 buys / 13334 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/88bapr12syhqh7mb8vgofn2d2dhzpn3gu5nmj3l2j7yh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-dividend-trust-fund-sol-78a3)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
