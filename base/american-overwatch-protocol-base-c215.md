---
token: American Overwatch Protocol
ticker: AOP
network: base
risk_score: 75
status: high
date: 2026-10-24
---

# American Overwatch Protocol (AOP) — Smart Contract Security Analysis | Base

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-base-c215)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates and pool access. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over token supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** To improve security, the project should transition administrative functions to a decentralized governance model or a time-locked multi-sig wallet. This would prevent sudden changes to token supply or transfer rules without community oversight.

Additionally, consider implementing a 'grace period' or 'notice period' for any changes to the minting rate or pool locking status to provide transparency to the community and allow users to react to protocol changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The architecture leverages well-audited OpenZeppelin libraries for ERC-20 and governance functionality. 7.1 Architecture and 7.2 Code Security are robust, utilizing standard patterns for token… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are highly centralized. The owner has the ability to mint tokens and halt transfers, which directly impacts token value and liquidity. While inflation is… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as the contract is not a proxy. 7.8 Operations are handled via the owner address, which is currently a multi-sig. The lack of upgradeability ensures immutability of… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the ability to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply, which can dilute the value of existing holdings.

**Recommendation:** Implement a timelock on all minting-related functions to ensure that any increase in supply is transparent and predictable for token holders.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch via the lockPool and unlockPool functions. This allows the owner to unilaterally halt or enable token transfers, effectively freezing user assets.

**Recommendation:** Remove the ability for the owner to arbitrarily lock transfers, or restrict this functionality to a decentralized governance vote.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,064 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,064 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $202K (DexScreener, all pools). 24h trading volume $570K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $202K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x275a...01a8`](https://basescan.org/address/0x275a7155952a74109e526491f9812460d8e401a8) |
| **Network** | Base |
| **Price** | $0.3727 |
| **24h Volume** | $570.4K |
| **Liquidity** | $202.3K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 13h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1454 buys / 1393 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xd0934301892d7c0b6d3e64aa3feb2cb9cbf804ae3d09eb85fdec91d36d9d70a4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-overwatch-protocol-base-c215)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
