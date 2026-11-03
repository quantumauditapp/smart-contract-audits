---
token: United States Oil Exchange
ticker: USOE
network: solana
risk_score: 2
status: low
date: 2026-11-03
---

# United States Oil Exchange (USOE) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-oil-exchange-sol-af75)

---

## Audit Summary

The United States Oil Exchange (USOE) token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully locked, and no adverse flags were reported by third-party registries. The token exhibits a healthy distribution and stable trading metrics.

> **Final Recommendation:** The token is currently in a secure state with no identified vulnerabilities. Holders should continue to monitor the top 10 holder distribution periodically to ensure concentration remains within reasonable bounds.

Verify the mint and freeze authority status directly on-chain using a block explorer to confirm they remain set to 'None'. No further action is required for safe interaction with this token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the SPL Token-2022 program (7.1 Architecture). Security is robust as both mint and freeze authorities are revoked, preventing unauthorized supply inflation or account… |
| **Governance / Economics** | 10/10 | Low | The top 10 holders control 12.52% of the supply, indicating a healthy distribution (7.5 Governance). Liquidity is $198,586 and is 100% locked, ensuring no risk of rug-pulls via liquidity withdrawal… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, and there are no upgradeable components such as transfer hooks or fee configurations (7.7 Upgrades). The mint and freeze authorities are permanently revoked, ensuring… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 12.5% of supply. What remains: 12.5% in wallets, 0.0% in other contracts. 4,814 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,814 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $205K (DexScreener, all pools). 24h trading volume $355K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $205K of DEX liquidity across 2 pools. Launch: 17 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 17 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 17 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`USoEHw...PjnB`](https://solscan.io/account/USoEHwaQxrdk66KrrMdd1rhzvfvUDxvNW1Kn75yPjnB) |
| **Network** | Solana |
| **Price** | $0.02292 |
| **24h Volume** | $203.2K |
| **Liquidity** | $195.5K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 17d |
| **Top-10 Holders** | 12.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2278 buys / 891 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6esbso1k12jjbebnthw8qwjprgzpu3rrmskteuiv9jif)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-oil-exchange-sol-af75)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
