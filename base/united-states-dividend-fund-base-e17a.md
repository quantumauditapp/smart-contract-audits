---
token: United States Dividend Fund🔥
ticker: USDF
network: base
risk_score: 58
status: medium
date: 2026-10-23
---

# United States Dividend Fund🔥 (USDF) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-base-e17a)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation, token vesting, and transfer restrictions. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over token supply and transferability presents a significant centralization risk.

> **Final Recommendation:** To improve security, the project should transition administrative control from a single EOA to a multi-signature wallet or a decentralized governance contract. Implementing a timelock on sensitive functions like updateMintRate and lockPool would provide transparency and allow the community to react to administrative changes.

Additionally, consider renouncing ownership if the protocol reaches a state of maturity where active management is no longer required. Ensure that all administrative keys are stored in hardware security modules to prevent unauthorized access.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes robust OpenZeppelin libraries for ERC-20 and voting functionality, ensuring 7.1 Architecture and 7.2 Code Security standards are met. 7.3 Access Control is implemented via… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance risks are elevated due to the owner's ability to arbitrarily mint tokens and halt transfers. While 7.8 Operations are supported by clear administrative functions, the… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, eliminating 7.7 Upgrades risk. The logic is immutable, which provides certainty to token holders regarding the contract's behavior. No proxy patterns are utilized in… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to call updateMintRate and release, which can increase the total supply of tokens. This allows the owner to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Implement a timelock for all supply-altering functions to ensure transparency and provide users with a window to exit if they disagree with the proposed inflation changes.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable token transfers. This gives the owner the power to effectively freeze user funds or prevent trading on decentralized exchanges.

**Recommendation:** Remove the ability to arbitrarily lock transfers, or restrict this functionality to a decentralized governance vote rather than a single owner address.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x6642…3673 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 3,090 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,090 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $90K (DexScreener, all pools). 24h trading volume $176K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.05325 — it does not hold a peg. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $90K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x54c5...c615`](https://basescan.org/address/0x54c5c606ea5e4d8504ec4399a06b3cfb8ec9c615) |
| **Network** | Base |
| **Price** | $0.05325 |
| **24h Volume** | $176.3K |
| **Liquidity** | $90.2K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 14h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1718 buys / 1612 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x197a77b1b560a769675c98e9a79b85d9d934e7b3d1a2a64022588eb76343c7fe)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-base-e17a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
