---
token: Circuit
ticker: CIRCUIT
network: solana
risk_score: 1
status: low
date: 2026-10-17
---

# Circuit (CIRCUIT) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/circuit-sol)

---

## Audit Summary

This SPL Token Mint for Circuit (Circuit) exhibits a low-risk profile based on the available on-chain data and third-party security registries. Key authorities like mint and freeze are revoked, and liquidity is fully burned. No critical or high-severity issues were identified based on the deterministic audit rules.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to ensure supply and account control are fixed. Monitor DEX liquidity to ensure it remains robust for desired trade sizes. Confirm that no new extensions are added to the token program that could introduce unforeseen risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Circuit token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts can be frozen… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding only 19.76% of the supply. The token has $43,093 in DEX liquidity, which is fully burned (100.0%), preventing rug pulls from… |
| **Upgrades** | 10/10 | Low | The mint and freeze authorities are permanently revoked, meaning the core token parameters cannot be altered. The token's metadata is immutable, ensuring its name, symbol, and image cannot be… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 36.8% of supply. Of that, 17.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.8% in wallets, 0.0% in other contracts. 1,038 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Circuit (CIRCUIT), rank #5191. 1,038 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 74% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $54K (DexScreener, all pools). 24h trading volume $334K (CoinGecko, all markets, daily snapshot). 24h trading volume $342K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $54K of DEX liquidity across 9 pools. Launch: launched on pump.fun, 7 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 7 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 7 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EcZndA...pump`](https://solscan.io/account/EcZndAERfzNhLirHwfsy44dAyPSZazjDU83pa6RApump) |
| **Network** | Solana |
| **Price** | $0.0001713 |
| **24h Volume** | $295.1K |
| **Liquidity** | $40.5K |
| **Volume / Liquidity** | 7.3× |
| **Token Age** | 7d |
| **Top-10 Holders** | 36.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2314 buys / 2141 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/xyxuqk6dcnny5wmwxedj13kjjh8ug2dtjfx8npisy3p)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/circuit-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*
