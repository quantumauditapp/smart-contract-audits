---
token: Project Lazarus
ticker: LAZARUS
network: solana
risk_score: 23
status: low
date: 2026-10-31
---

# Project Lazarus (LAZARUS) — Smart Contract Security Analysis | Solana

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/project-lazarus-sol)

---

## Audit Summary

Project Lazarus (LAZARUS) utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. While the token architecture is secure, the high volume-to-liquidity ratio suggests potential wash trading activity. All third-party risk registry data was successfully retrieved and indicates no adverse flags.

> **Final Recommendation:** Investors should monitor the high volume-to-liquidity ratio, as it may indicate artificial trading activity that does not reflect genuine market demand. Ensure that any future interactions are based on verified on-chain data rather than external volume metrics.

Verify the current supply and holder distribution via a block explorer to ensure no significant changes have occurred since this audit. No further action is required regarding authority management as the mint is fully renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the SPL Token-2022 program. 7.1 Architecture is standard for non-custodial assets. 7.2 Code Security is inherent to the audited program version. 7.3 Access Control is robust… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic factors show a 19.99% concentration among the top 10 holders. 7.5 Governance is decentralized due to authority revocation. 7.6 External market data reveals a volume/liquidity ratio of… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints are immutable. Metadata is immutable, and there are no upgradable extensions or balance-mutating authorities present. The token configuration is finalized. |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 60.98, which significantly exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution when evaluating market demand; prioritize liquidity depth over reported volume.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 52.5% of supply. Of that, 32.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 18.0% in wallets, 2.0% in other contracts. 529 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

529 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $752K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 5 pools. Launch: launched on pump.fun (PumpSwap), 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2GvnZ8...vh3x`](https://solscan.io/account/2GvnZ864v6Nx99KbZnQrADK1z88ykbz5A9rBtB5Bvh3x) |
| **Network** | Solana |
| **Price** | $0.00002267 |
| **24h Volume** | $715.5K |
| **Liquidity** | $11.3K |
| **Volume / Liquidity** | 63.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | 52.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8534 buys / 6149 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fvsst7y4vit8kuz5vsn3bsfg16ozgi1ehcurm873xpyf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/project-lazarus-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
