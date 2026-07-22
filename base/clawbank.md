---
token: ClawBank
ticker: CLAWBANK
network: base
risk_score: 40
status: medium
date: 2026-07-22
---

# ClawBank (CLAWBANK) — Smart Contract Security Analysis | Base

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/clawbank-base)

---

## Audit Summary

The ClankerToken contract is an ERC20 token with extensions for burning, voting, and cross-chain functionality. It leverages battle-tested OpenZeppelin libraries for core token logic, enhancing code security. Key features include an admin role for metadata management and a one-time verification mechanism by an original admin. Cross-chain minting and burning are restricted to a predefined SuperchainTokenBridge. The primary risk identified is the centralized control held by the `_admin` role, which can update critical token metadata and transfer its own administrative privileges.

> **Final Recommendation:** To enhance the security posture, it is crucial to implement robust operational security practices for the `_admin` key. Consider multi-signature wallets or time-locks for sensitive administrative actions, especially for transferring the admin role. Additionally, ensure the `Predeploys.SUPERCHAIN_TOKEN_BRIDGE` is thoroughly audited and maintained, as the token's cross-chain integrity relies heavily on its security. Regular reviews of the administrative access controls and external dependencies are recommended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates strong technical foundations (7.1 Architecture, 7.2 Code Security). It inherits from well-audited OpenZeppelin ERC20, ERC20Permit, ERC20Votes, and ERC20Burnable contracts… |
| **Governance / Economics** | 1/10 | High | The contract's economic model (7.4 Economic) involves a fixed `maxSupply_` minted to the deployer on a specific chain, which is a clear design choice. Governance (7.5 Governance) is centralized… |
| **Upgrades** | 8/10 | Low | The ClankerToken contract is not designed with an upgrade mechanism (7.7 Upgrades), meaning its logic is immutable once deployed. This eliminates risks associated with proxy patterns or upgradeable… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 2 Informational_

### `M-01` — Centralized Control by Admin Role  *(Severity: Medium · Status: Unresolved)*

The `_admin` role has significant control over the contract, including the ability to update the token's image, metadata, and crucially, to transfer the `_admin` role itself to any address via `updateAdmin`, `updateImage`, and `updateMetadata` functions. If the `_admin` key is compromised, an attacker could alter token branding or transfer administrative control, potentially leading to reputational damage or further exploits.

**Recommendation:** Implement a multi-signature wallet for the `_admin` role to require multiple approvals for sensitive operations like `updateAdmin`. Consider adding a time-lock mechanism for `updateAdmin` to provide a window for community or team intervention if an unauthorized transfer is initiated. Clearly document the responsibilities and security procedures for managing the `_admin` key.


### `I-01` — Reliance on External Bridge Security  *(Severity: Informational · Status: Unresolved)*

The `crosschainMint` and `crosschainBurn` functions are critical for maintaining the token's supply consistency across chains. These functions are exclusively callable by `Predeploys.SUPERCHAIN_TOKEN_BRIDGE`. The security and integrity of the ClankerToken's cross-chain operations are entirely dependent on the security of this external bridge contract.

**Recommendation:** Ensure that the `Predeploys.SUPERCHAIN_TOKEN_BRIDGE` contract is rigorously audited, continuously monitored, and maintained with the highest security standards. Any vulnerability in the bridge could directly impact the ClankerToken's supply and value. Consider establishing a robust incident response plan for bridge-related issues.


### `I-02` — Fixed Initial Supply Distribution to Deployer  *(Severity: Informational · Status: Unresolved)*

In the constructor, the entire `maxSupply_` is minted to `msg.sender` (the contract deployer) if `block.chainid` matches `initialSupplyChainId_`. This design choice means the initial token distribution is entirely concentrated with the deployer on a specific chain, rather than being distributed or held by a treasury contract.

**Recommendation:** This is a design decision, not a vulnerability. However, it's important for the project to clearly communicate this initial distribution strategy to stakeholders. If not already planned, consider a transparent mechanism for subsequent distribution or management of this initial supply to avoid perceptions of centralization or to fund ecosystem development.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1633...eb07`](https://basescan.org/address/0x16332535e2c27da578bc2e82beb09ce9d3c8eb07) |
| **Network** | Base |
| **Price** | $0.00001299 |
| **24h Volume** | $33.7K |
| **Liquidity** | $678.3K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 34.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 211 buys / 494 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xb04b187062efbf94cf9b4b6f42bf688258d3c88b7c9283bbc74dbbfb1af40d54)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/clawbank-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*
