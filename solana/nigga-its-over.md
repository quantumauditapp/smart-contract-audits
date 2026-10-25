---
token: Nigga Its Over
ticker: NIO
network: solana
risk_score: 16
status: low
date: 2026-10-25
---

# Nigga Its Over (NIO) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nigga-its-over-sol)

---

## Audit Summary

The token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. However, the token is flagged as high-risk by a third-party registry due to the creator's history of rug-pulling, and the trading activity exhibits a high volume-to-liquidity ratio indicative of potential wash trading. While liquidity is fully burned, the external security signals regarding developer history necessitate extreme caution.

> **Final Recommendation:** Given the third-party registry flag regarding developer history, users should exercise extreme caution and perform independent due diligence before interacting with this asset. Monitor the token's price action for signs of artificial volume manipulation.

Verify the current mint and freeze authority status on-chain to ensure they remain null. Do not rely on the token's metadata as a guarantee of legitimacy, as external risk signals suggest a high probability of malicious intent by the deployer.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is built on the SPL Token-2022 standard. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is inherent to the standard… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic analysis shows a volume/liquidity ratio of 20.27, exceeding the 20 threshold for wash-trading signals. 7.5 Governance is decentralized as the creator cannot withdraw liquidity, with 100%… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a standard SPL token. 7.8 Operations are stable, with metadata mutability set to false, preventing future changes to token branding. |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 6 Informational_

### `C-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on the developer's history of creating rugged tokens.

**Recommendation:** Do not interact with this token.


### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 20.27, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for potential price manipulation and lack of organic demand in any swap calculation.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 25.1% of supply. Of that, 7.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 17.3% in wallets, 0.0% in other contracts. 1,386 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,386 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 81% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $60K (DexScreener, all pools). 24h trading volume $982K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $60K of DEX liquidity across 26 pools. Launch: launched on pump.fun, 4 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7SL2Vn...pump`](https://solscan.io/account/7SL2VnfYsChvog5oQY9Nmtqu1wceaMiQzWoqoLQpump) |
| **Network** | Solana |
| **Price** | $0.0003019 |
| **24h Volume** | $880.5K |
| **Liquidity** | $48.5K |
| **Volume / Liquidity** | 18.2× |
| **Token Age** | 4d |
| **Top-10 Holders** | 25.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6755 buys / 5885 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/b4wmjc6pvjctu3qsvs3ett9mr4m5v5jbkrqctwantc71)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nigga-its-over-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
