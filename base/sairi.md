---
token: SAIRI
ticker: SAIRI
network: base
risk_score: 56
status: high
date: 2026-06-13
---

# SAIRI (SAIRI) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sairi-base)

---

## Audit Summary

The ClankerToken contract implements an ERC20 token with cross-chain capabilities and administrative controls. The contract leverages well-audited OpenZeppelin standards for core token functionality. Key areas of concern include a potentially misleading parameter name for token supply, centralized administrative control over metadata, and the inherent dependency on an external bridge for cross-chain operations.

> **Final Recommendation:** The ClankerToken contract is generally well-written and leverages robust OpenZeppelin components. Addressing the misleading `maxSupply_` parameter and considering a multi-sig or time-lock for the `_admin` role would significantly enhance the contract's transparency and security posture. For long-term sustainability, the lack of upgradeability should be carefully considered against future needs.

For enhanced security and operational flexibility, we recommend a Premium Deploy option. This includes a comprehensive pre-deployment review, gas optimization analysis, and continuous monitoring post-deployment to identify and mitigate potential risks in real-time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good technical practices by inheriting from battle-tested OpenZeppelin ERC20 extensions (ERC20Permit, ERC20Votes, ERC20Burnable), which enhances code security (7.2). It also… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) initially mints a specified `maxSupply_` on a single chain, but the `crosschainMint` function allows the `SUPERCHAIN_TOKEN_BRIDGE` to mint additional tokens without a global… |
| **Upgrades** | 8/10 | Low | The ClankerToken contract is deployed as a standard, non-upgradeable implementation (7.7). This design choice means that once deployed, the contract's logic cannot be modified. Any future bug fixes… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Misleading `maxSupply_` Parameter and Uncapped Supply  *(Severity: High · Status: Unresolved)*

The constructor parameter `maxSupply_` implies a maximum token supply, but it only dictates the initial supply on a specific chain (`initialSupplyChainId_`). The `crosschainMint` function allows the `SUPERCHAIN_TOKEN_BRIDGE` to mint an arbitrary amount of new tokens without any explicit global supply cap. This design choice, combined with the misleading parameter name, could lead to user confusion, unexpected inflation, and a loss of confidence in the token's economic model (7.4).

**Recommendation:** Rename `maxSupply_` to `initialSupply_` or `initialChainSupply_` to accurately reflect its purpose. Implement a global maximum supply mechanism if the intention is to have a capped token, or clearly document that the token has an uncapped supply managed by the bridge.


### `M-01` — Centralized Control of Token Parameters and Admin Role  *(Severity: Medium · Status: Unresolved)*

The `_admin` role has extensive control, including the ability to update the token's `_image`, `_metadata`, and crucially, to transfer the `_admin` role itself via `updateAdmin`. While `_originalAdmin` is immutable for the one-time `verify()` call, the mutable `_admin` represents a single point of failure. If the `_admin` key is compromised, an attacker could alter token metadata or transfer the admin role to themselves, potentially impacting user trust and the token's representation (7.3).

**Recommendation:** Consider implementing a multi-signature wallet for the `_admin` role or introducing a time-lock for critical administrative actions, especially for `updateAdmin`, to mitigate the risk of a single key compromise. This enhances access control and operational security (7.8).


### `L-01` — Dependency on External Bridge Security  *(Severity: Low · Status: Unresolved)*

The `crosschainMint` and `crosschainBurn` functions grant exclusive minting and burning privileges to the `Predeploys.SUPERCHAIN_TOKEN_BRIDGE`. The security and integrity of the token's supply are therefore directly dependent on the security of this external bridge contract. Any vulnerability or compromise within the `SUPERCHAIN_TOKEN_BRIDGE` could lead to unauthorized minting or burning of ClankerTokens (7.6).

**Recommendation:** Ensure the `SUPERCHAIN_TOKEN_BRIDGE` contract undergoes rigorous security audits and maintains robust operational security. Implement monitoring for unusual activity originating from the bridge address to detect potential compromises (7.8).


### `I-01` — No Upgradeability  *(Severity: Informational · Status: Unresolved)*

The `ClankerToken` contract is deployed as a standard, non-upgradeable implementation. This means that once deployed, its logic cannot be modified. Any future bug fixes, feature enhancements, or changes to the token's economic model would necessitate deploying a new contract and migrating users, which can be a complex and disruptive process (7.7).

**Recommendation:** For long-term projects, consider using an upgradeable proxy pattern (e.g., UUPS or Transparent Proxies) to allow for future contract modifications without requiring redeployment and migration. This provides flexibility for future protocol evolution.


### `I-02` — `ERC20Votes` Without On-Chain Governance  *(Severity: Informational · Status: Unresolved)*

The contract inherits `ERC20Votes`, which enables tracking of voting power based on token holdings. However, the contract itself does not implement any on-chain governance mechanisms (e.g., a Governor contract). While this is a common pattern for tokens intended for future governance integration, it means that currently, voting power is only usable off-chain or requires a separate governance contract to be deployed and integrated (7.5).

**Recommendation:** Clearly communicate the intended use of `ERC20Votes` and outline the roadmap for any future on-chain governance integration. If on-chain governance is planned, ensure the governance contract is properly integrated and secured.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xde61...eb07`](https://basescan.org/address/0xde61878b0b21ce395266c44d4d548d1c72a3eb07) |
| **Network** | Base |
| **Price** | $0.00001573 |
| **24h Volume** | $143.2K |
| **Liquidity** | $726.9K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 31.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 240 buys / 719 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x8e1737aab1bb49dcdbfa014868c1cfb8702b7b66ce20e023e7d6f7427f9e1537)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sairi-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-13*
