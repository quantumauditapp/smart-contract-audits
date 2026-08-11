---
token: Prompt
ticker: PROMPT
network: base
risk_score: 75
status: critical
date: 2026-08-11
---

# Prompt (PROMPT) — Smart Contract Security Analysis | Base

> **Risk Score: 75/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/prompt-base)

---

## Audit Summary

The PromptToken contract implements an ERC-20 token with LayerZero OFT capabilities and a Wayfinder gateway mechanism. It utilizes OpenZeppelin's ReentrancyGuard and AccessControl for security. Key findings include centralized control over Wayfinder handler registration, a conditional initial token minting logic, and the inherent risks associated with external calls to untrusted handlers. The contract is not upgradeable via proxy.

> **Final Recommendation:** It is recommended to implement robust multi-signature control and potentially a time-lock for the `DEFAULT_ADMIN_ROLE` to mitigate the risks associated with centralized control over Wayfinder handler registration. Thoroughly audit and monitor all registered `InvokeWayfinderHandler` contracts, as they represent external trust dependencies. Additionally, ensure the initial token supply strategy is clearly documented and aligns with deployment plans across all target chains, especially for non-mainnet environments.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes OpenZeppelin's `ReentrancyGuard` and `AccessControl` for robust security, including explicit prevention of role renouncement and self-revocation (7.2 Code Security, 7.3 Access… |
| **Governance / Economics** | 2/10 | High | The contract implements a centralized access control model where the `DEFAULT_ADMIN_ROLE` (also `INVOKE_WAYFINDER_CONFIGURATION_ROLE`) has significant power, including the ability to register new… |
| **Upgrades** | 4/10 | Medium | The `PromptToken` contract is deployed as a standard implementation and does not utilize a proxy pattern, meaning it is not directly upgradeable. Any future changes to the contract logic would… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control over Wayfinder Gateway Configuration  *(Severity: High · Status: Unresolved)*

The `INVOKE_WAYFINDER_CONFIGURATION_ROLE`, which is aliased to `DEFAULT_ADMIN_ROLE`, has exclusive control over adding new `WayfinderGateway` contracts via `addWayfinderHandlerContract`. While the function prevents overwriting existing entries, a malicious or compromised administrator could register a harmful handler. If users then interact with this malicious handler through `invokeWayfinder`, it could lead to the loss of their native tokens or PROMPT tokens, as the `PromptToken` contract facilitates transfers to the configured destination addresses and calls the specified handler.

**Recommendation:** Implement robust multi-signature control for the `DEFAULT_ADMIN_ROLE` with a high threshold to ensure multiple trusted parties must approve critical changes. Consider adding a time-lock mechanism for `addWayfinderHandlerContract` to provide a window for community review or emergency intervention before a new handler becomes active.


### `M-01` — Conditional Initial Token Minting on Mainnet Only  *(Severity: Medium · Status: Unresolved)*

The contract's constructor includes a conditional minting statement: `if (block.chainid == 1) { _mint(msg.sender, SUPPLY); }`. This logic dictates that the initial `SUPPLY` of tokens will only be minted if the contract is deployed on Ethereum mainnet (chain ID 1). If deployed on any other chain, such as Base (chain ID 8453), the initial supply will not be minted, resulting in a token with zero initial supply. While this might be an intentional design for a cross-chain token where supply originates on Ethereum and is bridged, it represents a critical operational detail that could lead to unexpected behavior or a non-functional token if the deployment strategy is misunderstood or misconfigure…

**Recommendation:** Clearly document the intended deployment strategy and initial supply mechanism across all target chains. If an initial supply is desired on non-mainnet chains, adjust the minting condition to include relevant chain IDs or implement a separate, access-controlled minting function for post-deployment initialization on other networks.


### `L-01` — Reliance on External Untrusted Handler Logic  *(Severity: Low · Status: Unresolved)*

The `invokeWayfinder` function makes an external call to `InvokeWayfinderHandler(_handlerAddress).handleInvokeWayfinder`. While the `PromptToken` contract itself is protected by `ReentrancyGuard` and its internal state changes occur before the external call, the `_handlerAddress` is configured by an administrator. A malicious or buggy handler contract could lead to unexpected behavior, denial of service, or loss of funds for users interacting with that specific handler, even if the `PromptToken` contract remains secure. Users implicitly trust the logic of the configured handlers.

**Recommendation:** Emphasize the critical importance of thorough security audits and continuous monitoring for all registered `InvokeWayfinderHandler` contracts. Users should be made aware that interacting with a specific handler implies trust in that handler's logic and security. Consider implementing a 'pause' mechanism for specific handlers in case of detected vulnerabilities.


### `I-01` — Irreversible Role Renouncement Prevention  *(Severity: Informational · Status: Unresolved)*

The `renounceRole` and `renounceOwnership` functions are explicitly overridden to `revert("Cannot renounce role")`. This design choice prevents any administrator or owner from accidentally or maliciously renouncing their critical roles, ensuring that administrative control is always maintained within the system. This is a security-conscious decision to prevent loss of control.

**Recommendation:** Document this design choice clearly within the project's technical specifications, highlighting its role in maintaining consistent administrative oversight and preventing accidental loss of control.


### `I-02` — Self-Revocation Prevention for Roles  *(Severity: Informational · Status: Unresolved)*

The `revokeRole` function includes a `require(account != _msgSender(), "Cannot revoke role from self")` check. This prevents an administrator from accidentally or maliciously revoking their own role, which could lead to a loss of administrative control over the contract. This is a good security practice that enhances the robustness of the access control system.

**Recommendation:** Document this design choice clearly, explaining its purpose in preventing administrative lockout and ensuring continuous operational control.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x30c7...3452`](https://basescan.org/address/0x30c7235866872213f68cb1f08c37cb9eccb93452) |
| **Network** | Base |
| **Price** | $0.02268 |
| **24h Volume** | $55.8K |
| **Liquidity** | $100.7K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 77.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 337 buys / 279 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x953764548d1ca834e2b73fcd0d26a495336c99c8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/prompt-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
