---
token: CLAWNCH
ticker: CLAWNCH
network: base
risk_score: 6
status: low
date: 2026-09-04
---

# CLAWNCH (CLAWNCH) — Smart Contract Security Analysis | Base

> **Risk Score: 6/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/clawnch-base)

---

## Audit Summary

The ClankerToken contract is an ERC20 token implementation with additional features for cross-chain operations, admin-controlled metadata, and voting capabilities. It leverages battle-tested OpenZeppelin libraries, contributing to its code security. However, the contract exhibits a high degree of centralization around its `_admin` role and relies heavily on an external Superchain Token Bridge for cross-chain minting/burning, introducing significant operational and economic risks. The contract is not upgradeable, which limits future flexibility.

> **Final Recommendation:** Implement a multi-signature wallet or a time-locked governance mechanism for the `_admin` role to mitigate the risks associated with centralized control. Conduct a thorough security audit of the `Predeploys.SUPERCHAIN_TOKEN_BRIDGE` contract, as its security directly impacts the integrity of the token's cross-chain supply. Consider the implications of the non-upgradeable design for long-term maintenance and future feature development.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract leverages battle-tested OpenZeppelin libraries for its ERC20, ERC20Permit, ERC20Votes, and ERC20Burnable functionalities, ensuring a robust foundation (7.2 Code Security). The… |
| **Governance / Economics** | 7/10 | Low | The economic model involves an initial mint of the entire `maxSupply_` to the deployer on a specific chain, centralizing initial distribution (7.4 Economic). The contract's cross-chain capabilities… |
| **Upgrades** | 9/10 | Low | The `ClankerToken` contract is deployed as a standard, non-proxy implementation, meaning its logic is immutable post-deployment (7.7 Upgrades). This design choice ensures immutability and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Reliance on External Superchain Token Bridge  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `crosschainMint` and `crosschainBurn` functions are exclusively callable by `Predeploys.SUPERCHAIN_TOKEN_BRIDGE`. The security and integrity of this external bridge are paramount, as any vulnerability or misconfiguration in the bridge could lead to unauthorized minting or burning of `ClankerToken`, directly impacting the token's supply, value, and overall economic stability (7.6 External, 7.4 Economic).

**Recommendation:** Ensure that the `Predeploys.SUPERCHAIN_TOKEN_BRIDGE` contract has undergone rigorous security audits and is maintained by a reputable team. Implement robust monitoring for `crosschainMint` and `crosschainBurn` events to detect any anomalous activity originating from the bridge. Consider a mechanism for emergency pausing of cross-chain operations if a bridge vulnerability is detected.


### `M-02` — Centralized Control of Admin Role and Metadata  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_admin` address has significant control over the contract, including the ability to transfer the admin role itself via `updateAdmin` and modify critical token metadata (`updateImage`, `updateMetadata`). A compromise of this single address would allow an attacker to seize control of these functions, potentially impacting the token's perceived legitimacy, branding, or even facilitating social engineering attacks. This represents a single point of failure for critical administrative functions (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the `_admin` role to require multiple approvals for sensitive operations like `updateAdmin` and metadata changes. Alternatively, introduce a time-lock mechanism for `updateAdmin` to provide a window for community or team intervention in case of a compromised key.


### `L-01` — Single Point of Initial Supply Minting  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The entire `maxSupply_` is minted to `msg.sender` (the deployer) during construction if `block.chainid` matches `initialSupplyChainId_`. This design centralizes the initial token distribution entirely with the deployer. While common for new tokens, it could pose a risk if the deployer's address is compromised before distribution, or if the distribution strategy is not transparently communicated (7.4 Economic, 7.8 Operations).

**Recommendation:** Ensure that the deployer's address is secured with best practices (e.g., hardware wallet, multi-sig). Clearly communicate the initial distribution strategy to the community to manage expectations and transparency. This is largely an operational concern for the project team.


### `I-01` — Non-Upgradeable Contract Design  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ClankerToken` contract is deployed as a standard implementation contract and does not utilize any proxy pattern. This means that its logic cannot be modified or upgraded after deployment, making it immutable. Any future bug fixes, security patches, or feature enhancements would require a new contract deployment and a migration of token holders (7.7 Upgrades).

**Recommendation:** Acknowledge the implications of a non-upgradeable design. While it provides immutability guarantees, it sacrifices flexibility. Ensure that the current contract logic is thoroughly tested and robust to minimize the need for future changes. If future upgradeability is desired, a proxy pattern should be considered for new deployments.


### `I-02` — Unused ERC20Votes Functionality  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract inherits `ERC20Votes` and correctly overrides the `_update` function, enabling voting power tracking based on token balances. However, no explicit governance mechanism or voting logic is implemented within this contract itself that utilizes this voting power. While this provides the foundation for future governance, its current inclusion without active use might be considered informational (7.1 Architecture).

**Recommendation:** Clarify the project's intention for the `ERC20Votes` functionality. If a governance system is planned, ensure it integrates correctly with this token. If not, consider if the overhead of including `ERC20Votes` is justified, although it is a standard and well-audited OpenZeppelin extension.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa1f7...47be`](https://basescan.org/address/0xa1f72459dfa10bad200ac160ecd78c6b77a747be) |
| **Network** | Base |
| **Price** | $0.00000335 |
| **24h Volume** | $288.9K |
| **Liquidity** | $157.5K |
| **Volume / Liquidity** | 1.8× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 47.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 507 buys / 1308 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x03d3c21ea1daf51dd2898ebaf9342a93374877ba6ab34cc7ffe5b5d43ee46e0a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/clawnch-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-04*
