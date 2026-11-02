---
token: Just Stealth It
ticker: STEALTH
network: solana
risk_score: 15
status: low
date: 2026-11-02
---

# Just Stealth It (STEALTH) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/just-stealth-it-sol)

---

## Audit Summary

The STEALTH token is a Token-2022 asset with both mint and freeze authorities successfully revoked. Liquidity is fully burned, eliminating withdrawal risk, though high volume relative to liquidity suggests potential wash trading. Holder concentration data is unavailable, and no adverse flags were reported by third-party registries.

> **Final Recommendation:** Investors should monitor the token's trading activity, as the high volume-to-liquidity ratio may indicate artificial market manipulation. Verify the current holder distribution via block explorers if this data becomes available to ensure supply is not overly concentrated.

Since authorities are revoked and liquidity is burned, the primary remaining risks are market-driven rather than technical. Ensure all transactions are executed through reputable DEX interfaces to avoid potential front-running or slippage issues associated with low-liquidity environments.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control is robust as both… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic stability is supported by 100% burned liquidity, ensuring the pool cannot be drained by the creator. 7.5 Governance is decentralized due to the lack of administrative authorities.… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is a standard SPL token. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is fixed and cannot be altered by any… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 30.19, which exceeds the 20x threshold, indicating a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when evaluating market demand; do not rely solely on volume metrics as a proxy for organic interest.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 87% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $68K (DexScreener, all pools). 24h trading volume $1.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $68K of DEX liquidity across 12 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GoDSW3...BmoA`](https://solscan.io/account/GoDSW31bTxfkoup9yA1qcGGx9RMXdTEWgApv3xzBmoA) |
| **Network** | Solana |
| **Price** | $0.0004719 |
| **24h Volume** | $1.60M |
| **Liquidity** | $59.8K |
| **Volume / Liquidity** | 26.7× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16802 buys / 11777 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/e6rfkjwdbjrype4xwndyu4qyyh1nywzhxzunufeifylx)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/just-stealth-it-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
