---
token: USOE
ticker: USOE
network: base
risk_score: 64
status: medium
date: 2026-10-28
---

# USOE (USOE) — Smart Contract Security Analysis | Base

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usoe-base-17e8)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance and vesting features. The protocol relies on a centralized owner to manage minting rates and pool transfer restrictions. While the code follows established OpenZeppelin standards, the high level of administrative control over token supply and transferability presents a significant centralization risk to token holders.

> **Final Recommendation:** To improve security, it is recommended to transition ownership to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single compromised key. Implementing a time-lock on sensitive functions like updateMintRate would provide transparency and allow the community to react to significant changes in token supply.

Furthermore, consider documenting the specific criteria for pool locking to ensure users understand the conditions under which their ability to transfer tokens may be restricted. Regular audits of the owner's operational procedures are advised to ensure that administrative keys are managed with industry-standard security practices.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin libraries for ERC-20, Votes, and Permitting, ensuring robust base functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the contract owner. The owner has the ability to mint tokens and toggle transferability, which directly impacts the token's… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not supported as this is a non-proxy contract. The logic is immutable, which provides security against proxy-based storage collisions. Future changes to the protocol would require a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total token supply. This allows the controller to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Implement a time-lock mechanism for minting operations or transition ownership to a DAO to ensure community oversight of supply changes.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to enable or disable token transfers. This gives the controller the power to freeze user assets or halt trading activity unilaterally.

**Recommendation:** Remove the ability to arbitrarily pause transfers or implement a decentralized consensus mechanism to trigger such restrictions in emergency scenarios only.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xd9a2…3a88 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 96.2% in other contracts. 35 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

35 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $118K (DexScreener, all pools). 24h trading volume $537K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $118K of DEX liquidity across 2 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd8d9...bf75`](https://basescan.org/address/0xd8d9f522d4b80dc93c2eed393da2d08ef177bf75) |
| **Network** | Base |
| **Price** | $0.0000073 |
| **24h Volume** | $537.4K |
| **Liquidity** | $118.4K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1098 buys / 1074 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x6c02da89ecf22d84f9c7f414b186fc9b0845bfabc40c4c1addd2d27a97cdaab6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usoe-base-17e8)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
