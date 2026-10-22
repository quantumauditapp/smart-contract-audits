---
token: US Dividend Reserve (USDR)
ticker: USDR
network: base
risk_score: 64
status: medium
date: 2026-10-22
---

# US Dividend Reserve (USDR) (USDR) — Smart Contract Security Analysis | Base

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/us-dividend-reserve-usdr-base-b52c)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation, token distribution, and transfer restrictions. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over supply and transferability presents a significant centralization risk.

> **Final Recommendation:** To improve security and trust, consider transitioning ownership to a multi-signature wallet or a decentralized governance contract. This would mitigate the risk of a single point of failure regarding token minting and transfer restrictions.

Additionally, implement a timelock mechanism for all privileged functions. This provides transparency and allows the community to react to administrative changes before they are executed on-chain.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture leverages well-audited OpenZeppelin libraries for ERC-20, Votes, and Permit functionality (7.1, 7.2). Code security is robust with proper use of modifiers and standard state… |
| **Governance / Economics** | 2/10 | High | Economic control is highly centralized under the owner address (7.5). The owner has the authority to mint tokens and toggle transferability, which directly impacts token value and liquidity (7.4).… |
| **Upgrades** | 4/10 | Medium | The contract is not a proxy and is immutable (7.7). Operations are limited to the defined administrative functions (7.8). No upgradeability patterns are present, ensuring the logic remains consistent… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply at their discretion, which can dilute the value of existing holdings.

**Recommendation:** Implement a timelock on minting functions or transition to a decentralized governance model where minting requires community approval.


### `CP-05` — Centralized Transfer Control  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch via the lockPool and unlockPool functions. This allows the owner to unilaterally freeze or unfreeze token transfers, effectively controlling the liquidity of the token.

**Recommendation:** Remove the ability to arbitrarily pause transfers or implement a transparent, community-governed mechanism for emergency pauses.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.0% in wallets, 80.2% in other contracts. The deployer/owner wallet itself holds 16.0%. 3,028 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,028 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $49K (DexScreener, all pools). 24h trading volume $30K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.002408 — it does not hold a peg. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $49K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x04e1...5076`](https://basescan.org/address/0x04e1be61539ff243b283e122af32ed8a0eda5076) |
| **Network** | Base |
| **Price** | $0.002408 |
| **24h Volume** | $30.3K |
| **Liquidity** | $49.2K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 15h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1862 buys / 1828 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x6d66ddd2b394bef09fadc23468754aff1656fcd91c0a8777ed26275ac9020f66)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/us-dividend-reserve-usdr-base-b52c)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
