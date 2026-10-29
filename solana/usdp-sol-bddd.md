---
token: USDP🔥
ticker: USDP
network: solana
risk_score: 91
status: critical
date: 2026-10-29
---

# USDP🔥 (USDP) — Smart Contract Security Analysis | Solana

> **Risk Score: 91/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usdp-sol-bddd)

---

## Audit Summary

The USDP token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn, mitigating risks of rug pulls. Holder distribution data is unavailable, and a third-party registry flags high holder correlation, which warrants caution regarding potential market manipulation.

> **Final Recommendation:** Investors should monitor the token's price action and volume for signs of artificial manipulation due to the flagged high holder correlation. Since holder distribution data is currently unavailable, exercise caution when entering large positions.

Verify the current supply and authority status periodically using a block explorer to ensure no unexpected state changes occur. Given the high liquidity, ensure that slippage settings on decentralized exchanges are configured appropriately for your trade size.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token is implemented via the Token-2022 program (7.1 Architecture). Security is bolstered by the permanent revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks… |
| **Governance / Economics** | 4/10 | Medium | Liquidity is robust at $521,813 and is 100% burned, ensuring it cannot be withdrawn (7.4 Economic). Trading volume is healthy with a 0.78 ratio, indicating normal activity (7.6 External). However… |
| **Upgrades** | 4/10 | Medium | The mint is immutable with metadata and balance-mutating authorities disabled (7.7 Upgrades). There are no upgrade paths for transfer hooks or fees. The token configuration is finalized and cannot be… |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · ⚪ 4 Informational_

### `QA-IDENTITY` — Imitation of Pax Dollar (USDP)  *(Severity: Critical · Status: Acknowledged)*

Presents itself as Pax Dollar (USDP), but the listed USDP contract on solana is hvbpjaqgnpkgbaybzqbr1t7yfdvayvp2vcqqfkken4tm (CoinGecko). Holders who think they own the real asset own this contract instead; it has none of the real asset's backing, liquidity or redemption.

**Recommendation:** Do not buy, hold or accept this token as the asset it names. Verify any token address against the issuer's official site.


### `M-01` — High Holder Correlation  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by a small, interconnected group of wallets.

**Recommendation:** Monitor on-chain movements for coordinated sell-offs and avoid over-exposure to the asset.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $519K (DexScreener, all pools). 24h trading volume $407K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Imitation of Pax Dollar (USDP)  *(Severity: Informational · Status: Acknowledged)*

A token presenting itself under the name or ticker of an established asset without being that asset's contract. Its only reason to borrow that identity is to be mistaken for it. Scored as an imitation (see the identity finding). Its name presents it as a stable-value coin, yet it trades at $0.03771 — it does not hold a peg. Basis: launched on pump.fun, a meme launchpad; behaves as: meme token. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $519K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Do not treat this token as the asset it names. Use only the official contract address published by that asset's issuer.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7L1tZY...pump`](https://solscan.io/account/7L1tZYhM83mVaASro3rD1Up2jhschVEhj6VvpVBnpump) |
| **Network** | Solana |
| **Price** | $0.03771 |
| **24h Volume** | $406.7K |
| **Liquidity** | $519.5K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 15h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 41776 buys / 1881 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dvavznpvzl8h6y5uparv9j7uknkfsewfgdvkermsn1th)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usdp-sol-bddd)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
