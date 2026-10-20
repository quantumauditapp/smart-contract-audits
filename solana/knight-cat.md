---
token: Knight Cat
ticker: KNIGHTCAT
network: solana
risk_score: 12
status: low
date: 2026-10-04
---

# Knight Cat (KNIGHTCAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/knight-cat-sol)

---

## Audit Summary

The Knight Cat SPL Token Mint has revoked its mint and freeze authorities, indicating a fixed supply and unfreezable accounts. No critical Token-2022 extensions like permanent delegate or transfer hook are active. Holder concentration data and liquidity locking status were unavailable for this assessment.

> **Final Recommendation:** Holders should monitor for the availability of holder distribution data to assess potential concentration risks. Additionally, verify on-chain the status of the pool's liquidity to confirm if it is burned or locked, as this information was not available during this audit.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Knight Cat token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring that no new tokens can be minted and no existing token… |
| **Governance / Economics** | 7/10 | Low | The token has a liquidity of $183,419 USD, which is not considered very low. The 24-hour volume to liquidity ratio is 5.33, which is not indicative of wash trading (threshold > 20). Information… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority for the Knight Cat token have both been revoked, preventing any further changes to the token's supply or the ability to freeze accounts. The token's metadata… |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $373K (DexScreener, all pools). 24h trading volume $10.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $373K of DEX liquidity across 7 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3Dgwn5...pump`](https://solscan.io/account/3Dgwn5E7H5a8k6iGrz3qirkaJqUaJrKHEZ2xPcLRpump) |
| **Network** | Solana |
| **Price** | $0.002439 |
| **24h Volume** | $967.3K |
| **Liquidity** | $191.2K |
| **Volume / Liquidity** | 5.1× |
| **Token Age** | 15h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2518 buys / 2888 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/awmawjsrq55hygjfihcqtwzqx9qlbtgzhpqnjhjdppkz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/knight-cat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-04*
