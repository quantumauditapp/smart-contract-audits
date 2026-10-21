---
token: American Dividend Protocol
ticker: ADP
network: base
risk_score: 58
status: medium
date: 2026-10-21
---

# American Dividend Protocol (ADP) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-dividend-protocol-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with added governance, voting, and vesting capabilities. The architecture is robust, leveraging OpenZeppelin standards for core functionality. However, the contract grants significant centralized control to the owner, including the ability to mint tokens and halt transfers, which introduces notable trust requirements for token holders.

> **Final Recommendation:** To improve trust, consider transitioning ownership to a multi-signature wallet or a decentralized governance contract (DAO). This would mitigate the risk of a single compromised key performing unauthorized minting or halting transfers.

Additionally, implement a timelock mechanism for all privileged functions. This would provide transparency and a delay period for the community to react to significant changes in token supply or transfer rules.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract follows 7.1 Architecture standards by utilizing well-audited OpenZeppelin libraries for ERC-20 and governance. 7.2 Code Security is high, with clear logic and standard implementation… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the owner. The owner has the power to mint tokens via updateMintRate, which directly impacts 7.4 Economic stability by diluting… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as this is a standard non-proxy contract. 7.8 Operations are straightforward, with the owner managing the lifecycle of the token. The lack of upgradeability ensures… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Control  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to increase the total supply of the token through the updateMintRate and release functions. This allows the owner to dilute the value of existing holdings at their discretion.

**Recommendation:** Restrict minting capabilities to a decentralized governance process or implement a hard-coded, immutable inflation schedule that cannot be altered by a single address.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable token transfers. This gives the owner the power to freeze user assets or prevent trading activity entirely.

**Recommendation:** Remove the ability to pause transfers or move this functionality to a community-voted emergency pause mechanism with a clear, transparent trigger condition.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 96.2% in other contracts. 1,938 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,938 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $50K (DexScreener, all pools). 24h trading volume $242K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $50K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2c12...94cb`](https://basescan.org/address/0x2c12f26c07d0ac9eb30fd4937b9c9fad59be94cb) |
| **Network** | Base |
| **Price** | $0.00000784 |
| **24h Volume** | $242.4K |
| **Liquidity** | $50.1K |
| **Volume / Liquidity** | 4.8× |
| **Token Age** | 17h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1452 buys / 1437 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x37936b0ce04258ff606d07be16593f75e16abc11c68300e881b489faa15ccab1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-dividend-protocol-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
