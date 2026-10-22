---
token: US Oil Exchange (USOE)
ticker: USOE
network: base
risk_score: 56
status: medium
date: 2026-10-22
---

# US Oil Exchange (USOE) (USOE) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/us-oil-exchange-usoe-base-b2a5)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance-controlled minting and transfer-restriction capabilities. While the code follows standard OpenZeppelin patterns, the centralization of power in the owner address poses a significant risk to token holders. The protocol demonstrates 7.1 Architecture (standard), 7.2 Code Security (high), 7.3 Access Control (centralized), 7.4 Economic (inflationary), 7.5 Governance (owner-centric), 7.6 External (standard), 7.7 Upgrades (N/A), and 7.8 Operations (standard).

> **Final Recommendation:** It is recommended to transition the owner role to a decentralized multi-signature wallet or a DAO governance contract to mitigate the risks of single-point-of-failure. Additionally, implementing a timelock on sensitive functions like updateMintRate and lockPool would provide transparency and allow the community to react to administrative changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for core ERC-20 functionality. Code quality is high, with clear separation of concerns and standard implementation of EIP-712 and… |
| **Governance / Economics** | 3/10 | High | The economic model is inflationary, allowing the owner to mint tokens up to a 2% annual cap. This provides the owner with significant control over token supply and holder dilution. The governance… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, which provides immutability for the core logic. This eliminates risks associated with proxy storage collisions or malicious implementation swaps. Users can rely on… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply, which directly dilutes the value of existing tokens held by users.

**Recommendation:** Implement a decentralized governance mechanism or a hard-coded minting schedule that limits the owner's ability to arbitrarily increase supply.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch via the lockPool and unlockPool functions. This allows the owner to unilaterally halt or resume token transfers, effectively freezing user assets at will.

**Recommendation:** Remove the ability for the owner to pause transfers, or implement a multi-signature requirement and a public notice period before any transfer restrictions are applied.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 3,034 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,034 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $440K (DexScreener, all pools). 24h trading volume $552K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $440K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd037...83e3`](https://basescan.org/address/0xd03768a917d2e030d6366d951b7d70b69b0583e3) |
| **Network** | Base |
| **Price** | $0.7837 |
| **24h Volume** | $551.6K |
| **Liquidity** | $440.4K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 14h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1793 buys / 1758 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xe31e86c52106738b7b78101ea12ff72041276cacf81d413a6c9c6606219661ca)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/us-oil-exchange-usoe-base-b2a5)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
