---
token: XTO
ticker: XTO
network: base
risk_score: 58
status: medium
date: 2026-10-25
---

# XTO (XTO) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-base-db59)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance, voting, and vesting capabilities. The architecture relies on a centralized owner account that holds significant power over token supply and transferability. While the code follows standard OpenZeppelin patterns, the centralization of administrative functions creates a trust-based model for token holders.

> **Final Recommendation:** To improve security, consider transitioning the ownership to a multi-signature wallet or a decentralized governance contract to remove single points of failure. Implementing a timelock on sensitive functions like updateMintRate would provide the community with visibility and time to react to significant economic changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, voting, and permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of established… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the contract owner. The owner has the authority to mint tokens and halt transfers, which directly impacts token value and… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, providing certainty to users regarding the contract's behavior. No upgrade path exists, which eliminates risks… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to mint new tokens via updateMintRate and release functions, which can lead to the dilution of existing token holders' value.

**Recommendation:** Implement a timelock for minting operations or transition ownership to a DAO to ensure community oversight.


### `CP-05` — Transfer Control Switch  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch via lockPool and unlockPool, effectively freezing or enabling token transfers at will.

**Recommendation:** Restrict the ability to pause transfers to emergency scenarios only and document the specific conditions under which this power will be exercised.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 6,971 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

6,971 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $238K (DexScreener, all pools). 24h trading volume $1.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $238K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x941c...a759`](https://basescan.org/address/0x941c2c92f0d71d0be34c8278d4fab5476bd2a759) |
| **Network** | Base |
| **Price** | $0.4728 |
| **24h Volume** | $1.42M |
| **Liquidity** | $237.5K |
| **Volume / Liquidity** | 6.0× |
| **Token Age** | 11h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1245 buys / 1131 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x796221ce282023cd48e8097c0989ddf63981c8dc0ff59e8fb3e7ca56bdfcca77)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-base-db59)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
