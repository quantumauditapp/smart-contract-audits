---
token: AudaCity
ticker: DACITYCOIN
network: solana
risk_score: 15
status: low
date: 2026-10-20
---

# AudaCity (DACITYCOIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/audacity-sol)

---

## Audit Summary

AudaCity is a Token-2022 asset with fully revoked mint and freeze authorities, providing a secure foundation for holders. While the token exhibits a high volume-to-liquidity ratio suggesting potential wash trading, the liquidity is fully burned, preventing rug-pull risks via liquidity withdrawal. No adverse flags were reported by third-party registries.

> **Final Recommendation:** Investors should monitor the high volume-to-liquidity ratio, as it may indicate artificial market activity that does not reflect organic demand. Verify the token mint address directly on a block explorer to ensure no secondary minting or unexpected state changes have occurred.

Given the immutable nature of the contract, no further on-chain actions are required to secure the token. Users should rely on official project channels for metadata verification, as the contract's metadata is locked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program, ensuring compatibility with advanced extensions. 7.1 Architecture and 7.2 Code Security are standard for this program version. 7.3 Access Control is… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance metrics show a healthy distribution, with the top 10 holders controlling 17.55% of the supply. 7.6 External market data indicates $55,358 in liquidity, which is 100%… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is immutable, preventing unauthorized changes to the token identity. There are no upgradeable transfer hooks or fee configurations… |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 26.78, which exceeds the 20x threshold, indicating a pattern associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting market volume; perform independent analysis of trade history to distinguish between organic and automated activity.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 28.7% of supply. Of that, 11.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 17.6% in wallets, 0.0% in other contracts. 1,260 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,260 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $65K (DexScreener, all pools). 24h trading volume $1.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $65K of DEX liquidity across 5 pools. Launch: launched on pump.fun, 5 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 5 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 5 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DKYcjo...pump`](https://solscan.io/account/DKYcjobF7HPtL9RyQBRdeRQ2iWvizpfbgWwPWNXdpump) |
| **Network** | Solana |
| **Price** | $0.0003725 |
| **24h Volume** | $1.44M |
| **Liquidity** | $63.6K |
| **Volume / Liquidity** | 22.6× |
| **Token Age** | 5d |
| **Top-10 Holders** | 28.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6370 buys / 4732 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7te1wxcfeqjklghxfvxscngztqunoz9fxbn7kkjrkner)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/audacity-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
