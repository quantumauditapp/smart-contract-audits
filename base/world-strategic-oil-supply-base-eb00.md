---
token: World Strategic Oil Supply
ticker: WSOS
network: base
risk_score: 57
status: medium
date: 2026-10-22
---

# World Strategic Oil Supply (WSOS) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/world-strategic-oil-supply-base-eb00)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates and pool access. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over token supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** To improve security, consider transitioning ownership to a multi-signature wallet or a decentralized governance contract to mitigate the risk of a single compromised key. Additionally, implementing a timelock on sensitive functions like updateMintRate would provide transparency and allow the community to react to significant changes in tokenomics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, voting, and permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to standard implementation… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance risks are elevated due to the owner's ability to mint tokens and halt transfers. The owner can influence the token supply via updateMintRate, which is capped at 2%… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not implemented as this is a non-proxy contract. 7.8 Operations are straightforward, relying on the owner to trigger vesting releases and inflation updates. No complex upgrade paths… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to call updateMintRate and release, which can increase the total supply of the token. This allows the owner to dilute existing holders at their discretion, provided the inflation remains within the 2% annual cap.

**Recommendation:** Implement a timelock for all supply-altering functions to ensure that token holders are notified before any significant changes to the total supply occur.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable transfers for specific pools. This grants the owner the power to effectively freeze user assets or halt trading activity at any time.

**Recommendation:** Restrict the ability to lock pools to a decentralized governance process or remove the functionality entirely to ensure the token remains permissionless and censorship-resistant.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.7% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.1% in other contracts. The deployer/owner wallet itself holds 16.2%. 3,007 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,007 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $50K (DexScreener, all pools). 24h trading volume $32K (DexScreener, all pools).

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
| **Contract** | [`0x3628...7131`](https://basescan.org/address/0x3628cc8f4aa26e161b0daafc8ed56392e1d87131) |
| **Network** | Base |
| **Price** | $0.00493 |
| **24h Volume** | $31.8K |
| **Liquidity** | $50.2K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 15h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1358 buys / 902 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xe07fb45d1d42351dc2a64ef78100425c3d90a80e8b2257c232e77b9f6a56ae4d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/world-strategic-oil-supply-base-eb00)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
