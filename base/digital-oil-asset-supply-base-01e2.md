---
token: Digital Oil Asset Supply
ticker: DOAS
network: base
risk_score: 56
status: medium
date: 2026-10-24
---

# Digital Oil Asset Supply (DOAS) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/digital-oil-asset-supply-base-01e2)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage minting rates and pool access. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over supply and transferability poses a significant trust requirement for token holders.

> **Final Recommendation:** To improve security, consider transitioning the ownership to a multi-signature wallet or a decentralized DAO structure to mitigate the risks associated with a single point of failure. Additionally, implementing a timelock on sensitive functions like updateMintRate would provide transparency and allow the community to react to significant changes in token supply.

Ensure that all administrative actions are logged via events to maintain an audit trail. For long-term sustainability, consider renouncing ownership or moving to a governance-controlled model once the initial distribution and vesting phases are complete.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, voting, and permit functionality (7.1 Architecture, 7.2 Code Security). The implementation is clean and follows standard patterns… |
| **Governance / Economics** | 3/10 | High | The economic model is heavily centralized, with the owner having the authority to mint tokens up to a 2% annual cap (7.4 Economic). Governance is currently limited to the owner, with no decentralized… |
| **Upgrades** | 4/10 | Medium | The contract is not currently using a proxy pattern, meaning the logic is immutable (7.7 Upgrades). While this prevents malicious logic updates, it also prevents the protocol from patching potential… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to trigger minting via updateMintRate and release functions, which increases the total supply and dilutes existing token holders.

**Recommendation:** Implement a timelock for minting operations or move the minting authority to a decentralized governance contract.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to toggle the transferability of tokens, effectively allowing the owner to freeze user assets or restrict market activity.

**Recommendation:** Remove the ability to arbitrarily lock transfers or restrict this functionality to specific, time-bound scenarios with clear community oversight.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,516 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,516 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $75K (DexScreener, all pools). 24h trading volume $209K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $75K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xce8a...4698`](https://basescan.org/address/0xce8a6353754b74ca2c1559bda72f5c3f78644698) |
| **Network** | Base |
| **Price** | $0.1135 |
| **24h Volume** | $209.4K |
| **Liquidity** | $74.6K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 11h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1334 buys / 1321 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x9e778441840420218f52d57b3f5806be1eb5135abdb4173479d65bb855b35ffe)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/digital-oil-asset-supply-base-01e2)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
