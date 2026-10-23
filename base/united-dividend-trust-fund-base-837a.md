---
token: United Dividend Trust Fund
ticker: UDTF
network: base
risk_score: 56
status: medium
date: 2026-10-23
---

# United Dividend Trust Fund (UDTF) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-dividend-trust-fund-base-837a)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage token inflation and liquidity pool access. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** To improve security, consider transitioning ownership to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single compromised key. Additionally, implementing a time-lock mechanism for sensitive functions like updateMintRate would provide transparency and protection for token holders against sudden supply changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes robust OpenZeppelin standards (7.1 Architecture, 7.2 Code Security). The implementation of ERC-20, ERC-20Votes, and EIP-712 is standard and well-structured. However, the… |
| **Governance / Economics** | 3/10 | High | The economic model (7.4 Economic) is highly centralized, allowing the owner to mint tokens up to a 2% annual cap. Governance (7.5 Governance) is currently limited to the owner, lacking decentralized… |
| **Upgrades** | 4/10 | Medium | The contract is not a proxy (7.7 Upgrades), meaning the logic is immutable once deployed. Operations (7.8 Operations) are straightforward, though the owner's ability to change token URI and mint… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply, which dilutes the value of existing holdings.

**Recommendation:** Implement a time-lock for minting operations or transition ownership to a DAO to ensure community oversight of supply changes.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch via the lockPool and unlockPool functions. This allows the owner to unilaterally restrict or enable token transfers, potentially freezing user funds or liquidity.

**Recommendation:** Remove the ability to arbitrarily lock pools or restrict it to specific, transparent, and time-bound conditions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 3,631 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,631 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $50K (DexScreener, all pools). 24h trading volume $207K (DexScreener, all pools).

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
| **Contract** | [`0x06c9...ff40`](https://basescan.org/address/0x06c96b1f551d09357ef2dd7bc4d47c1ed1a9ff40) |
| **Network** | Base |
| **Price** | $0.005019 |
| **24h Volume** | $206.7K |
| **Liquidity** | $50.2K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 11h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1468 buys / 1380 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x2757716eae1d32fb33833dd4fae843a0b0260d52f21348ea154c0d896dcb9cf1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-dividend-trust-fund-base-837a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
