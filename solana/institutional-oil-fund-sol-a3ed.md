---
token: Institutional Oil Fund
ticker: IOF
network: solana
risk_score: 0
status: low
date: 2026-10-30
---

# Institutional Oil Fund (IOF) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/institutional-oil-fund-sol-a3ed)

---

## Audit Summary

The Institutional Oil Fund (IOF) token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating risks of rug-pulls via liquidity withdrawal. Holder distribution data was unavailable, and a third-party registry flagged high holder correlation, which warrants caution regarding potential market manipulation.

> **Final Recommendation:** Investors should monitor on-chain holder movements to verify if the 'high holder correlation' signal translates into actual market concentration. Since the mint and freeze authorities are revoked, the token's technical parameters are secure from developer interference.

Verify the current holder distribution using block explorers to assess the impact of the flagged holder correlation. Ensure that any future interactions with the token are based on independent analysis of the liquidity pool's performance rather than relying solely on the current volume metrics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring supply immutability and preventing account freezing (7.3 Access… |
| **Governance / Economics** | 10/10 | Low | Liquidity is robust at $272,959 with 100% of LP tokens burned, ensuring permanent availability (7.4 Economic). Trading volume is healthy relative to liquidity (7.6 External). However, a third-party… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, and no upgradeable extensions are configured (7.7 Upgrades). The mint state is finalized, preventing future modifications to token parameters (7.8 Operations). |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — High Holder Correlation  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, which may indicate that a significant portion of the supply is controlled by a small group of entities.

**Recommendation:** Monitor the top holder accounts for coordinated activity and assess the risk of price volatility resulting from concentrated selling pressure.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $271K (DexScreener, all pools). 24h trading volume $225K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $271K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AcBX8a...pump`](https://solscan.io/account/AcBX8a8eHbzQghgqMfqXeAz4kQSRbtHWKUSGXvwMpump) |
| **Network** | Solana |
| **Price** | $0.0109 |
| **24h Volume** | $224.5K |
| **Liquidity** | $270.8K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 13h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 25971 buys / 1555 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ffx248swf7spygcuapyksn7bmx8x5hvid5b7znfe3mbs)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/institutional-oil-fund-sol-a3ed)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
