---
token: UDTF
ticker: UDTF
network: base
risk_score: 57
status: medium
date: 2026-10-29
---

# UDTF (UDTF) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/udtf-base-ab1a)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation and liquidity pool access. While the code follows standard OpenZeppelin patterns, the high level of administrative control over token supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** To improve security and trust, consider transitioning ownership to a decentralized multi-signature wallet or a DAO governance contract. This would mitigate the risk of a single compromised owner key affecting token supply or transferability.

Additionally, implement a timelock mechanism for all privileged functions, such as updateMintRate and lockPool. This would provide the community with a window to react to administrative changes, significantly reducing the impact of potential owner account compromise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-tested OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to standard implementation… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized. The owner has the ability to mint tokens and toggle transferability, which directly impacts the token's market value and liquidity.… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not implemented; the contract is immutable. This eliminates risks associated with proxy logic errors or malicious implementation updates. The logic remains fixed as deployed. |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to call updateMintRate and release, which can increase the total supply of the token. This allows the owner to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Implement a timelock for minting operations or transition control to a decentralized governance mechanism to prevent arbitrary supply increases.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable transfers for the pool. This grants the owner the power to effectively freeze liquidity or restrict user access to the token's utility.

**Recommendation:** Restrict the ability to toggle transferability to a decentralized voting process or remove the functionality entirely to ensure token fungibility.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 96.2% in other contracts. The deployer/owner wallet itself holds 16.2%. 7 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

7 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $70K (DexScreener, all pools). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $70K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3fcf...54a1`](https://basescan.org/address/0x3fcf5db8e04104cde5c589be5ef0e904c35a54a1) |
| **Network** | Base |
| **Price** | $0.525 |
| **24h Volume** | $1.03M |
| **Liquidity** | $69.8K |
| **Volume / Liquidity** | 14.8× |
| **Token Age** | 6h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2400 buys / 2986 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x0d3365ffbf62c735df56a58b7618668e90e9bfb2ab471301d117df387d06f935)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/udtf-base-ab1a)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
