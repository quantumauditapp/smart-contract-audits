---
token: Moonoween
ticker: MOONOWEEN
network: solana
risk_score: 0
status: low
date: 2026-10-22
---

# Moonoween (MOONOWEEN) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/moonoween-sol)

---

## Audit Summary

Moonoween is a Token-2022 asset with both mint and freeze authorities successfully revoked, ensuring supply immutability and preventing account freezing. Liquidity is fully burned, eliminating the risk of rug pulls via liquidity withdrawal. Holder distribution data was unavailable, and third-party registries noted high holder correlation, which should be monitored.

> **Final Recommendation:** Investors should monitor the token's holder distribution using block explorers, as concentration data was unavailable during this audit. Given the high holder correlation noted by third-party registries, users should exercise caution regarding potential coordinated market movements.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or frozen account states. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control is robust, as… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $683,642 in liquidity, which is 100% burned. 7.5 Governance is decentralized by the lack of administrative authorities. 7.6 External signals indicate high… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints are immutable once authorities are revoked. Metadata is immutable (metadata_mutable: False), preventing branding changes. No further administrative… |

## Security Findings

_🟢 1 Low · ⚪ 5 Informational_

### `L-01` — High Holder Correlation  *(Severity: Low · Status: Unresolved)*

Third-party risk registries indicate high holder correlation, suggesting that a significant portion of the supply may be controlled by a small group of related entities.

**Recommendation:** Monitor large wallet movements and cross-reference holder addresses to assess potential market manipulation risks.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $682K (DexScreener, all pools). 24h trading volume $441K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (moon); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $682K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`eEomAE...pump`](https://solscan.io/account/eEomAEbGqwfzckzYjN6x1rc7tmqbdKJoHZdR25Upump) |
| **Network** | Solana |
| **Price** | $0.06301 |
| **24h Volume** | $441.4K |
| **Liquidity** | $681.8K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 27643 buys / 1138 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/j7qrnwxoxh1xagbgkhz4lded837njy6z55ktgywpwnwp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/moonoween-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
