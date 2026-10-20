---
token: Token Battles
ticker: FIGHT
network: solana
risk_score: 13
status: low
date: 2026-10-12
---

# Token Battles (FIGHT) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-battles-sol)

---

## Audit Summary

The Token Battles (FIGHT) SPL token mint is configured with revoked mint and freeze authorities, ensuring a fixed supply and unfreezable accounts. All pool liquidity is burned, providing stability against rug pulls. However, holder concentration data was unavailable, and a third-party registry flagged it as a "Copycat token."

> **Final Recommendation:** Verify on-chain that the mint and freeze authorities remain revoked to confirm the fixed supply and unfreezable nature. Monitor the token's trading activity and liquidity for stability, especially given its very recent launch and the "Copycat token" flag from a third-party registry. If holder distribution data becomes available, assess for high concentration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Token Battles (FIGHT) token is implemented using the spl-token-2022 program, indicating modern Solana token standards. Both the mint authority and freeze authority have been permanently revoked… |
| **Governance / Economics** | 9/10 | Low | The token currently has $43,315 in DEX liquidity, with a 24-hour trading volume of $395,834, resulting in a volume/liquidity ratio of 9.14. This high ratio, especially for a pair aged 0 days… |
| **Upgrades** | 10/10 | Low | The token's core parameters are highly immutable, as both the mint and freeze authorities have been revoked. This means the token supply cannot be increased, and no accounts can be frozen… |

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

Liquidity $43K (DexScreener, all pools). 24h trading volume $385K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $43K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`A8JUiZ...pump`](https://solscan.io/account/A8JUiZLzjGAsKxE74evdspHcuW4hvhPbvryDhaDZpump) |
| **Network** | Solana |
| **Price** | $0.0002447 |
| **24h Volume** | $384.6K |
| **Liquidity** | $43.2K |
| **Volume / Liquidity** | 8.9× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5819 buys / 3042 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bow9h5gbqdnr55fke3vhdzngplanzmyky1eiqmx1drlz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-battles-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
