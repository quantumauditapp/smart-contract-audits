---
token: USOS
ticker: USOS
network: base
risk_score: 68
status: high
date: 2026-11-04
---

# USOS (USOS) — Smart Contract Security Analysis | Base

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usos-base)

---

## Audit Summary

The ClankerToken is an ERC-20 compliant token with cross-chain capabilities integrated via the Superchain Token Bridge. The architecture relies on the bridge contract to manage supply fluctuations across chains. While the core token logic follows standard OpenZeppelin implementations, the privileged cross-chain functions introduce significant centralization risks regarding supply control and user balance manipulation.

> **Final Recommendation:** The protocol should implement a multi-signature wallet or a timelock mechanism for the admin role to mitigate the risk of unauthorized metadata or administrative changes. Additionally, users should be aware that the Superchain Token Bridge holds the authority to burn or mint tokens, which is a necessary design choice for cross-chain functionality but represents a significant trust assumption.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard OpenZeppelin libraries for ERC-20, Votes, and Permit functionality, ensuring high interoperability. 7.1 Architecture is modular, leveraging the Superchain Token Bridge… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance risks are centralized within the bridge and the admin role. The admin can update metadata and administrative addresses, while the bridge controls the total supply. 7.6… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not explicitly implemented via proxy patterns in this contract. The contract is immutable in its current deployment. 7.8 Operations are straightforward, relying on standard bridge… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `QA-HOLDERS` — Who holds the supply  *(Severity: High · Status: Acknowledged)*

The ten largest holders own 99.3% of supply. What remains: 29.0% in wallets, 70.2% in other contracts. The deployer/owner wallet itself holds 21.8%. A holder that also controls the contract can sell into its own liquidity. 1,018 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xffa3…0762 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `CP-01` — Privileged Minting Authority  *(Severity: Informational · Status: Unresolved)*

The crosschainMint function allows the Superchain Token Bridge to increase the total supply of the token. This capability can lead to the dilution of existing token holders if the bridge is compromised or misconfigured. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Ensure the bridge contract is secured with robust access controls and consider implementing a supply cap if cross-chain minting needs to be bounded.


### `CP-02` — Privileged Balance Manipulation  *(Severity: Informational · Status: Unresolved)*

The crosschainBurn function allows the Superchain Token Bridge to directly remove tokens from any user's balance. This grants the bridge the power to seize or destroy user funds, which is a high-risk centralization point. Ownership is renounced, so no one can call these functions now.

**Recommendation:** Restrict the burn functionality to only allow users to burn their own tokens, or implement a transparent, verifiable process for cross-chain burns that minimizes the bridge's direct control over user balances.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,018 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $265K (DexScreener, all pools). 24h trading volume $45K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $265K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5df8...4a7c`](https://basescan.org/address/0x5df82b9cc7ddd86cf9c020b50fa3d25453a84a7c) |
| **Network** | Base |
| **Price** | $0.00000315 |
| **24h Volume** | $45.4K |
| **Liquidity** | $265.4K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 3h |
| **Top-10 Holders** | 99.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1883 buys / 449 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xa2a7ac25cbee9e9de3fed074a82fbca6d88d2cd078d0f87e39b55b280fe6c7ed)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usos-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
