---
token: United States Dividend Program
ticker: USDP
network: solana
risk_score: 93
status: critical
date: 2026-11-03
---

# United States Dividend Program (USDP) — Smart Contract Security Analysis | Solana

> **Risk Score: 93/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-dividend-program-sol-e8fb)

---

## Audit Summary

The USDP token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully locked, and the token exhibits no aggressive transfer hooks or mutable metadata. Third-party registry data indicates high holder correlation, which is the primary observed risk factor.

> **Final Recommendation:** The token demonstrates strong security posture regarding authority management and liquidity. Holders should monitor the high holder correlation signal via block explorers to ensure that the distribution remains decentralized over time.

Verify the current mint and freeze authority status using a block explorer to confirm they remain set to 'None'. No further action is required for the current configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token is implemented via the SPL Token-2022 program. 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is robust as both mint and freeze authorities are… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic and 7.5 Governance metrics show healthy liquidity of $258,279 with 100% of LP tokens burned. 7.6 External signals indicate high holder correlation, though concentration among the top 10… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is fixed and cannot be modified. There are no upgradeable transfer hooks or fees configured for this mint. |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · ⚪ 5 Informational_

### `QA-IDENTITY` — Imitation of Pax Dollar (USDP)  *(Severity: Critical · Status: Acknowledged)*

Presents itself as Pax Dollar (USDP), but the listed USDP contract on solana is hvbpjaqgnpkgbaybzqbr1t7yfdvayvp2vcqqfkken4tm (CoinGecko). Holders who think they own the real asset own this contract instead; it has none of the real asset's backing, liquidity or redemption.

**Recommendation:** Do not buy, hold or accept this token as the asset it names. Verify any token address against the issuer's official site.


### `M-01` — High Holder Correlation  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry signals indicate high holder correlation, suggesting that a significant portion of the supply may be controlled by a single entity or coordinated group.

**Recommendation:** Monitor on-chain wallet movements to identify potential coordinated sell-offs.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 1.6% of supply. Of that, 1.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.5% in wallets, 0.0% in other contracts. 3,003 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $259K (DexScreener, all pools). 24h trading volume $203K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Imitation of Pax Dollar (USDP)  *(Severity: Informational · Status: Acknowledged)*

A token presenting itself under the name or ticker of an established asset without being that asset's contract. Its only reason to borrow that identity is to be mistaken for it. Scored as an imitation (see the identity finding). Its name presents it as a stable-value coin, yet it trades at $0.01024 — it does not hold a peg. Basis: launched on pump.fun, a meme launchpad; behaves as: meme token. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $259K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Do not treat this token as the asset it names. Use only the official contract address published by that asset's issuer.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`kgBpvF...pump`](https://solscan.io/account/kgBpvFt4q4FhCgaL7aAQ4pxVrfvVzQjkLjxnJQ7pump) |
| **Network** | Solana |
| **Price** | $0.01024 |
| **24h Volume** | $202.6K |
| **Liquidity** | $259.3K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 2d |
| **Top-10 Holders** | 1.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 20108 buys / 2606 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2gjqvlqfx7yvhlo6hyxukhxwymp8cygbvsij58ljf6tt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-dividend-program-sol-e8fb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
