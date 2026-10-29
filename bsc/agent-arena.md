---
token: Agent Arena
ticker: ARENA
network: bsc
risk_score: 63
status: medium
date: 2026-10-29
---

# Agent Arena (ARENA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/agent-arena-bsc)

---

## Audit Summary

GangToken is an ERC-20 implementation featuring centralized control mechanisms via a 'launchpad' role. The contract includes administrative functions that allow for token transfers and pair configuration. While the core ERC-20 logic is standard, the centralized control over supply and transfer rules introduces significant trust requirements for token holders.

> **Final Recommendation:** Token holders should be aware that the 'launchpad' address possesses significant control over the token's economic parameters and transfer capabilities. We recommend that the project team considers transitioning the 'launchpad' role to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with centralized control.

Ensure that the private keys associated with the 'launchpad' role are stored in a highly secure environment, such as a hardware security module or a multi-party computation (MPC) wallet, to prevent unauthorized access and potential abuse of the privileged functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-style ERC-20 logic, ensuring 7.1 Architecture and 7.2 Code Security compliance. 7.3 Access Control is implemented via a custom 'onlyLaunchpad' modifier… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the 'launchpad' address. This entity holds the power to manipulate token flows and pair settings, which directly impacts 7.8… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable (7.7 Upgrades), meaning the logic is immutable once deployed. This provides certainty to users regarding the contract's behavior, as the code cannot be altered… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The 'launchpad' address has the authority to execute 'reclaim' and 'pullFor' functions, which allow it to move tokens from user wallets to the launchpad address. This centralized control effectively grants the controller the ability to seize tokens or manipulate liquidity.

**Recommendation:** Implement a time-lock mechanism for these privileged functions or transition the 'launchpad' role to a decentralized governance structure to prevent unilateral actions by a single entity.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $291K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 3% on buy, 3.03% on sell. Market: $10K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7da1...b72d`](https://bscscan.com/address/0x7da17617b7e810a8f1f5188f7601e4536b52b72d) |
| **Network** | BNB Chain |
| **Price** | $0.00000953 |
| **24h Volume** | $290.7K |
| **Liquidity** | $9.6K |
| **Volume / Liquidity** | 30.4× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 2235 buys / 3629 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xa568b43aad62e167412b1c1d8fc36d621ba67d14)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/agent-arena-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
