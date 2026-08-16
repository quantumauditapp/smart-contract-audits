---
token: Dolomite
ticker: DOLO
network: ethereum
risk_score: 42
status: medium
date: 2026-08-16
---

# Dolomite (DOLO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dolomite-eth)

---

## Audit Summary

The DOLOWithOwnable contract is an ERC20Burnable token with an Ownable access control pattern. It includes a centralized minting mechanism controlled by the contract owner, who can designate minter addresses. The contract leverages OpenZeppelin libraries for standard token functionality and access control, along with a custom 'Require' library for assertions. While code quality is generally good, the significant power vested in the owner, particularly regarding token minting, introduces a high economic risk.

> **Final Recommendation:** It is crucial to implement robust operational security measures for the owner's multisig and any designated minter contracts, given the significant power over token supply. Consider introducing mechanisms to limit the minting capability, such as a maximum total supply, a per-period minting cap, or a timelock for minting operations, to mitigate the economic risks associated with centralized minting. Thoroughly audit any external contracts designated as minters or CCIP admins.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good code security practices (7.2) by inheriting from battle-tested OpenZeppelin ERC20, ERC20Burnable, and Ownable contracts. It uses Solidity 0.8.9+, mitigating common… |
| **Governance / Economics** | 2/10 | High | The economic model (7.4) of the DOLO token is highly centralized, with the contract owner having the ability to grant unlimited minting power to designated minters. This introduces a significant… |
| **Upgrades** | 7/10 | Low | The DOLOWithOwnable contract is not designed with an upgrade mechanism (7.7), meaning its logic is immutable once deployed. This simplifies the architecture and removes upgrade-related risks such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 3 Informational_

### `H-01` — Centralized Unlimited Minting Capability  *(Severity: High · Status: Unresolved)*

The `DOLOWithOwnable` contract grants the owner the ability to set and unset minters, and these minters can call the `mint` function to create an arbitrary amount of new tokens. This centralized control over token supply introduces a significant economic risk, as a compromised owner key or a malicious minter could lead to unlimited inflation, devaluing existing tokens.

**Recommendation:** Implement safeguards to limit the minting capability. This could include a hard cap on the total supply, a maximum mintable amount per period, or requiring a multi-signature approval or a timelock for minting operations. If unlimited minting is a core design choice, ensure the operational security of the owner and minter addresses is exceptionally high.


### `I-01` — `renounceOwnership` Function Reverted  *(Severity: Informational · Status: Unresolved)*

The `renounceOwnership` function is explicitly overridden to revert, preventing the owner from ever relinquishing ownership. This design choice ensures that the contract will always have an owner with the associated administrative privileges, including control over minting and setting the CCIP admin.

**Recommendation:** Acknowledge this design choice. If future decentralization or transfer of ownership to a DAO is desired, this design would require a new contract deployment. Ensure the implications of permanent ownership are well understood and documented.


### `I-02` — Minter Must Be a Contract  *(Severity: Informational · Status: Unresolved)*

The `_ownerSetMinter` function includes a `Require.that(_minter.isContract(), ...)` check, enforcing that only smart contract addresses can be designated as minters. This prevents Externally Owned Accounts (EOAs) from directly holding minting privileges.

**Recommendation:** Document the rationale behind this design choice. Ensure that any contract designated as a minter is thoroughly audited and secured, as its compromise would directly impact the token's supply. This design can be beneficial for integrating with governance or timelock contracts.


### `I-03` — Undefined `_ccipAdmin` Role Functionality  *(Severity: Informational · Status: Unresolved)*

The contract defines a `_ccipAdmin` state variable and functions (`ownerSetCCIPAdmin`, `getCCIPAdmin`) to manage it. However, the provided contract code does not implement any logic that utilizes this `_ccipAdmin` role. This suggests that its functionality is intended for external integration or future development.

**Recommendation:** Clearly document the intended purpose and responsibilities of the `_ccipAdmin` role. If this role interacts with external systems or contracts, ensure those integrations are secure and that the `_ccipAdmin` address is managed with the highest security standards.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0f81...a654`](https://etherscan.io/address/0x0f81001ef0a83ecce5ccebf63eb302c70a39a654) |
| **Network** | Ethereum |
| **Price** | $0.02483 |
| **24h Volume** | $169.9K |
| **Liquidity** | $176.9K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 77.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 583 buys / 420 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x003896387666c5c11458eeb3f927b72a11b19783)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dolomite-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-16*
