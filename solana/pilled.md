---
token: pilled
ticker: PILLED
network: solana
risk_score: 21
status: low
date: 2026-10-23
---

# pilled (PILLED) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pilled-sol)

---

## Audit Summary

The pilled token is a Token-2022 asset with fully revoked mint and freeze authorities, eliminating central control risks. However, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Investors should monitor the token's trading activity, as the high volume-to-liquidity ratio may indicate artificial market manipulation. Verify the current market depth on a DEX interface before executing large trades to ensure slippage remains within acceptable bounds.

Since holder concentration data is currently unavailable, users should exercise caution regarding potential whale activity. Periodically check the mint address on a block explorer to confirm that authority statuses remain revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active extensions. 7.1 Architecture is standard, and 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.2 Code Security… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic stability is impacted by a volume/liquidity ratio of 32.83, which exceeds the 20x threshold for wash-trading signals. 7.6 External liquidity is protected by 100% burning of LP tokens… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. 7.8 Operations are secure due to the revocation of all administrative authorities. Metadata is immutable, preventing branding changes. |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 32.83, which is significantly higher than the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics; verify actual order book depth.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $43K (DexScreener, all pools). 24h trading volume $877K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $43K of DEX liquidity across 30 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AVKYgz...pump`](https://solscan.io/account/AVKYgzccwrWTNtW2ejz3VRthG3UYsVMmJ5piVEhzpump) |
| **Network** | Solana |
| **Price** | $0.0002322 |
| **24h Volume** | $819.9K |
| **Liquidity** | $43.1K |
| **Volume / Liquidity** | 19.0× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9795 buys / 7078 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/duyqeto5lfgtjgvop57xzaul3dbbpgszsnckpahcyuas)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pilled-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
