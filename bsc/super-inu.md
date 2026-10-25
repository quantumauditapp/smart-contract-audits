---
token: Super Inu
ticker: 四
network: bsc
risk_score: 52
status: medium
date: 2026-10-25
---

# Super Inu (四) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 52/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/super-inu-bsc)

---

## Audit Summary

The BinanceAgentTaxToken is a complex, modular token implementation deployed as an EIP-1167 minimal clone. It features extensive administrative control over transfer logic, fee structures, and external dependency routing. While the architecture is modular, the high degree of centralization in privileged roles poses significant risks to token holders.

> **Final Recommendation:** The protocol should transition administrative functions to a multi-signature wallet or a decentralized governance contract to mitigate the risk of single-point-of-failure. Additionally, implementing timelocks on sensitive functions like fee adjustments would provide transparency and protection for token holders.

Users should be aware that the token's transferability and economic value are subject to change by the protocol's controllers. Regular monitoring of the privileged module addresses is recommended to ensure they remain secure and trustworthy.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes a robust EIP-1167 clone pattern to ensure consistent logic across deployments. It implements a sophisticated internal accounting system for taxes and liquidity management.… |
| **Governance / Economics** | 7/10 | Low | Economic parameters are entirely controlled by privileged roles, allowing for dynamic fee adjustments and fund movement. 7.4 Economic: Fees are mutable. 7.5 Governance: Centralized control via… |
| **Upgrades** | 8/10 | Low | The contract is deployed as a minimal clone, meaning the implementation logic is immutable once deployed. 7.7 Upgrades: Not upgradeable. This prevents malicious logic updates but limits the ability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `CP-03` — Centralized Control Over Core Logic Dependencies  *(Severity: High · Status: Unresolved)*

The postInitialize function allows a privileged module to change the addresses of external contracts that the token relies on for core operations. This means the controller can redirect token logic to arbitrary contracts at any time.

**Recommendation:** Restrict the ability to change core dependencies to a multi-signature wallet or a governance process with a mandatory timelock.


### `CP-07` — Mutable Transfer Fees  *(Severity: Medium · Status: Unresolved)*

Multiple privileged functions allow for the modification of transfer fees and tax collection rates. This allows the controller to unilaterally change the economic cost of transacting with the token.

**Recommendation:** Implement a cap on the maximum fee that can be set to protect users from sudden, excessive tax increases.


### `CD-01` — Rounding Loss Due to Division Before Multiplication  *(Severity: Low · Status: Unresolved)*

The _doDispatchFee function performs division before multiplication, which can lead to precision loss and minor inaccuracies in fee calculations.

**Recommendation:** Reorder arithmetic operations to perform multiplication before division to maintain higher precision.


### `CP-05` — Administrative Switch for Transfer Functionality  *(Severity: Informational · Status: Unresolved)*

Privileged functions can toggle internal switches that determine whether transfers, swaps, or liquidity additions are permitted. This grants the controller the power to effectively pause or censor token activity. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Document the intended use of these switches and implement a public event log to notify users when these states are changed.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 46.3% of supply. Of that, 30.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.5% in wallets, 7.4% in other contracts. The deployer/owner wallet itself holds 1.0%. 359 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

359 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $16K (DexScreener, all pools). 24h trading volume $466K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 1% on sell. Market: $16K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa229...ffff`](https://bscscan.com/address/0xa2299d7179afebf5667afbf1e4e45fa051a2ffff) |
| **Network** | BNB Chain |
| **Price** | $0.0000272 |
| **24h Volume** | $466.2K |
| **Liquidity** | $15.5K |
| **Volume / Liquidity** | 30.1× |
| **Token Age** | 9h |
| **Top-10 Holders** | 46.3% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 3568 buys / 3909 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xecbf550aed7d1bdfbd5d876a88472c1fb0801372)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/super-inu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
