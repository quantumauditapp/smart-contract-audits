---
token: Anthropic IPO
ticker: ANT
network: solana
risk_score: 16
status: low
date: 2026-10-26
---

# Anthropic IPO (ANT) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anthropic-ipo-sol)

---

## Audit Summary

The Anthropic IPO (ANT) token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating rug-pull risks associated with pool withdrawal. Holder concentration data is unavailable, and the high volume-to-liquidity ratio suggests potential wash-trading activity.

> **Final Recommendation:** Investors should monitor the token's market activity, specifically the high volume-to-liquidity ratio, which may indicate artificial trading patterns. Since holder concentration data is unavailable, users should exercise caution regarding potential whale activity that could impact price stability.

Verify the current supply and authority status directly via a block explorer to confirm that no new tokens can be minted. Given the lack of holder distribution data, perform independent analysis of the top token accounts before committing significant capital.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is robust, as… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic factors show $129,671 in liquidity, which is fully burned, preventing creator withdrawal. 7.5 Governance is decentralized due to the lack of administrative authorities. However, 7.6… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the token utilizes a fixed SPL program. Metadata is immutable, and no upgradeable extensions (such as transfer fees or hooks) are enabled. The configuration is… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 25.91, which exceeds the 20x threshold, indicating a pattern associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; verify trade history for repetitive, non-organic patterns.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $145K (DexScreener, all pools). 24h trading volume $3.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $145K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`VFck39...pump`](https://solscan.io/account/VFck39CHFLoX74ws4YzioK61TAGe1QTQB3tma7Rpump) |
| **Network** | Solana |
| **Price** | $0.002631 |
| **24h Volume** | $3.09M |
| **Liquidity** | $144.6K |
| **Volume / Liquidity** | 21.3× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 23267 buys / 7733 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cqgjkah8varfsvhaj5we1pdyvbv842qcyimtpf1k9jc8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anthropic-ipo-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
