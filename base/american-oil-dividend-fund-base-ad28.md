---
token: American Oil Dividend Fund
ticker: AODF
network: base
risk_score: 58
status: medium
date: 2026-10-24
---

# American Oil Dividend Fund (AODF) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-base-ad28)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage minting rates and pool transfer restrictions. While the code follows OpenZeppelin standards, the high level of administrative control over token supply and transferability presents a significant centralization risk.

> **Final Recommendation:** To improve security, consider implementing a Timelock controller for all privileged functions, specifically updateMintRate and lockPool. This would provide transparency and a delay period for token holders to react to significant changes in supply or transfer rules.

Additionally, transitioning ownership to a multi-signature wallet or a decentralized DAO structure would mitigate the single point of failure inherent in the current 'Ownable' implementation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, EIP-712, and governance features. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has the ability to mint tokens and halt transfers, which directly impacts the token's economic stability. While 7.8… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. This ensures immutability of the logic, which is a positive security trait. No upgrade-related risks are present. |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total supply of the token. This allows the owner to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Implement a timelock for minting operations or move the minting authority to a decentralized governance contract.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to toggle a switch that determines if transfers are allowed. This gives the owner the power to freeze user funds or restrict trading activity.

**Recommendation:** Remove the ability to arbitrarily pause transfers or implement a community-voted pause mechanism.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,128 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,128 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $98K (DexScreener, all pools). 24h trading volume $171K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $98K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfed3...d8c2`](https://basescan.org/address/0xfed3ff62cb220e7361056f177c35e6480e62d8c2) |
| **Network** | Base |
| **Price** | $0.209 |
| **24h Volume** | $171.1K |
| **Liquidity** | $97.8K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 18h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1192 buys / 1114 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xf52cb1dec0794fa9ebe5d750516ce5986b3eb37a88a25f7dc19af7c33684ad71)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-base-ad28)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
