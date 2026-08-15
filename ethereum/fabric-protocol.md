---
token: Fabric Protocol
ticker: ROBO
network: ethereum
risk_score: 48
status: high
date: 2026-08-15
---

# Fabric Protocol (ROBO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 48/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fabric-protocol-eth)

---

## Audit Summary

The ERC20Token contract implements a standard ERC20 token with OpenZeppelin's ERC20Permit and Ownable extensions. The contract features a fixed total supply, user-initiated burning, and an owner-controlled function to restore the supply up to the initial cap. While the technical implementation is robust, leveraging audited libraries and Solidity 0.8+ safety features, the centralized minting capability held by the owner introduces a High economic risk. The owner (a multisig) can mint tokens up to the initial total supply, which could impact token value if not managed transparently. Additionally, the ability to change token metadata (name/symbol) is restricted to a single instance, which might be inflexible for future branding needs.

> **Final Recommendation:** It is recommended to clearly communicate the owner's ability to restore the token supply up to the initial `TOTAL_SUPPLY` to all token holders, as this can impact tokenomics. Consider implementing a timelock for sensitive owner actions, such as `restoreSupply`, to provide transparency and allow community reaction time. For the EIP-712 domain separator, optimize its computation by caching the value to reduce gas costs for `permit` operations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages well-audited OpenZeppelin libraries for ERC20, ERC20Permit, and Ownable functionalities (7.2 Code Security). Solidity version 0.8.20 provides default overflow/underflow checks… |
| **Governance / Economics** | 3/10 | High | The contract's economic model features a fixed `TOTAL_SUPPLY`, but the `restoreSupply` function grants the owner the power to mint tokens up to this cap if the current supply is lower (7.4 Economic).… |
| **Upgrades** | 6/10 | Medium | The contract is not designed to be upgradeable; it does not implement any proxy patterns (7.7 Upgrades). This simplifies the architecture by removing upgrade-related complexities and risks. The… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Minting Power for Supply Restoration  *(Severity: High · Status: Unresolved)*

The `restoreSupply` function allows the contract owner to mint new tokens up to the `TOTAL_SUPPLY` constant. While the total supply is capped, this function grants the owner significant power to re-introduce tokens into circulation that were previously burned, effectively undoing deflationary events. This centralized control over supply restoration can lead to unexpected inflation and impact token value if not managed transparently or with community oversight.

**Recommendation:** Implement a timelock for the `restoreSupply` function to introduce a delay before execution, allowing for community review and reaction. Alternatively, consider a multi-signature approval process beyond the standard owner for such a critical function, or remove the function entirely if the intent is for a truly fixed and non-restorable supply.


### `M-01` — Single Metadata Change Limitation  *(Severity: Medium · Status: Unresolved)*

The `updateNameAndSymbol` function, callable only by the owner, includes a `require(!_metadataChanged, "Name and symbol can only be changed once")` check. This design choice permanently restricts the ability to update the token's name and symbol after the first modification. While this prevents arbitrary changes, it removes flexibility for future branding, re-organizations, or corrections if a mistake is made during the single allowed update.

**Recommendation:** Assess if this single-change limitation aligns with long-term project goals. If future flexibility is desired, consider removing the `_metadataChanged` flag or implementing a more robust governance mechanism for metadata updates, potentially with a timelock or multi-signature approval for subsequent changes.


### `L-01` — Inefficient EIP-712 Domain Separator Computation  *(Severity: Low · Status: Unresolved)*

The `_buildCurrentDomainSeparator` function, which is called by `DOMAIN_SEPARATOR` and `_hashTypedDataV4`, recomputes the EIP-712 domain separator on every invocation. In OpenZeppelin's standard `ERC20Permit` implementation, the domain separator is typically cached to avoid redundant computations, especially since the `name` and `symbol` (which are part of the domain) are only intended to change once. Repeated computation incurs unnecessary gas costs for `permit` operations.

**Recommendation:** Cache the EIP-712 domain separator in a state variable and update it only when the token's name or symbol changes via `updateNameAndSymbol`. This will optimize gas usage for `permit` calls.


### `I-01` — Redundant Name and Symbol State Variables  *(Severity: Informational · Status: Unresolved)*

The contract declares private state variables `_name` and `_symbol` in addition to inheriting these properties from the `ERC20` base contract. While the `name()` and `symbol()` overrides correctly return these private variables, and they are used to facilitate the `updateNameAndSymbol` function, it introduces a slight redundancy. If not carefully managed, this could lead to inconsistencies, although in this specific implementation, they are updated together.

**Recommendation:** Ensure that the custom `_name` and `_symbol` variables are always kept in sync with the underlying ERC20 state if the intention is to override the base ERC20 behavior. The current implementation correctly handles this by overriding the getters and updating the custom variables.


### `I-02` — Fixed Total Supply with Owner-Controlled Restoration  *(Severity: Informational · Status: Unresolved)*

The contract defines a `TOTAL_SUPPLY` constant, implying a fixed maximum supply. However, the `restoreSupply` function allows the owner to mint tokens up to this `TOTAL_SUPPLY` if the current supply is lower due to burns. This means the 'fixed' total supply is only a cap, and the circulating supply can fluctuate up to this cap based on owner actions, rather than being strictly immutable after initial minting.

**Recommendation:** Clearly document and communicate this behavior to all token holders and potential investors. Emphasize that while there is a maximum supply, the actual circulating supply can be increased by the owner up to this maximum if tokens are burned. This transparency is crucial for managing expectations regarding tokenomics.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x32b4...f36e`](https://etherscan.io/address/0x32b4d049fe4c888d2b92eecaf729f44df6b1f36e) |
| **Network** | Ethereum |
| **Price** | $0.01821 |
| **24h Volume** | $483.5K |
| **Liquidity** | $584.0K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 405 buys / 221 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x468fb0cd8d52b5b7db6f35f249e87f08ad90f644)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fabric-protocol-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-15*
