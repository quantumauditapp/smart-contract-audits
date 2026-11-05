---
token: im tired boss
ticker: TIRED
network: solana
risk_score: 20
status: low
date: 2026-11-05
---

# im tired boss (TIRED) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/im-tired-boss-sol)

---

## Audit Summary

The TIRED token is a standard SPL-2022 mint with both mint and freeze authorities successfully revoked. Liquidity is fully burned, eliminating withdrawal risks, though the high volume-to-liquidity ratio suggests potential wash trading. Holder distribution data was unavailable from the RPC source.

> **Final Recommendation:** Investors should monitor the token's market activity, as the high volume-to-liquidity ratio is a strong indicator of wash trading. While the liquidity is safely burned, the lack of holder distribution data requires caution regarding potential whale concentration.

Verify the current supply and authority status directly via a block explorer to ensure no unexpected changes have occurred. Do not rely solely on DEX-reported volume metrics when assessing the token's true market demand.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL-2022 program with no active extensions like transfer hooks or default frozen states. 7.1 Architecture is standard for SPL tokens. 7.3 Access Control is robust as both mint… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows $27,131 in liquidity, which is fully burned and inaccessible to the creator. 7.6 External market data indicates a volume/liquidity ratio of 53.10, which is significantly… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is a static SPL token. Metadata and balance-mutating authorities are disabled, ensuring the token configuration cannot be altered post-launch. The token is… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 53.10, exceeding the 20 threshold, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting trading volume as a proxy for organic market interest.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $32K (DexScreener, all pools). 24h trading volume $1.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $32K of DEX liquidity across 30 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Bmhp8n...pump`](https://solscan.io/account/Bmhp8nat7zTFu3Ct8HpQftiHHmB6dnf4B9ivvYYzpump) |
| **Network** | Solana |
| **Price** | $0.0001356 |
| **24h Volume** | $1.42M |
| **Liquidity** | $31.1K |
| **Volume / Liquidity** | 45.9× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 19309 buys / 13937 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/47xilcq44pv1f7yu4jrssj7czcuffdfyzmxh5gt4tian)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/im-tired-boss-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*
