---
token: Checkmate
ticker: CHECK
network: base
risk_score: 48
status: high
date: 2026-08-13
---

# Checkmate (CHECK) — Smart Contract Security Analysis | Base

> **Risk Score: 48/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/checkmate-base)

---

## Audit Summary

The ERC20FixedSupply contract implements a standard fixed-supply ERC-20 token with additional features like batch transfers, permit functionality, token recovery, and meta-transaction support. The contract utilizes a modular architecture with library-based storage. No critical vulnerabilities were identified, but centralized ownership and potential front-running in permit functions are noted.

> **Final Recommendation:** Implement robust operational security practices for the contract owner's private key to mitigate the risks associated with centralized control. Consider exploring multi-signature wallets or time-locked ownership transfers for enhanced security and decentralization. Ensure the external `IForwarderRegistry` is thoroughly audited and maintained, as its security directly impacts the meta-transaction functionality of this token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates a robust modular architecture, leveraging multiple OpenZeppelin-style extensions for ERC-20 functionality (7.1 Architecture). It includes features like safe transfers, batch… |
| **Governance / Economics** | 2/10 | High | The economic model is a fixed-supply ERC-20 token, with all tokens minted during construction, preventing inflationary risks post-deployment (7.4 Economic). Governance is centralized, with a single… |
| **Upgrades** | 6/10 | Medium | The contract is not designed as an upgradeable proxy, as indicated by `is_proxy: false`. However, it employs storage layout patterns (e.g., `Layout` structs, `LAYOUT_STORAGE_SLOT`… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 92.7% |
| **Top-3 Unlocked** | ⚠️ 98.1% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Ownership  *(Severity: Medium · Status: Unresolved)*

The `ContractOwnership` pattern grants significant control to a single owner address, including the ability to transfer ownership and potentially recover tokens via `TokenRecovery`. This introduces a single point of failure, where compromise of the owner's private key could lead to unauthorized control over critical contract functions.

**Recommendation:** Consider implementing a multi-signature wallet (e.g., Gnosis Safe) for the contract owner to distribute control and reduce the risk of a single point of failure. For highly sensitive operations, explore time-locked transactions or a more decentralized governance mechanism.


### `L-01` — Potential Front-Running in ERC20Permit  *(Severity: Low · Status: Unresolved)*

The `permit` function, while adhering to the EIP-2612 standard, can be susceptible to front-running attacks. An attacker observing a signed `permit` message could execute the `transferFrom` before the legitimate user, potentially leading to unexpected transaction ordering or a 'sandwich attack' if the `deadline` is set too far in the future or not used effectively.

**Recommendation:** Users should be advised to set a reasonable and short `deadline` for `permit` signatures to minimize the window for front-running. Developers should ensure the `ERC20Permit` implementation correctly validates `deadline` and `nonce` to prevent replay attacks.


### `I-01` — Storage Layout Pattern for Non-Upgradeable Contract  *(Severity: Informational · Status: Unresolved)*

The contract utilizes a storage layout pattern (e.g., `Layout` structs, `LAYOUT_STORAGE_SLOT`, `PROXY_INIT_PHASE_SLOT`) typically found in upgradeable proxy implementation contracts. While this contract is not explicitly a proxy, this design choice might be confusing or lead to issues if it were later used as an implementation without proper proxy setup, potentially causing storage collisions or unexpected behavior.

**Recommendation:** Clarify in documentation whether this contract is intended to be used as a standalone token or as an implementation for a proxy. If standalone, consider simplifying storage management if the proxy-specific patterns are not strictly necessary. If it is intended for future proxy use, ensure the proxy setup is robust and compatible with this storage pattern.


### `I-02` — Dependency on External Forwarder Registry  *(Severity: Informational · Status: Unresolved)*

The `ForwarderRegistryContext` relies on an external `IForwarderRegistry` for meta-transaction functionality. The security and trustworthiness of this external registry are critical for the proper and secure operation of meta-transactions within this token contract. Any compromise or malfunction of the registry could impact the ability to process meta-transactions.

**Recommendation:** Ensure the `IForwarderRegistry` contract is thoroughly audited, well-maintained, and controlled by a secure, preferably decentralized, entity. Document the expected behavior and security considerations of the forwarder registry for users and integrators.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9126...86eb`](https://basescan.org/address/0x9126236476efba9ad8ab77855c60eb5bf37586eb) |
| **Network** | Base |
| **Price** | $0.01359 |
| **24h Volume** | $191.1K |
| **Liquidity** | $274.9K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 92.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2163 buys / 2162 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x5a7b4970b2610aee4776a6944d9f2171ee6060b0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/checkmate-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
