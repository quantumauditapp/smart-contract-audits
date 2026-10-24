---
token: Why would I deceive you?
ticker: ELIZABETH
network: solana
risk_score: 13
status: low
date: 2026-10-24
---

# Why would I deceive you? (ELIZABETH) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/why-would-i-deceive-you-sol)

---

## Audit Summary

The ELIZABETH token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. While the token exhibits a high volume-to-liquidity ratio suggesting potential wash trading, the liquidity is fully burned, preventing rug pulls via liquidity withdrawal. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should monitor the token's trading volume, as the high volume-to-liquidity ratio is a strong indicator of artificial activity. Given the lack of holder concentration data, users should exercise caution regarding potential whale activity that may not be visible in current market metrics.

Verify the current mint and freeze authority status on-chain using a block explorer to confirm they remain null. No further administrative actions are required for this token as the current configuration is immutable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program with no active transfer hooks or default frozen account states. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic analysis shows a volume/liquidity ratio of 39.50, which exceeds the 20x threshold and indicates potential wash trading. 7.5 Governance is decentralized by the revocation of authorities.… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL mint. Metadata is immutable, and no balance-mutating authorities exist. The token configuration is final and cannot be altered by the… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 39.50, which is significantly higher than the 20x threshold, indicating potential wash trading activity.

**Recommendation:** Exercise caution when evaluating market demand, as volume may not reflect organic interest.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 71% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $66K (DexScreener, all pools). 24h trading volume $1.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $66K of DEX liquidity across 24 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Biiv46...pump`](https://solscan.io/account/Biiv46yBzZwwdg3HvYQ52yPXmnMb5EnF8dboTx2qpump) |
| **Network** | Solana |
| **Price** | $0.0002893 |
| **24h Volume** | $1.37M |
| **Liquidity** | $47.4K |
| **Volume / Liquidity** | 28.9× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16895 buys / 12596 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7sqcc11sheno53ksnsrdivaiu36t3bkqbcclm5vefzrm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/why-would-i-deceive-you-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
