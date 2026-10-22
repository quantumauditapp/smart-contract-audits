---
token: Federal Oil Trust Fund
ticker: FOTF
network: base
risk_score: 59
status: medium
date: 2026-10-22
---

# Federal Oil Trust Fund (FOTF) — Smart Contract Security Analysis | Base

> **Risk Score: 59/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/federal-oil-trust-fund-base-75bb)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with added governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates and pool access. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over token supply and transferability presents a significant centralization risk.

> **Final Recommendation:** It is recommended to transition the ownership of the contract to a decentralized governance model, such as a DAO or a multi-signature wallet, to mitigate the risks associated with a single point of failure. Implementing a timelock for sensitive administrative functions like updateMintRate would provide transparency and allow the community to react to significant changes in tokenomics.

Additionally, ensure that the owner's private keys are managed with high-security standards, such as hardware security modules or institutional-grade custody solutions, given the level of control granted over the token's supply and transferability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, voting, and permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has the ability to mint tokens up to a 2% annual cap and toggle transferability, which directly impacts token value and… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward, relying on the owner to trigger vesting releases and inflation adjustments. No complex upgrade paths… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Token Minting Control  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply, which dilutes the value of existing holdings for all token holders.

**Recommendation:** Consider implementing a timelock on minting functions or moving the minting authority to a decentralized governance contract to prevent unilateral supply increases.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable token transfers. This gives the owner the power to freeze user funds or restrict liquidity at their discretion.

**Recommendation:** Remove the ability to pause transfers or restrict this functionality to a decentralized emergency pause mechanism that requires community consensus.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,531 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,531 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $97K (DexScreener, all pools). 24h trading volume $292K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $97K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xec26...6e26`](https://basescan.org/address/0xec26f3995e6b51d0dfcb704e9b16d8972f5e6e26) |
| **Network** | Base |
| **Price** | $0.19 |
| **24h Volume** | $291.6K |
| **Liquidity** | $97.0K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 14h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1458 buys / 1434 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xdf573dc23d1f3a40f9bce41ece87bb6fb3a02cd73f488ade64533675c677971d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/federal-oil-trust-fund-base-75bb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
