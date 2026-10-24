---
token: US Oil Exchange (USOE)
ticker: USOE
network: base
risk_score: 56
status: medium
date: 2026-10-24
---

# US Oil Exchange (USOE) (USOE) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/us-oil-exchange-usoe-base-b796)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage minting rates and pool access, which introduces significant trust requirements. While the code follows standard OpenZeppelin patterns, the ability for the owner to unilaterally restrict transfers and inflate supply warrants caution for potential holders.

> **Final Recommendation:** To improve security, consider transitioning the ownership to a multi-signature wallet or a decentralized governance contract to mitigate the risks associated with a single point of failure. Additionally, implementing a timelock on sensitive functions like updateMintRate and lockPool would provide transparency and protection for token holders against sudden administrative actions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-tested OpenZeppelin libraries for ERC-20 and governance features (7.1 Architecture, 7.2 Code Security). The implementation of standard interfaces ensures compatibility with… |
| **Governance / Economics** | 3/10 | High | The economic model is heavily centralized under the owner's control (7.4 Economic, 7.5 Governance). The owner can adjust minting rates, which directly impacts token dilution (7.4 Economic).… |
| **Upgrades** | 4/10 | Medium | The contract is not currently using a proxy pattern (7.7 Upgrades). Logic is immutable once deployed, which provides security against unauthorized logic changes. Future upgrades would require a… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Control  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to call updateMintRate and release, which can increase the total supply of the token. This allows the owner to dilute the value of existing holdings at their discretion.

**Recommendation:** Implement a timelock for minting operations or move the minting authority to a decentralized governance mechanism to ensure community oversight.


### `CP-05` — Centralized Transfer Restriction  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to toggle the ability for users to transfer tokens or interact with specific pools. This gives the owner the power to freeze user assets or halt trading activity.

**Recommendation:** Remove the ability to arbitrarily lock pools or restrict it to specific, transparent emergency scenarios governed by a multi-sig or DAO.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 5,242 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,242 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $88K (DexScreener, all pools). 24h trading volume $291K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $88K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2e8c...de41`](https://basescan.org/address/0x2e8c8554fce95bed9e58836353673f8b7619de41) |
| **Network** | Base |
| **Price** | $0.158 |
| **24h Volume** | $291.0K |
| **Liquidity** | $87.5K |
| **Volume / Liquidity** | 3.3× |
| **Token Age** | 11h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1397 buys / 1351 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xde73c63076fe77109f7e2eabb6dabdcd612fe24034c3dff07c7bfe224c11dfc2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/us-oil-exchange-usoe-base-b796)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
