---
token: Mr Veto
ticker: VETO
network: solana
risk_score: 27
status: low
date: 2026-11-04
---

# Mr Veto (VETO) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mr-veto-sol)

---

## Audit Summary

The Mr Veto (VETO) token is a Token-2022 asset with both mint and freeze authorities successfully revoked. While the token exhibits a high volume-to-liquidity ratio suggesting potential wash trading, the liquidity itself is 100% burned, preventing rug-pulls via liquidity withdrawal. No adverse flags were reported by third-party registries.

> **Final Recommendation:** Investors should monitor the high volume-to-liquidity ratio, as it indicates that reported trading activity may not reflect organic market demand. Given that liquidity is fully burned, the primary risk is price volatility rather than protocol-level rug-pulls.

Verify the current holder distribution using a block explorer to ensure that the top 10 holders are not accumulating further supply. No further on-chain action is required to secure the token, as the mint and freeze authorities are already permanently revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control is robust, as both mint and… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic factors show a concentration of 22.99% among the top 10 holders. 7.5 Governance is decentralized due to authority revocation. 7.6 External market data indicates a volume/liquidity ratio… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL tokens do not use proxy patterns. Metadata is immutable, and extension configurations such as transfer fees and hooks are non-upgradable. The token state is… |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 32.47, exceeding the 20x threshold. This pattern is strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; perform independent analysis of trade frequency and order book depth.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 35.3% of supply. Of that, 12.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.0% in wallets, 0.0% in other contracts. 1,096 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,096 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $42K (DexScreener, all pools). 24h trading volume $1.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $42K of DEX liquidity across 10 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4xWRsd...pump`](https://solscan.io/account/4xWRsdRkre5ibf3ZyS2eje6sUY8wGnmtSHx7gkGtpump) |
| **Network** | Solana |
| **Price** | $0.0002026 |
| **24h Volume** | $1.39M |
| **Liquidity** | $41.9K |
| **Volume / Liquidity** | 33.2× |
| **Token Age** | 2d |
| **Top-10 Holders** | 35.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8990 buys / 6667 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dok34bzdnveaijtseonxwcqwamezp5ifn9zsjjvtjqzq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mr-veto-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
