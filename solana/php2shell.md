---
token: PHP2SHELL
ticker: PHP2SHELL
network: solana
risk_score: 24
status: low
date: 2026-10-22
---

# PHP2SHELL (PHP2SHELL) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/php2shell-sol)

---

## Audit Summary

The PHP2SHELL token is a Token-2022 asset with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should monitor the token's market activity, as the high volume-to-liquidity ratio may indicate artificial trading patterns. Given the lack of holder concentration data, exercise caution regarding potential whale activity.

Verify the current supply and authority status directly on a Solana block explorer to confirm that the mint and freeze authorities remain null. Do not rely on third-party front-ends for price data if volume appears decoupled from liquidity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program. 7.1 Architecture is standard for SPL mints. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.8 Operations are secure… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows $19,968 in liquidity, which is fully burned and inaccessible to the creator. 7.5 Governance is decentralized due to the lack of minting authority. However, 7.6 External… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint. Metadata is immutable, and no transfer hooks or balance-mutating extensions are active. The token configuration is fixed. |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 81.99, which significantly exceeds the 20x threshold, indicating a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; verify trade history for repetitive or circular patterns.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $1.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 20 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FjLFsa...pump`](https://solscan.io/account/FjLFsaPKSxJGh25iTKCLEkthbeHKLJrxvHyJG9wqpump) |
| **Network** | Solana |
| **Price** | $0.00004388 |
| **24h Volume** | $1.63M |
| **Liquidity** | $18.1K |
| **Volume / Liquidity** | 90.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16439 buys / 12904 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7rruhbymch1q1ktkhyxjqud1ngw1tfbd89jdbttxarwd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/php2shell-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
