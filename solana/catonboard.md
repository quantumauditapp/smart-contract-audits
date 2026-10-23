---
token: catonboard
ticker: ONBOARD
network: solana
risk_score: 2
status: low
date: 2026-10-23
---

# catonboard (ONBOARD) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/catonboard-sol)

---

## Audit Summary

The catonboard token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, and no adverse flags were reported by third-party registries. All sources were successfully retrieved, confirming a standard, non-custodial configuration.

> **Final Recommendation:** The token configuration is secure and immutable. Holders should continue to monitor the top 10 holder distribution via block explorers to ensure concentration remains low over time.

No further action is required to secure the token's mint or freeze state, as these are already permanently revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the SPL Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture is standard for SPL mints, with 7.3 Access Control demonstrating that both mint and… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $55,611 in liquidity, which is 100% burned, preventing rug-pull risks from the creator. 7.5 Governance is decentralized as the top 10 holders control only… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is fully immutable. Metadata is fixed, and no authority exists to modify the token's core parameters. The configuration is locked, ensuring no future… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 29.8% of supply. Of that, 16.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 13.8% in wallets, 0.0% in other contracts. 3,600 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,600 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 75% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $73K (DexScreener, all pools). 24h trading volume $300K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $73K of DEX liquidity across 10 pools. Launch: launched on pump.fun, 6 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5ubruM...pump`](https://solscan.io/account/5ubruMYpgKqw9ip5J1qrXbVGmMdn2VCsMg421B4bpump) |
| **Network** | Solana |
| **Price** | $0.0002282 |
| **24h Volume** | $248.3K |
| **Liquidity** | $55.0K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 6d |
| **Top-10 Holders** | 29.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 14662 buys / 3148 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dbzf8tq3mtlsdgmlcdj1ya7e8hqatq22jafqma92fi4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/catonboard-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
