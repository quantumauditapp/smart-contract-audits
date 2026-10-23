---
token: stablecoin
ticker: STABLECOIN
network: solana
risk_score: 96
status: critical
date: 2026-10-23
---

# stablecoin (STABLECOIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 96/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stablecoin-sol)

---

## Audit Summary

The token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the high volume-to-liquidity ratio suggests potential wash trading. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Investors should monitor the token's trading activity, as the high volume-to-liquidity ratio is a strong indicator of artificial market activity. Verify the current market price against the low liquidity depth before executing large swaps to avoid excessive slippage.

Since holder concentration data is currently unavailable, exercise caution regarding potential whale activity. No further on-chain actions are required to secure the token itself, as the authorities are already permanently revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token utilizes the SPL Token-2022 program. 7.1 Architecture is standard, with no active transfer hooks or custom extensions. 7.2 Code Security is inherent to the audited SPL program. 7.3 Access… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic indicators show $12,429 in liquidity, which is fully burned, ensuring 7.5 Governance and liquidity safety. However, 7.6 External market data indicates a volume/liquidity ratio of 52.51… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable to this mint. Metadata is immutable, and no authority exists to modify token parameters. The token state is fixed. |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 4 Informational_

### `QA-IDENTITY` — Imitation of Stable Coin (SBC)  *(Severity: Critical · Status: Acknowledged)*

Presents itself as Stable Coin (SBC), but the listed SBC contract on solana is dbazbuxalj1qancseupzz4sp9f8d2sc78c4vkjhbtgma (CoinGecko). Holders who think they own the real asset own this contract instead; it has none of the real asset's backing, liquidity or redemption.

**Recommendation:** Do not buy, hold or accept this token as the asset it names. Verify any token address against the issuer's official site.


### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 52.51, which significantly exceeds the 20x threshold, indicating potential wash trading.

**Recommendation:** Exercise caution when interpreting volume metrics; verify trade history for repetitive patterns.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $741K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Imitation of Stable Coin (SBC)  *(Severity: Informational · Status: Acknowledged)*

A token presenting itself under the name or ticker of an established asset without being that asset's contract. Its only reason to borrow that identity is to be mistaken for it. Scored as an imitation (see the identity finding). Its name presents it as a stable-value coin, yet it trades at $2.736e-05 — it does not hold a peg. Basis: launched on pump.fun, a meme launchpad; behaves as: meme token. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $13K of DEX liquidity across 3 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Do not treat this token as the asset it names. Use only the official contract address published by that asset's issuer.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`B66MyR...pump`](https://solscan.io/account/B66MyRSvU5KaP8wfUgHCNXMNHmiw4y5tFwSWq6iQpump) |
| **Network** | Solana |
| **Price** | $0.00002736 |
| **24h Volume** | $649.0K |
| **Liquidity** | $12.8K |
| **Volume / Liquidity** | 50.6× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6172 buys / 5263 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4ucvkkd1sv7cggudbudcgxchqu61gbscr4ibxmfifibp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stablecoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
