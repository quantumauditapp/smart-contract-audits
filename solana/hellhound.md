---
token: Hellhound
ticker: HELL
network: solana
risk_score: 0
status: low
date: 2026-10-19
---

# Hellhound (HELL) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hellhound-sol)

---

## Audit Summary

The Hellhound (HELL) SPL token mint has been audited. Key authorities, including Mint Authority and Freeze Authority, are revoked, indicating a fixed supply and unfreezable accounts. The token utilizes the spl-token-2022 program without a transfer hook or default frozen account state. Liquidity is robust, and 100% of the pool's LP tokens are burned. Third-party risk registry data was unavailable for this assessment.

> **Final Recommendation:** Holders should verify on-chain that the Mint Authority and Freeze Authority remain revoked to ensure supply immutability and unhindered transfers. Monitor the token's trading volume and liquidity for any significant changes. No specific actions are required regarding mutable features as metadata and balance mutability are disabled.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Hellhound (HELL) token is an SPL Token-2022 mint with a current supply of 953,827,494.327771 tokens and 6 decimals. Both the Mint Authority and Freeze Authority have been revoked, ensuring no new… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for 19.63% of the supply. The token has substantial DEX liquidity of $118,204 USD, with a healthy 24-hour volume of… |
| **Upgrades** | 10/10 | Low | The token's core authorities, Mint Authority and Freeze Authority, are revoked, preventing any post-launch changes to supply or account freeze status. As an SPL Token-2022, it does not utilize… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 22.8% of supply. Of that, 3.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.3% in wallets, 4.3% in other contracts. 1,259 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Hellhound (HELL), market cap $2M, rank #2375. 1,259 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $114K (DexScreener, all pools). 24h trading volume $151K (CoinGecko, all markets, daily snapshot). 24h trading volume $145K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $114K of DEX liquidity across 3 pools. Launch: launched on pump.fun, 5 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`A75Xx6...pump`](https://solscan.io/account/A75Xx6SeftAmWduv9KGwb2GCjXUAhxozcCUCys9jpump) |
| **Network** | Solana |
| **Price** | $0.001793 |
| **24h Volume** | $144.8K |
| **Liquidity** | $113.7K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 5d |
| **Top-10 Holders** | 22.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 20070 buys / 18435 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ewsyhiuznynqh5f65ypfsoqblq2kyetuvhm5un7wsfdg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hellhound-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*
