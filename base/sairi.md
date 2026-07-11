---
token: SAIRI
ticker: SAIRI
network: base
risk_score: 46
status: high
date: 2026-06-13
---

# SAIRI (SAIRI) — Smart Contract Security Analysis | Base

> **Risk Score: 46/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sairi-base)

---

## Audit Summary

The ClankerToken contract is an ERC20 token with extensions for burning, permits, and voting, leveraging OpenZeppelin's battle-tested libraries. It includes custom functionality for cross-chain minting/burning, restricted to a Superchain Token Bridge, and administrative control over metadata and the admin role itself. While the core ERC20 implementation is robust, the centralized control held by the `_admin` role for critical parameters and the admin transfer mechanism introduces a medium-level risk. The token's initial supply distribution and the nature of its `maxSupply_` parameter also warrant clear understanding.

> **Final Recommendation:** To enhance the security posture, consider implementing a multi-signature wallet for the `_admin` role to manage critical functions like `updateAdmin` and metadata changes. This would distribute control and reduce the risk associated with a single point of failure. Additionally, ensure comprehensive documentation clearly outlines the token's economic model, particularly regarding the initial supply distribution and the dynamic nature of the total supply due to cross-chain operations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1) of ClankerToken is sound, building upon well-audited OpenZeppelin ERC20 standards, including ERC20Burnable, ERC20Permit, and ERC20Votes. Code security (7.2) is… |
| **Governance / Economics** | 1/10 | High | Economically (7.4), the token's initial supply is minted entirely to the deployer on a specific chain, which is a design choice that centralizes initial distribution. The `maxSupply_` parameter is… |
| **Upgrades** | 8/10 | Low | The ClankerToken contract is not designed as an upgradeable proxy (7.7). This means that its logic cannot be modified post-deployment. While this eliminates upgrade-related risks, any future feature… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control of Admin Role and Metadata  *(Severity: Medium · Status: Unresolved)*

The `_admin` role has the sole authority to transfer the admin role (`updateAdmin`) and modify token metadata (`updateImage`, `updateMetadata`). A compromise of the `_admin` key could lead to unauthorized changes to the token's administrative control and public-facing information. This centralizes significant power in a single address, increasing the impact of a private key compromise. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Consider implementing a multi-signature wallet for the `_admin` role or introducing a time-lock for critical administrative actions like `updateAdmin` to provide a window for community review or emergency intervention. This would distribute control and enhance security.


### `L-01` — Initial Supply Distribution to Deployer  *(Severity: Low · Status: Unresolved)*

The constructor mints the entire `maxSupply_` to `msg.sender` (the deployer) if `block.chainid` matches `initialSupplyChainId_`. This design centralizes the initial token supply entirely with the deployer, which might not align with desired distribution strategies for a public token. While not a direct vulnerability, it's a significant design choice for token distribution. (7.4 Economic)

**Recommendation:** Ensure that this distribution model is intentional and clearly communicated to stakeholders. For future deployments, consider alternative initial distribution mechanisms, such as vesting contracts or a controlled release, if a broader initial distribution is desired.


### `I-01` — `maxSupply_` is not a Global Hard Cap  *(Severity: Informational · Status: Unresolved)*

The `maxSupply_` parameter in the constructor only dictates the initial supply minted on a specific chain. The `crosschainMint` function, callable by `Predeploys.SUPERCHAIN_TOKEN_BRIDGE`, allows for additional tokens to be minted, meaning the total supply across all chains can exceed the initial `maxSupply_`. This is a standard pattern for cross-chain tokens but should be explicitly understood by users and stakeholders. (7.4 Economic, 7.1 Architecture)

**Recommendation:** Clearly document that `maxSupply_` refers to the initial supply on a specific chain and that the total supply can increase through legitimate cross-chain bridging operations. This helps manage expectations regarding tokenomics and supply dynamics.


### `I-02` — Unused `_context` Variable  *(Severity: Informational · Status: Unresolved)*

The `_context` state variable is set in the constructor and exposed via the `context()` and `allData()` view functions, but there is no function to update its value after deployment. This makes it a static piece of metadata. If it's intended to be dynamic, its current implementation limits flexibility. (7.2 Code Security)

**Recommendation:** If `_context` is intended to be dynamic, add an `updateContext` function with appropriate access control. If it's meant to be static, ensure this is clearly documented. If it serves no purpose, consider removing it to reduce contract size and complexity.

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
