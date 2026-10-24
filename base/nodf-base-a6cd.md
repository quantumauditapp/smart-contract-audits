---
token: NODF 🔥
ticker: NODF
network: base
risk_score: 56
status: medium
date: 2026-10-24
---

# NODF 🔥 (NODF) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nodf-base-a6cd)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage token inflation and pool access. While the code follows standard OpenZeppelin patterns, the high level of administrative control over supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** To improve security, consider transitioning the ownership to a multi-signature wallet or a decentralized DAO structure to mitigate the risks associated with a single privileged account. Additionally, implement a timelock on all sensitive administrative functions to provide transparency and a window for users to react to significant changes in tokenomics or transfer rules.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20 and governance features. 7.1 Architecture is modular, and 7.2 Code Security is robust with no obvious reentrancy or overflow… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the owner. The owner can unilaterally mint tokens and toggle transfer restrictions, which directly impacts 7.8 Operations. While… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable (7.7 Upgrades), which provides immutability for the logic layer. This eliminates risks associated with proxy storage collisions or malicious implementation swaps.… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Control  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to increase the total supply of tokens via the updateMintRate and release functions. This allows the owner to dilute the holdings of all existing token holders at their discretion, provided they stay within the 2% annual cap.

**Recommendation:** Implement a timelock for minting operations or move the minting authority to a decentralized governance contract to prevent unilateral supply changes.


### `CP-05` — Centralized Transfer Restrictions  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch using the lockPool and unlockPool functions. This allows the owner to arbitrarily halt or enable token transfers, effectively freezing user assets or liquidity at will.

**Recommendation:** Remove the ability for the owner to pause transfers or implement a community-driven emergency pause mechanism that requires a consensus threshold.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 10,013 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

10,013 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $188K (DexScreener, all pools). 24h trading volume $1.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $188K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x744f...3fa9`](https://basescan.org/address/0x744f2017c13b190432f1537a7c5d9acd7d203fa9) |
| **Network** | Base |
| **Price** | $6.6700 |
| **24h Volume** | $1.61M |
| **Liquidity** | $187.8K |
| **Volume / Liquidity** | 8.5× |
| **Token Age** | 2h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1694 buys / 1522 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x445aa53de460c89e2f37a1f99863c84e903dbe00dc331abf0b172adff7ee706f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nodf-base-a6cd)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
