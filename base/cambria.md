---
token: Cambria
ticker: RSGP
network: base
risk_score: 54
status: medium
date: 2026-10-29
---

# Cambria (RSGP) — Smart Contract Security Analysis | Base

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cambria-base)

---

## Audit Summary

The BurnMintERC20 contract is a standard ERC-20 implementation with additional minting and burning capabilities managed via OpenZeppelin AccessControl. The architecture is robust, utilizing battle-tested libraries for core functionality. The primary risk is centralized control over supply expansion, which is inherent to the design of this token type.

> **Final Recommendation:** The protocol should implement a multi-signature wallet or a time-locked governance contract to manage the MINTER_ROLE. This prevents a single compromised key from unilaterally inflating the token supply.

Ensure that the address assigned to the DEFAULT_ADMIN_ROLE is highly secured, as it holds the power to reassign all other roles within the system.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages standard OpenZeppelin libraries for ERC-20 and AccessControl, ensuring high code quality and reliability. 7.1 Architecture follows standard patterns, while 7.2 Code Security is… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic risk is centered on the minting authority, which can dilute token holders. 7.5 Governance is managed via role-based access, allowing for granular control over administrative actions. The… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are straightforward, relying on standard ERC-20 interfaces. The lack of upgradeability ensures immutability of the logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 74.3% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 4 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 16.4% in wallets, 83.5% in other contracts. The deployer/owner wallet itself holds 80.8%. A holder that also controls the contract can sell into its own liquidity. 11 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows addresses with the MINTER_ROLE to create new tokens at will. This increases the total supply and dilutes the value of existing holdings, representing a significant centralization risk.

**Recommendation:** Restrict the MINTER_ROLE to a multi-signature wallet or a decentralized governance contract to ensure that minting events are transparent and subject to community oversight.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 3 address(es) other than the owner/deployer. One of them — a wallet, 0x0817…d627 — holds 74.3% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 71% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

11 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $391K (DexScreener, all pools). 24h trading volume $711K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner key. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $391K of DEX liquidity across 9 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x44b6...9e85`](https://basescan.org/address/0x44b63af715d5ef02cc3646a6ce96875e11d69e85) |
| **Network** | Base |
| **Price** | $0.002701 |
| **24h Volume** | $583.6K |
| **Liquidity** | $275.7K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 0h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 702 buys / 1264 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x8e859b6cf564c4ac2b848693c85c496e81dbf6c8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cambria-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
