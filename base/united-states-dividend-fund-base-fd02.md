---
token: United States Dividend Fund
ticker: USDF
network: base
risk_score: 55
status: medium
date: 2026-10-28
---

# United States Dividend Fund (USDF) — Smart Contract Security Analysis | Base

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-base-fd02)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation and transfer restrictions. While the code follows standard OpenZeppelin patterns, the high degree of administrative control presents a significant centralization risk to token holders.

> **Final Recommendation:** To improve security, transition the ownership of the contract to a multi-signature wallet or a decentralized governance contract. This would mitigate the risk of a single compromised key performing unauthorized minting or locking user transfers.

Additionally, implement a timelock for all sensitive administrative functions such as updateMintRate and lockPool. This provides transparency to the community and allows users to react to significant changes in the token's economic parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for core ERC-20 and governance functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the contract owner. The owner has the authority to mint tokens and modify transfer rules, which directly impacts token value and… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as this is a non-proxy contract. 7.8 Operations are straightforward, relying on the owner to trigger vesting releases and inflation adjustments. The immutability of the… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply at their discretion, which dilutes the value of existing holdings.

**Recommendation:** Consider implementing a multi-signature requirement for minting actions or moving to a fixed, transparent emission schedule that does not require manual owner intervention.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable token transfers. This gives the owner the power to effectively freeze user funds or prevent trading at any time.

**Recommendation:** Remove the ability for the owner to arbitrarily lock transfers, or implement a community-driven governance vote to authorize such actions in emergency scenarios.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 14 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

14 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $287K (DexScreener, all pools). 24h trading volume $336K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.0909 — it does not hold a peg. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $287K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1421...6553`](https://basescan.org/address/0x1421d26dfa031505cd91c25f72e77dfed29d6553) |
| **Network** | Base |
| **Price** | $0.0909 |
| **24h Volume** | $335.8K |
| **Liquidity** | $287.1K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 12h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1495 buys / 994 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x594e1f9d9a8469ddfb003852b302db5c2848a7d1f3f8dddfa80c592f63f282c2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-base-fd02)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
