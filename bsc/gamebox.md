---
token: Gamebox
ticker: GXB
network: bsc
risk_score: 47
status: medium
date: 2026-10-22
---

# Gamebox (GXB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 47/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gamebox-bsc)

---

## Audit Summary

The Gamebox contract is a standard ERC-20 token implementation. Ownership has been renounced, meaning no administrative functions can be executed, and the contract logic is immutable. The code follows OpenZeppelin standards, ensuring robust and predictable behavior for token transfers and allowances.

> **Final Recommendation:** The contract is secure and follows best practices for a standard ERC-20 token. No further action is required as the contract is immutable and ownership is renounced.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows the standard OpenZeppelin ERC-20 implementation, ensuring 7.1 Architecture and 7.2 Code Security compliance. The transfer path is standard, relying on internal _transfer and… |
| **Governance / Economics** | 6/10 | Medium | The token has no 7.4 Economic or 7.5 Governance mechanisms implemented. 7.8 Operations are limited to standard token transfers. The renounced ownership ensures no central party can influence the… |
| **Upgrades** | 8/10 | Low | The contract is not a proxy, meaning 7.7 Upgrades are not possible. The code is immutable, providing high security against upgrade-related vulnerabilities. No risk of logic changes exists. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — Null Address, PinkLock02 |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 94.3% of supply. Of that, 4.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 90.3% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 100.0%. A holder that also controls the contract can sell into its own liquidity. 313 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

313 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is locked in PinkLock02 until 22 Oct 2027 (364 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $390K (DexScreener, all pools). 24h trading volume $600K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $390K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0af9...277b`](https://bscscan.com/address/0x0af9a0016769951e7a6b9a88358748b1f34f277b) |
| **Network** | BNB Chain |
| **Price** | $0.1932 |
| **24h Volume** | $600.2K |
| **Liquidity** | $389.9K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 5h |
| **Top-10 Holders** | 94.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1099 buys / 550 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xb821547180aa62b7340f7d47f4c6c0519b3e02b5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gamebox-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
