---
token: Broke Nigga Baddie
ticker: BNB
network: solana
risk_score: 16
status: low
date: 2026-10-31
---

# Broke Nigga Baddie (BNB) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/broke-nigga-baddie-sol)

---

## Audit Summary

The token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. Liquidity is fully burned, eliminating withdrawal risks, though the high volume-to-liquidity ratio suggests potential wash trading. Third-party risk registry data was unavailable for this assessment.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which may indicate non-organic market activity. Monitor the token's price action and liquidity depth on decentralized exchanges before executing large trades.

Verify the current supply and authority status periodically using a block explorer to ensure no unexpected changes occur, although the current revoked status makes this highly unlikely.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program, which provides advanced extension capabilities. 7.1 Architecture and 7.2 Code Security are robust as both mint and freeze authorities are revoked.… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic analysis shows 100% of pool liquidity is burned, ensuring permanent availability for traders. However, 7.5 Governance and 7.6 External market signals indicate a volume-to-liquidity ratio… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is non-mutable, and no upgradeable extensions were initialized during the mint process. The token state is fixed, providing high… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 30.08, which exceeds the 20x threshold, indicating a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when trading; high volume relative to liquidity can lead to misleading price signals and increased slippage.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $88K (DexScreener, all pools). 24h trading volume $2.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $88K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EYqygb...pump`](https://solscan.io/account/EYqygbhZjP7EbM4fSn8devctnksAvPAD1Bt57XBFpump) |
| **Network** | Solana |
| **Price** | $0.001027 |
| **24h Volume** | $2.61M |
| **Liquidity** | $88.4K |
| **Volume / Liquidity** | 29.5× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 29058 buys / 13346 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/81jgrptmsqwc1rgwxutyyww27ruiatehuzwlydchhwdb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/broke-nigga-baddie-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
