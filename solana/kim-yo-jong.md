---
token: Kim Yo Jong
ticker: 김여정
network: solana
risk_score: 36
status: medium
date: 2026-10-20
---

# Kim Yo Jong (김여정) — Smart Contract Security Analysis | Solana

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kim-yo-jong-sol)

---

## Audit Summary

The Kim Yo Jong token mint exhibits elevated market risk driven by very thin DEX liquidity of $8,803 alongside a volume-to-liquidity ratio of 109.61 indicating wash trading. Technical permissions are secure with both mint and freeze authorities revoked and liquidity 100% burned, though chain-native RPC holder distribution data was unavailable.

> **Final Recommendation:** Simulate slippage and verify route depth on Solana decentralized aggregators prior to executing transactions, as low liquidity risks sharp capital depletion. Monitor real-time transaction activity to identify circular wallet routines, and periodically inspect top token accounts via an explorer once RPC indexing restores visibility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The mint operates under the spl-token-2022 program with an initialized supply of 951,617,328,574,073 raw units at 6 decimals. Both mint authority and freeze authority are revoked (None), ensuring… |
| **Governance / Economics** | 5/10 | Medium | On-chain pool safety is bolstered by 100.0% of LP tokens being burned, eliminating creator pool withdrawal vectors. However, available liquidity is severely restricted at $8,803 while 24-hour volume… |
| **Upgrades** | 8/10 | Low | The mint configuration is structurally immutable on-chain. Metadata mutability is set to False, preventing retroactive adjustments to branding or off-chain URI references. Extension upgrade… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $8,803. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Avoid executing standard market swaps until liquidity depth increases substantially.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 109.61x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Analyze pool transaction logs for automated self-dealing before relying on reported trading turnover.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 5 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3Ckrmz...Jcbf`](https://solscan.io/account/3Ckrmzsp6NbnW6zLcrj3z8BSn1H1gRN3fh6Un15DJcbf) |
| **Network** | Solana |
| **Price** | $0.00001502 |
| **24h Volume** | $964.4K |
| **Liquidity** | $9.3K |
| **Volume / Liquidity** | 103.8× |
| **Token Age** | 21h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8334 buys / 6832 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9h51k8vijv2ydnqugvpzktkpzwlfd9gqpgrvfwy3ck6h)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kim-yo-jong-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
