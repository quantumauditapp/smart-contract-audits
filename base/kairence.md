---
token: Kairence
ticker: KAI
network: base
risk_score: 41
status: medium
date: 2026-09-14
---

# Kairence (KAI) — Smart Contract Security Analysis | Base

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kairence-base)

---

## Audit Summary

The AgentToken contract implements an ERC20 token with a custom 'Humanship' ownership pattern and an explicitly disabled 'burnFrom' function. The code leverages OpenZeppelin standards, contributing to a solid foundation. Key findings include the centralized control inherent in the Humanship pattern, a minor usability issue in ownership transfer, and informational notes regarding initial token distribution and the disabled 'burnFrom' functionality. Overall, the contract exhibits a medium risk level, primarily due to the centralized nature of its control mechanisms.

> **Final Recommendation:** It is recommended to carefully manage the `_human` address, ensuring it is a secure multi-signature wallet or a robust governance mechanism to mitigate the risks associated with centralized control. Additionally, consider adding a check in `transferHumanship` to prevent setting `_pendingHuman` to the zero address, improving the robustness of the ownership transfer process. Thoroughly document the implications of the disabled `burnFrom` function for any future integrations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical implementation of AgentToken is generally robust, utilizing battle-tested OpenZeppelin ERC20 and ERC20Permit libraries (7.2 Code Security). The custom `Humanship` contract provides a… |
| **Governance / Economics** | 3/10 | High | The `Humanship` pattern centralizes significant control in a single `_human` address, which acts as the contract owner (7.5 Governance). This address has the sole authority to initiate ownership… |
| **Upgrades** | 7/10 | Low | The AgentToken contract is not implemented as an upgradeable proxy (7.7 Upgrades). This design choice eliminates risks associated with upgrade mechanisms, such as proxy initialization errors, storage… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control via Humanship  *(Severity: Medium · Status: Unresolved)*

The `Humanship` contract implements an ownership pattern where a single `_human` address holds significant control over the contract. This `_human` address is the sole entity capable of initiating an ownership transfer via `transferHumanship`. This centralization creates a single point of failure, as compromise of this address would grant an attacker full control over the contract's administrative functions (7.3 Access Control, 7.5 Governance).

**Recommendation:** Consider using a multi-signature wallet (e.g., Gnosis Safe) for the `_human` address to distribute control and reduce the risk associated with a single point of failure. Alternatively, implement a time-lock mechanism for critical administrative actions, including ownership transfers, to provide a window for intervention.


### `L-01` — `transferHumanship` allows setting `_pendingHuman` to `address(0)`  *(Severity: Low · Status: Unresolved)*

The `transferHumanship` function does not validate the `newHuman` address, allowing it to be set to `address(0)`. If `_pendingHuman` is set to `address(0)`, the `acceptHumanship` function can never be successfully called, as `msg.sender` can never be `address(0)`. This would effectively stall the ownership transfer process until the current `_human` initiates a new transfer with a valid address (7.2 Code Security).

**Recommendation:** Add a check in the `transferHumanship` function to ensure that `newHuman` is not the zero address. For example: `if (newHuman == address(0)) revert ZeroHuman();` (or a similar custom error).


### `I-01` — Initial Token Supply Minted to Deployer  *(Severity: Informational · Status: Unresolved)*

In the `AgentToken` constructor, the entire `totalSupply_` is minted to `msg.sender` (the contract deployer). This design choice centralizes the initial distribution of all tokens to a single address (7.4 Economic).

**Recommendation:** This is a design decision. Ensure that the implications of this centralized initial distribution are well-understood and align with the project's tokenomics and distribution strategy. If a more decentralized initial distribution is desired, consider alternative minting or distribution mechanisms.


### `I-02` — `burnFrom` Function Explicitly Disabled  *(Severity: Informational · Status: Unresolved)*

The `burnFrom` function in `AgentToken` is explicitly implemented to always revert with `BurnFromDisabled()`. This means that tokens cannot be burned from an approved address, which deviates from the standard ERC20 behavior where `burnFrom` is typically available for approved amounts (7.1 Architecture, 7.4 Economic).

**Recommendation:** This is a deliberate design choice. Ensure that all potential integrations and users are aware that `burnFrom` functionality is not available. Document this deviation from standard ERC20 behavior clearly in project documentation to prevent unexpected issues with third-party protocols that might rely on this function.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xca18...5ca1`](https://basescan.org/address/0xca18a528ea897040f715edc92e6e4572780c5ca1) |
| **Network** | Base |
| **Price** | $0.001225 |
| **24h Volume** | $59.5K |
| **Liquidity** | $74.6K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 12h |
| **Top-10 Holders** | 60.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 150 buys / 120 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x84bb5de343c30ebd863aaaea0c8d1013c12d4e876645f4ea610c67f71fa8490d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kairence-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-14*
