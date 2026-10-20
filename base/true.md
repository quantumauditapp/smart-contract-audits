---
token: True
ticker: TRUE
network: base
risk_score: 60
status: medium
date: 2026-09-23
---

# True (TRUE) — Smart Contract Security Analysis | Base

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/true-base)

---

## Audit Summary

The TrueToken contract implements an ERC-20 token with voting capabilities, incorporating OpenZeppelin's AccessControl and Ownable patterns. While leveraging well-audited libraries, the contract exhibits a high degree of centralization in minting and delegation functions, primarily controlled by the contract owner. The use of both Ownable and AccessControl introduces potential complexity. The `maxSupply` can be modified by a designated TIMELOCK_ROLE, which is a positive separation of concerns, but the owner retains significant power over token supply and governance participation.

> **Final Recommendation:** It is strongly recommended to transfer the `owner` role and the `DEFAULT_ADMIN_ROLE` to a robust multi-signature wallet or a well-configured Timelock contract immediately after deployment to mitigate the risks of centralized control. Review the `delegateByOwner` function's intent and consider if its current implementation aligns with the desired decentralized governance model. Implement a pause mechanism to provide emergency control in unforeseen circumstances.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract is built upon battle-tested OpenZeppelin libraries (ERC-20, ERC20Votes, AccessControl, Ownable), which significantly reduces the risk of common vulnerabilities (7.2 Code Security).… |
| **Governance / Economics** | 4/10 | Medium | The contract's economic model allows the contract owner to mint tokens up to a `maxSupply` (7.4 Economic), which represents a significant centralization of power. While the `maxSupply` itself can… |
| **Upgrades** | 5/10 | Medium | The TrueToken contract is not designed as an upgradeable proxy (7.7 Upgrades). This eliminates risks associated with upgrade mechanisms, such as proxy implementation mismatches or insecure upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Minting Power  *(Severity: High · Status: Unresolved)*

The `mint` function is restricted to `onlyOwner`, allowing a single address to mint new tokens up to the `maxSupply`. If the owner's private key is compromised, or if the owner acts maliciously, they could mint a large number of tokens, devaluing existing tokens and potentially disrupting the protocol's economy. While `maxSupply` can be changed by `TIMELOCK_ROLE`, the owner still retains the power to mint up to the current limit.

**Recommendation:** Transfer the `owner` role to a multi-signature wallet or a Timelock contract with a sufficient delay. Consider implementing a more decentralized minting mechanism, such as a capped minting schedule or a governance-controlled minting function, if the project's long-term vision includes decentralization.


### `M-01` — Redundant Access Control Mechanisms  *(Severity: Medium · Status: Unresolved)*

The contract inherits both `Ownable` and `AccessControl`. While `Ownable` provides a simple `owner` role, `AccessControl` offers a more granular role-based system. The constructor grants `DEFAULT_ADMIN_ROLE` to `msg.sender`, who is also the initial `owner`. This dual access control can lead to confusion regarding responsibilities, potential misconfigurations, or unexpected interactions between the two systems if not managed carefully (7.3 Access Control).

**Recommendation:** Consolidate access control to use a single, robust mechanism (preferably `AccessControl` for its granularity). If both are deemed necessary, clearly document the responsibilities and interactions of each role and ensure that critical functions are protected by the most appropriate and secure mechanism. Ensure the `owner` and `DEFAULT_ADMIN_ROLE` are managed by secure entities (e.g., multi-sig, Timelock).


### `M-02` — Owner's Ability to Force Self-Delegation  *(Severity: Medium · Status: Unresolved)*

The `delegateByOwner(address to)` function, restricted to `onlyOwner`, calls `_delegate(to, to)`. This allows the contract owner to force any address `to` to self-delegate its voting power. While this doesn't allow the owner to directly control `to`'s votes or delegate `to`'s votes to a third party, it gives the owner centralized control over who can be an active voter by forcing self-delegation, potentially influencing governance participation or quorum (7.5 Governance).

**Recommendation:** Review the intended purpose of `delegateByOwner`. If the goal is to allow the owner to delegate *their own* votes, the function should be `_delegate(msg.sender, to)`. If the goal is to enable delegation for others, consider if this centralized control is desirable. For truly decentralized governance, delegation should ideally be initiated by the delegator themselves.


### `L-01` — `maxSupply` Modifiable by a Single Role  *(Severity: Low · Status: Unresolved)*

The `setMaxSupply` function, which controls the maximum possible token supply, is protected by `onlyRole(Roles.TIMELOCK_ROLE)`. While using a `TIMELOCK_ROLE` is a good practice for critical parameters, it still relies on a single role to modify a fundamental economic constraint of the token (7.4 Economic). If the `TIMELOCK_ROLE` is compromised or mismanaged, the token's supply cap could be arbitrarily changed.

**Recommendation:** Ensure the `TIMELOCK_ROLE` is assigned to a highly secure entity, such as a multi-signature wallet with a significant number of signers and a substantial time delay. Consider if a more decentralized governance mechanism (e.g., a DAO vote) should be required to alter `maxSupply` for long-term protocol stability.


### `I-01` — Lack of Pause Mechanism  *(Severity: Informational · Status: Unresolved)*

The contract does not include a pause mechanism (e.g., `Pausable` from OpenZeppelin). In the event of an emergency, such as a critical vulnerability discovery or a major market exploit, the contract owner or administrators would not have the ability to temporarily halt token transfers or other critical operations (7.8 Operations).

**Recommendation:** Consider integrating OpenZeppelin's `Pausable` contract to provide an emergency stop functionality. This mechanism should be controlled by a multi-signature wallet or a Timelock to prevent arbitrary pausing.


### `I-02` — External Dependency on `Roles.sol`  *(Severity: Informational · Status: Unresolved)*

The contract imports `./libraries/Roles.sol` and uses `Roles.TIMELOCK_ROLE`. While this is a common pattern for defining constants, the content of `Roles.sol` was not provided for review. Assuming it defines `bytes32` constants, its absence in the audit scope means its specific implementation details and potential implications could not be fully assessed (7.6 External).

**Recommendation:** Ensure all external dependencies, including simple libraries like `Roles.sol`, are included in the audit scope for a comprehensive review. Verify that `Roles.sol` only contains constant definitions and does not introduce any unexpected logic or vulnerabilities.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x21cf...b7ab`](https://basescan.org/address/0x21cfcfc3d8f98fc728f48341d10ad8283f6eb7ab) |
| **Network** | Base |
| **Price** | $0.146 |
| **24h Volume** | $1.40M |
| **Liquidity** | $755.5K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 60.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1300 buys / 1350 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x1fae246b1b2d0ce47126bbb109850da355352d77)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/true-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*
