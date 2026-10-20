---
token: Super Intelligence
ticker: SI
network: ethereum
risk_score: 27
status: low
date: 2026-10-05
---

# Super Intelligence (SI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/super-intelligence-eth)

---

## Audit Summary

The `si` token contract is an ERC-20 standard token with renounced ownership. This means the original owner can no longer call owner-restricted functions like `manualTokenSend` or `manualETHSend`, making them dormant. The contract includes configurable transfer limits (`_maxTxAmount`, `_maxWalletSize`) which can be modified by an `authorized` address. One low-severity finding was identified, related to the ability of a privileged address to remove these transfer limits.

> **Final Recommendation:** It is recommended that token holders understand the role and identity of the `authorized` address, as this entity can significantly alter the token's transfer mechanics by removing transaction and wallet size limits. While ownership is renounced, ensuring the immutability of owner-only functions, the `authorized` role remains a central point of control for key economic parameters.

Consider implementing a multi-signature wallet or a time-lock mechanism for the `authorized` role if it is intended to be a community-governed or highly sensitive function. This would add an extra layer of security and transparency to limit changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The `si` contract implements the ERC-20 standard, providing basic token functionalities such as `transfer` and `transferFrom`. The core transfer logic is handled by `_transfer`, which incorporates… |
| **Governance / Economics** | 9/10 | Low | The contract's economic parameters include `_maxTxAmount` and `_maxWalletSize`, which govern transaction and wallet holding limits. These limits are crucial for controlling token distribution and… |
| **Upgrades** | 10/10 | Low | The `si` contract is not deployed as a proxy and does not include any explicit upgrade mechanisms (7.7 Upgrades). This means the contract's logic is immutable once deployed, providing certainty… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `CP-08` — Privileged Address Can Modify Token Transfer Limits  *(Severity: Low · Status: Unresolved)*

The `removeLimit` function allows an `authorized` or `ownerorauthorized` address to change the maximum transaction amount (`_maxTxAmount`) and maximum wallet size (`_maxWalletSize`) to the total supply. This means a designated controller could disable these protective limits, potentially impacting token distribution or market dynamics.

**Recommendation:** Token holders should be aware that a designated `authorized` address can remove transaction and wallet size limits using the `removeLimit` function. It is important to understand who controls this `authorized` address and the implications of these limits being removed.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.1% of supply. Of that, 8.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.0% in wallets, 85.1% in other contracts. 270 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

270 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $57K (DexScreener, all pools). 24h trading volume $76K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $57K of DEX liquidity across 3 pools. Launch: 3 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xed56...b2b5`](https://etherscan.io/address/0xed5631ff33800bb4008c7211eaa088bdade4b2b5) |
| **Network** | Ethereum |
| **Price** | $0.000356 |
| **24h Volume** | $75.6K |
| **Liquidity** | $56.6K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 3d |
| **Top-10 Holders** | 97.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 201 buys / 129 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x304713a674dbd543faa08790204556b80fac3cde)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/super-intelligence-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-05*
