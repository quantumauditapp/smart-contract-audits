---
token: Frongus
ticker: FRONGUS
network: solana
risk_score: 5
status: low
date: 2026-10-28
---

# Frongus (FRONGUS) — Smart Contract Security Analysis | Solana

> **Risk Score: 5/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/frongus-sol-98d3)

---

## Audit Summary

The Frongus token utilizes the SPL Token-2022 program with all administrative authorities, including mint and freeze, successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, mitigating rug-pull risks. While third-party registry data indicates high holder correlation, the overall security posture is robust due to the immutable nature of the mint configuration.

> **Final Recommendation:** The token is currently in a secure state with no active administrative risks. Holders should monitor the top 10 wallet addresses periodically to ensure that the high holder correlation does not lead to excessive market volatility.

No further action is required regarding contract security. Future interactions should focus on monitoring market-wide liquidity trends and verifying that no new, unexpected token extensions are introduced if the program were to support them in future protocol updates.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program, ensuring modern extension support. 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is fully restricted as… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic factors are favorable, with 100% of pool liquidity permanently burned. 7.5 Governance is decentralized by the lack of mint authority. 7.6 External signals show a volume/liquidity ratio… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is fixed and cannot be altered, preventing branding risks. No upgradeable extensions are enabled, ensuring long-term consistency. |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `M-01` — High Holder Correlation  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by related entities.

**Recommendation:** Monitor on-chain wallet activity for coordinated movements that could indicate potential market manipulation.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 24.6% of supply. Of that, 1.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.9% in wallets, 0.0% in other contracts. 2,342 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,342 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $234K (DexScreener, all pools). 24h trading volume $116K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $234K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AV3iJm...pump`](https://solscan.io/account/AV3iJmpLP8AzKBCREoiaPYDsSn5y9GDeemS1AnQJpump) |
| **Network** | Solana |
| **Price** | $0.007705 |
| **24h Volume** | $115.6K |
| **Liquidity** | $233.7K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 23h |
| **Top-10 Holders** | 24.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9797 buys / 8281 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gzpparuujh44x9tz7lu5ni7b5qxyfayprshnomdk1ug8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/frongus-sol-98d3)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
