---
token: 币安无忧
ticker: 币安无忧
network: bsc
risk_score: 55
status: medium
date: 2026-10-31
---

# 币安无忧 (币安无忧) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-c431c6-bsc)

---

## Audit Summary

BworryFreeToken is an ERC-20 token with centralized administrative controls. The contract allows a designated 'minter' address to mint new tokens, block specific addresses, and toggle transfer restrictions. While the code implements standard ERC-20 functionality correctly, the high degree of centralization poses significant risks to token holders, as the minter can unilaterally alter token economics and restrict liquidity.

> **Final Recommendation:** To improve security, the project should transition from a single 'minter' address to a multi-signature wallet or a decentralized governance contract (e.g., Governor Bravo or OpenZeppelin Governor). This would distribute the power to mint tokens or block addresses, preventing a single compromised key from impacting the entire ecosystem.

Additionally, consider implementing a timelock for all privileged functions. A delay of 24-48 hours on administrative actions would provide transparency and allow the community to react to significant changes in token economics or transfer rules.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-style ERC-20 logic, ensuring reliable token transfers and balance tracking. 7.1 Architecture follows a monolithic design, while 7.2 Code Security is… |
| **Governance / Economics** | 2/10 | High | The economic model is entirely controlled by a single address, creating a single point of failure for 7.4 Economic stability. 7.5 Governance is non-existent, as the minter has absolute authority over… |
| **Upgrades** | 3/10 | High | The contract is not upgradeable, which provides 7.7 Upgrades security by ensuring the code cannot be changed post-deployment. 7.8 Operations are fixed, meaning the current logic is immutable. This… |

## Security Findings

_🟡 4 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The minter address has the power to create new tokens at will, which can dilute the value of existing holdings. This function is restricted only to the minter, providing no protection for current token holders against supply inflation.

**Recommendation:** Implement a hard cap on total supply or transition minting authority to a decentralized governance contract with a timelock.


### `CP-05` — Centralized Control Over Transfer Functionality  *(Severity: Medium · Status: Unresolved)*

The minter can toggle the 'protocolOperating' switch or disable blocks, which directly controls whether users are allowed to transfer their tokens. This creates a risk where the minter can freeze all trading activity.

**Recommendation:** Remove the ability to pause or disable transfers, or move this control to a decentralized multi-signature wallet.


### `CP-06` — Ability to Blacklist Specific Holders  *(Severity: Medium · Status: Unresolved)*

The minter can add any address to a 'blockedPool' list, effectively preventing those users from moving or selling their tokens. This is a significant centralization risk that can be used to censor specific users.

**Recommendation:** Remove the blacklist functionality or require a community vote to add addresses to the blocklist.


### `CP-07` — Arbitrary Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

The minter can change the transfer fees and consume tax inventory, allowing them to extract value from the protocol at their discretion. This lack of transparency in fee management can negatively impact user trust.

**Recommendation:** Hardcode the fee structure or implement a governance-based mechanism for any future fee adjustments.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 28.6% of supply. Of that, 2.2% burned — not holders that can sell, so excluded from the concentration score. What remains: 7.1% in wallets, 19.3% in other contracts. 3,190 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,190 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $61K (DexScreener, all pools). 24h trading volume $517K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $61K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xfa44...2503`](https://bscscan.com/address/0xfa44a3a1e00220ca47acbd3f2ab52b9252662503) |
| **Network** | BNB Chain |
| **Price** | $0.00000019 |
| **24h Volume** | $516.6K |
| **Liquidity** | $60.5K |
| **Volume / Liquidity** | 8.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | 28.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3767 buys / 4434 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x07644ec759cf434ccc85799d3685c143830e885f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-c431c6-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
