---
token: United States Dividend Fund🔥
ticker: USDF
network: base
risk_score: 67
status: high
date: 2026-10-21
---

# United States Dividend Fund🔥 (USDF) — Smart Contract Security Analysis | Base

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates and pool access. While the code follows standard OpenZeppelin patterns, the high level of administrative control over supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** To improve security, it is recommended to transition ownership to a multi-signature wallet or a decentralized governance contract. Implementing a timelock on sensitive functions like updateMintRate and lockPool would provide users with sufficient notice before significant economic or operational changes occur.

Additionally, consider documenting the specific conditions under which the pool is locked or unlocked to provide transparency to the community. Ensure that the owner's private keys are managed with institutional-grade security practices to mitigate the risk of unauthorized administrative actions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes well-audited OpenZeppelin libraries for core ERC-20 and governance functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has the ability to mint tokens and halt transfers, which directly impacts the token's economic value and liquidity. While… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. This ensures immutability of the current logic, preventing unauthorized code changes. The owner cannot modify the contract logic, only… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to mint new tokens, which increases the total supply and dilutes the value of existing holdings. This power is unrestricted by any community vote or automated mechanism.

**Recommendation:** Implement a timelock for minting operations or transition control to a decentralized governance DAO to ensure community oversight of supply changes.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to toggle a switch that determines whether transfers are allowed. This effectively allows the owner to freeze user funds or halt trading at will.

**Recommendation:** Remove the ability to arbitrarily halt transfers or restrict this functionality to emergency scenarios governed by a multi-sig or timelock to prevent potential abuse.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 96.3% in other contracts. 2,549 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,549 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $60K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $1.224e-09 — it does not hold a peg. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb276...d4f5`](https://basescan.org/address/0xb2763b2947f2734a083517522ff44a7ab5b6d4f5) |
| **Network** | Base |
| **Price** | $0. |
| **24h Volume** | $59.8K |
| **Liquidity** | $17.8K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 1d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2743 buys / 2738 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x0a9ab7916f7e37fecdbfb9e30410c6db799ae8c24e2b44d4fa10b9e41a6691aa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
