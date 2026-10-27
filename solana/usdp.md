---
token: USDP
ticker: USDP
network: solana
risk_score: 90
status: critical
date: 2026-10-27
---

# USDP (USDP) — Smart Contract Security Analysis | Solana

> **Risk Score: 90/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usdp-sol)

---

## Audit Summary

The USDP token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, mitigating withdrawal risks. Holder distribution data was unavailable, and third-party registries indicate high holder correlation, which should be monitored.

> **Final Recommendation:** Investors should monitor the token's market activity via block explorers to track holder concentration as it develops, given the current lack of distribution data. Since the mint is immutable and liquidity is burned, the primary remaining risk is market volatility associated with the flagged high holder correlation.

Verify the current supply and authority status directly on-chain using a block explorer to confirm that the mint and freeze authorities remain null. Do not rely on third-party front-ends for metadata; always verify the mint address against official project documentation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token is deployed on the Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or… |
| **Governance / Economics** | 4/10 | Medium | Liquidity is healthy at $170,422 and fully protected by a 100% burn of LP tokens (7.4 Economic). The 24h volume of $1,616,143 relative to liquidity results in a ratio of 9.48, suggesting active… |
| **Upgrades** | 4/10 | Medium | The mint is fully immutable with no upgrade paths for authorities or metadata (7.7 Upgrades). Metadata is non-mutable, ensuring branding consistency (7.8 Operations). No further administrative… |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · ⚪ 4 Informational_

### `QA-IDENTITY` — Imitation of Pax Dollar (USDP)  *(Severity: Critical · Status: Acknowledged)*

Presents itself as Pax Dollar (USDP), but the listed USDP contract on solana is hvbpjaqgnpkgbaybzqbr1t7yfdvayvp2vcqqfkken4tm (CoinGecko). Holders who think they own the real asset own this contract instead; it has none of the real asset's backing, liquidity or redemption.

**Recommendation:** Do not buy, hold or accept this token as the asset it names. Verify any token address against the issuer's official site.


### `M-01` — High Holder Correlation  *(Severity: Medium · Status: Unresolved)*

Third-party risk registries have flagged the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by a small number of entities.

**Recommendation:** Monitor on-chain holder distribution and transaction patterns to assess the risk of coordinated sell-offs.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $168K (DexScreener, all pools). 24h trading volume $1.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Imitation of Pax Dollar (USDP)  *(Severity: Informational · Status: Acknowledged)*

A token presenting itself under the name or ticker of an established asset without being that asset's contract. Its only reason to borrow that identity is to be mistaken for it. Scored as an imitation (see the identity finding). Its name presents it as a stable-value coin, yet it trades at $0.004005 — it does not hold a peg. Basis: launched on pump.fun, a meme launchpad; behaves as: meme token. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $168K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Do not treat this token as the asset it names. Use only the official contract address published by that asset's issuer.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GwdwQJ...pump`](https://solscan.io/account/GwdwQJb1marsG8xq25dgtFR5CeZCBHrFYa3N5bLUpump) |
| **Network** | Solana |
| **Price** | $0.004005 |
| **24h Volume** | $1.61M |
| **Liquidity** | $167.6K |
| **Volume / Liquidity** | 9.6× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 35670 buys / 12940 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cf9tqoj2x872zwb3deosxtnbt2nppxpdfcthxohg5rjk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usdp-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
