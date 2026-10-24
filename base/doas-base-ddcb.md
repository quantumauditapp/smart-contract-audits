---
token: DOAS
ticker: DOAS
network: base
risk_score: 57
status: medium
date: 2026-10-24
---

# DOAS (DOAS) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/doas-base-ddcb)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with governance capabilities (ERC20Votes) and centralized administrative controls. The protocol relies on a single owner to manage inflation, pool locking, and vesting releases. While the code follows standard OpenZeppelin patterns, the high level of centralization poses a significant risk to token holders.

> **Final Recommendation:** To improve security, the protocol should transition from a single-owner model to a multi-signature wallet or a decentralized governance contract (e.g., Governor Bravo/Compound). This would mitigate the risk of a single point of failure regarding token minting and transfer restrictions.

Additionally, consider implementing a timelock for all administrative functions. A delay of 24-48 hours on functions like updateMintRate or lockPool would provide transparency to the community and allow users to react to significant changes in tokenomics.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for core ERC-20 and governance functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are dominated by the owner's ability to mint tokens and restrict transfers. While 7.6 External dependencies are minimal, the economic model is subject to… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. 7.8 Operations are handled via direct owner calls. The immutability of the contract logic provides a baseline of security, though it… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply at their discretion, which can dilute the value of existing holdings.

**Recommendation:** Transition ownership to a decentralized governance contract or implement a hard-coded, immutable inflation schedule that cannot be modified by any single address.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch using the lockPool and unlockPool functions. This grants the owner the power to unilaterally halt or resume token transfers, effectively freezing user assets.

**Recommendation:** Remove the ability to lock transfers or restrict this functionality to a decentralized voting process to prevent potential abuse of power.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,830 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,830 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $101K (DexScreener, all pools). 24h trading volume $370K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $101K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x935a...fb4e`](https://basescan.org/address/0x935a7ec64a2a308aef2a9ac2464cba80f9d1fb4e) |
| **Network** | Base |
| **Price** | $0.2291 |
| **24h Volume** | $370.2K |
| **Liquidity** | $101.0K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 12h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1161 buys / 1137 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xc9ef8f902a4497d66bc8d0c9a01128ff848a40d3158ca1c336b9e61edb6d1a52)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/doas-base-ddcb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
