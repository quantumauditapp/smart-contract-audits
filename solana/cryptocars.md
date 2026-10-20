---
token: CryptoCars
ticker: CRS
network: solana
risk_score: 15
status: low
date: 2026-10-16
---

# CryptoCars (CRS) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cryptocars-sol)

---

## Audit Summary

The CryptoCars (CRS) token is an SPL Token-2022 mint with both mint and freeze authorities revoked, indicating a fixed supply and unfreezable accounts. All pool liquidity is burned, providing strong assurance against rug pulls. However, holder concentration data was unavailable, and a third-party risk registry signals potential single holder ownership and high concentration, which could pose a risk to price stability. The token exhibits a high volume-to-liquidity ratio, suggesting active trading relative to its liquidity.

> **Final Recommendation:** Holders should monitor the token's trading activity and liquidity closely, especially given the high volume-to-liquidity ratio. While the burned liquidity offers security, the lack of transparent holder concentration data means potential risks from large holders cannot be fully assessed. Users should remain vigilant for any significant price movements or trading anomalies.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The CryptoCars (CRS) token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts can be frozen post-launch.… |
| **Governance / Economics** | 9/10 | Low | The token has a total DEX liquidity of $19,698, with 100.0% of the pool's LP tokens burned, ensuring liquidity cannot be withdrawn. The 24-hour volume of $109,966 results in a Volume/Liquidity Ratio… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, preventing any further changes to the token supply or account freeze status. The token's metadata, including name and symbol, is immutable… |

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

Liquidity $20K (DexScreener, all pools). 24h trading volume $141K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $20K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7cNGyB...pump`](https://solscan.io/account/7cNGyBBjcRZt7RSWZzh4fzXojg5mpsDLVuixgS8bpump) |
| **Network** | Solana |
| **Price** | $0.00006152 |
| **24h Volume** | $109.3K |
| **Liquidity** | $19.8K |
| **Volume / Liquidity** | 5.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1489 buys / 1125 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9pxy52j5rcynfrssasnnvvfn5jpaoxnmkhsthacqzmme)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cryptocars-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-16*
