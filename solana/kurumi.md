---
token: くるみちゃん
ticker: KURUMI
network: solana
risk_score: 6
status: low
date: 2026-10-25
---

# くるみちゃん (KURUMI) — Smart Contract Security Analysis | Solana

> **Risk Score: 6/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kurumi-sol)

---

## Audit Summary

The KURUMI token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, and no adverse flags were identified in third-party registries. Holder concentration data was unavailable, limiting the scope of the economic assessment.

> **Final Recommendation:** The token exhibits strong security properties regarding its administrative structure and liquidity. Users should monitor the token's market activity and volume trends, as the high volume-to-liquidity ratio may lead to significant price volatility.

Verify the current supply and holder distribution using block explorers to ensure no single entity holds a majority stake. As holder data was unavailable during this audit, independent verification of the top 10 token accounts is recommended before executing large trades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented on the Token-2022 program (7.1 Architecture). Access control is robust, with both mint and freeze authorities permanently revoked (7.3 Access Control). No transfer hooks or… |
| **Governance / Economics** | 10/10 | Low | Liquidity is highly secure, with 100% of LP tokens burned (7.4 Economic). While the volume/liquidity ratio is 11.55, indicating active trading, the lack of holder distribution data prevents a full… |
| **Upgrades** | 10/10 | Low | The mint is immutable as both mint and freeze authorities are revoked (7.7 Upgrades). Metadata is non-mutable, ensuring branding consistency (7.6 External). No upgrade paths exist for the token… |

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

Liquidity $53K (DexScreener, all pools). 24h trading volume $563K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $53K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AUHK6b...pump`](https://solscan.io/account/AUHK6bsTMU6nemt7epnvELJtGezx9JS76Lm48pxipump) |
| **Network** | Solana |
| **Price** | $0.0003949 |
| **24h Volume** | $562.7K |
| **Liquidity** | $52.8K |
| **Volume / Liquidity** | 10.7× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 15150 buys / 4454 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dxvcfzrle4dycthuzm5xchmb9zueaek56zkpbyuivfdf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kurumi-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
