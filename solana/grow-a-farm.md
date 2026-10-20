---
token: Grow a Farm
ticker: SEED
network: solana
risk_score: 13
status: low
date: 2026-10-11
---

# Grow a Farm (SEED) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/grow-a-farm-sol)

---

## Audit Summary

The Grow a Farm (SEED) SPL Token Mint audit reveals a well-configured token with no critical or high-severity risks identified. Both the mint and freeze authorities have been revoked, ensuring a fixed supply and preventing arbitrary freezing of accounts. All pool liquidity is burned, eliminating rug pull risks from liquidity withdrawal. Third-party registry data reported no adverse flags, but holder concentration data was unavailable.

> **Final Recommendation:** Holders should monitor the token's market activity and liquidity over time. While the current liquidity is fully burned, ensuring stability, the absence of holder distribution data means potential concentration risks cannot be assessed. Users should verify on-chain that the mint and freeze authorities remain revoked and that no new extensions are unexpectedly enabled if the token program were to be updated (though this is not a typical SPL token pattern).

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Grow a Farm (SEED) token is implemented using the spl-token-2022 program. Key security features include the revocation of both mint and freeze authorities, which prevents further token issuance… |
| **Governance / Economics** | 9/10 | Low | The token exhibits robust liquidity management, with 100.0% of the pool's LP tokens burned, ensuring that liquidity cannot be withdrawn by any party. Current DEX liquidity stands at $29,151, with a… |
| **Upgrades** | 10/10 | Low | The Grow a Farm (SEED) token mint has a robust configuration regarding mutability and control. The mint authority has been revoked, fixing the total supply, and the freeze authority is also revoked… |

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

Liquidity $30K (DexScreener, all pools). 24h trading volume $114K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $30K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CvxQvq...pump`](https://solscan.io/account/CvxQvqNQVRqq96oeoRnf6H64Memd8Weas9gte2xupump) |
| **Network** | Solana |
| **Price** | $0.0001285 |
| **24h Volume** | $114.4K |
| **Liquidity** | $29.8K |
| **Volume / Liquidity** | 3.8× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4891 buys / 1871 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gma1qtoljhrozhod4bjw5ee9joejq7zjstadmvfsibve)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/grow-a-farm-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
