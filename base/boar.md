---
token: boar
ticker: BOAR
network: base
risk_score: 4
status: low
date: 2026-09-28
---

# boar (BOAR) — Smart Contract Security Analysis | Base

> **Risk Score: 4/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/boar-base)

---

## Audit Summary

The ClankerToken contract implements an ERC20 token with burnable, permit, and voting functionalities, leveraging OpenZeppelin standards. It includes custom roles for an `_admin` and an `_originalAdmin`, and integrates cross-chain minting/burning via a predefined bridge. While the core ERC20 implementation is robust, the contract exhibits significant centralization risks due to the `_admin` role's extensive control and a critical external dependency on the `SUPERCHAIN_TOKEN_BRIDGE` for supply management. These factors contribute to a High overall risk level.

> **Final Recommendation:** It is strongly recommended to implement a multi-signature wallet or a time-locked mechanism for the `_admin` role to mitigate the risks associated with centralized control. This would significantly enhance the security of administrative functions such as `updateAdmin` and metadata modifications. Additionally, ensure rigorous security audits and continuous monitoring of the `SUPERCHAIN_TOKEN_BRIDGE` contract, as its integrity is paramount to the ClankerToken's supply management and overall economic stability. Clearly document the intended behavior of the `maxSupply_` parameter and the `_originalAdmin` role's limited utility to manage user expectations and operational procedures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract is built upon well-audited OpenZeppelin ERC20 standards, including extensions for `ERC20Permit`, `ERC20Votes`, and `ERC20Burnable`, which enhances code security (7.2 Code Security). It… |
| **Governance / Economics** | 6/10 | Medium | The contract's economic model (7.4 Economic) is heavily influenced by its cross-chain capabilities, with `crosschainMint` and `crosschainBurn` functions allowing the `SUPERCHAIN_TOKEN_BRIDGE` to… |
| **Upgrades** | 9/10 | Low | The ClankerToken contract is implemented as a standard, non-upgradeable contract (7.7 Upgrades). This design choice eliminates the complexities and potential vulnerabilities associated with proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · ⚪ 1 Informational_

### `M-01` — Limited Utility of `_originalAdmin` Role  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_originalAdmin` role is immutable and only has the permission to call the `verify()` function once. After this single invocation, the `_originalAdmin` address retains no further special privileges within the contract. If the `verify()` function is never called, the token remains in an unverified state, potentially impacting its perceived legitimacy or integration with other systems. (7.3 Access Control, 7.8 Operations)

**Recommendation:** Document the intended lifecycle and importance of the `verify()` function, clarifying its purpose and the implications if it remains uncalled. Consider if the `_originalAdmin` role could be removed after `verify()` is called, or if its single-use nature is intentional and well-understood within the protocol's design.


### `M-02` — Centralized Control by `_admin` Role  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_admin` role has exclusive control over critical functions such as `updateAdmin`, `updateImage`, and `updateMetadata`. This allows the `_admin` to transfer the administrative role to any address and modify token-related metadata. A compromise of the `_admin` key could lead to unauthorized changes to the token's perceived identity and potential loss of control. (7.3 Access Control, 7.5 Governance)

**Recommendation:** Consider implementing a multi-signature wallet for the `_admin` role or a time-locked mechanism for sensitive administrative changes to reduce the risk of a single point of failure. This would require multiple approvals or a delay period before critical changes can be enacted.


### `M-03` — Critical External Dependency on `SUPERCHAIN_TOKEN_BRIDGE`  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `crosschainMint` and `crosschainBurn` functions, which directly affect the token's total supply, are exclusively callable by `Predeploys.SUPERCHAIN_TOKEN_BRIDGE`. This introduces a critical external dependency. Any vulnerability or compromise within the `SUPERCHAIN_TOKEN_BRIDGE` contract could lead to unauthorized minting, burning, or manipulation of the token's supply, severely impacting its economic integrity. (7.4 Economic, 7.6 External)

**Recommendation:** Ensure the `SUPERCHAIN_TOKEN_BRIDGE` contract is thoroughly audited, robust, and secured with strong access controls and operational safeguards. Implement continuous monitoring for unusual activity originating from the bridge address to detect and respond to potential compromises promptly.


### `I-01` — Misleading `maxSupply_` Parameter in Constructor  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The constructor takes a `maxSupply_` parameter, which is minted to `msg.sender` if `block.chainid == initialSupplyChainId_`. However, the `crosschainMint` function, controlled by `SUPERCHAIN_TOKEN_BRIDGE`, allows for arbitrary minting of new tokens. This means the `maxSupply_` parameter does not represent a hard cap on the total token supply, as the actual supply is ultimately governed by the logic of the external bridge contract. This could be misleading for users expecting a fixed maximum supply. (7.4 Economic)

**Recommendation:** Clarify in documentation that `maxSupply_` refers to the initial supply on the designated chain and that the overall token supply is dynamically managed by the cross-chain bridge. Consider renaming the parameter to `initialChainSupply` or similar for better clarity to avoid confusion.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0cbf...bb07`](https://basescan.org/address/0x0cbf291ba052174879d90bf781df1a5f2bc5bb07) |
| **Network** | Base |
| **Price** | $0.00001342 |
| **24h Volume** | $1.98M |
| **Liquidity** | $347.5K |
| **Volume / Liquidity** | 5.7× |
| **Token Age** | 2d |
| **Top-10 Holders** | 30.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3771 buys / 2940 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xef256e214c45aab706ca54d6e2c5d0ca42b87895a43e97b382ea012d13e78e49)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/boar-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-28*
