---
token: World Strategic Oil Supply
ticker: WSOS
network: base
risk_score: 63
status: medium
date: 2026-10-25
---

# World Strategic Oil Supply (WSOS) — Smart Contract Security Analysis | Base

> **Risk Score: 63/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/world-strategic-oil-supply-base-987d)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation and transfer restrictions. While the code follows standard OpenZeppelin patterns, the high level of administrative control over supply and transferability presents a significant trust requirement for token holders.

> **Final Recommendation:** To improve security, it is recommended to transition ownership to a multi-signature wallet or a decentralized governance contract. Implementing a timelock on sensitive functions like updateMintRate and lockPool would provide transparency and allow the community to react to administrative changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-tested OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard, audited… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the contract owner. The owner has the ability to mint tokens and halt transfers, which directly impacts 7.8 Operations. While… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. This ensures immutability of the logic, which is a strength for security. There is no risk of malicious logic injection via proxy… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total token supply. This allows the owner to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Restrict minting capabilities to a decentralized governance process or implement a strict, transparent emission schedule that cannot be altered by a single address.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable token transfers. This gives the owner the power to freeze user assets or prevent trading activity entirely.

**Recommendation:** Remove the ability for the owner to pause transfers, or implement a multi-sig requirement and a public notification period before any such action is taken.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.1% in other contracts. The deployer/owner wallet itself holds 16.2%. 4,015 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,015 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $49K (DexScreener, all pools). 24h trading volume $50K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $49K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x92c3...7947`](https://basescan.org/address/0x92c34b89d01d15298a89270a045fea19f2277947) |
| **Network** | Base |
| **Price** | $0.004799 |
| **24h Volume** | $50.0K |
| **Liquidity** | $48.7K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 11h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2009 buys / 1336 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x9839336d4d7f811e0740ec6bd932315e35de45c737024460c281bca3cb0ee525)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/world-strategic-oil-supply-base-987d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
