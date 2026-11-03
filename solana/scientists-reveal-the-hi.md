---
token: Scientists Reveal the Hi
ticker: HI
network: solana
risk_score: 24
status: low
date: 2026-11-03
---

# Scientists Reveal the Hi (HI) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/scientists-reveal-the-hi-sol)

---

## Audit Summary

The token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the high volume-to-liquidity ratio suggests potential wash trading activity. Holder distribution data was unavailable from the provided sources.

> **Final Recommendation:** Investors should monitor the token's market activity, as the high volume-to-liquidity ratio may indicate artificial trading patterns. Since liquidity is fully burned, the pool is protected from creator withdrawal, but users should remain cautious of price volatility due to the low total liquidity.

Verify the current supply and authority status using a block explorer to confirm that no new tokens can be minted and that the freeze authority remains null. Always check the latest holder distribution if it becomes available to ensure no single wallet controls a majority of the circulating supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed using the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for the… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows $11,743 in liquidity, which is fully burned and inaccessible to the creator. 7.5 Governance is decentralized due to the lack of administrative authorities. However, 7.6… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL token mint. Metadata is immutable, and there are no upgradeable extensions or transfer hooks present. The token state is fixed and cannot be… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 26.58, which exceeds the 20x threshold, indicating potential wash trading activity.

**Recommendation:** Monitor trading volume for sustainability and exercise caution regarding potential price manipulation.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $310K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6Jrsvi...pump`](https://solscan.io/account/6JrsviCgzki77Zr35RBGYpuKDGo628hDYDCuB7mBpump) |
| **Network** | Solana |
| **Price** | $0.00006308 |
| **24h Volume** | $298.0K |
| **Liquidity** | $19.2K |
| **Volume / Liquidity** | 15.5× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5958 buys / 4716 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hxwsurjuendwcg4duhnatpxk7mpzto49nheezhzbpfay)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/scientists-reveal-the-hi-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
