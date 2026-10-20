---
token: Alchemix
ticker: ALCX
network: ethereum
risk_score: 49
status: medium
date: 2026-09-23
---

# Alchemix (ALCX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/alchemix-eth)

---

## Audit Summary

The AlchemixToken contract implements a standard ERC20 token with OpenZeppelin's AccessControl for role-based management. The primary functionality includes a minting mechanism controlled by a MINTER_ROLE, which is administered by an ADMIN_ROLE. While the technical implementation is robust, the centralized control over token minting presents a significant economic risk.

> **Final Recommendation:** It is crucial to implement stringent operational security measures for the address holding the `ADMIN_ROLE`, as it controls the token's minting capabilities. Consider multi-signature wallets or time-locks for critical administrative actions to mitigate the risk of a single point of failure. For future iterations, explore options for decentralizing or capping the minting authority if the project's long-term vision includes reduced centralization.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The AlchemixToken contract leverages battle-tested OpenZeppelin libraries for its ERC20 and AccessControl implementations, ensuring a solid technical foundation (7.2 Code Security). Arithmetic… |
| **Governance / Economics** | 1/10 | High | The contract design centralizes significant power in the `ADMIN_ROLE` and `MINTER_ROLE` (7.5 Governance). The `MINTER_ROLE` has the ability to mint an unlimited supply of tokens, which is a… |
| **Upgrades** | 3/10 | High | The AlchemixToken contract is not designed as an upgradeable proxy (7.7 Upgrades). This simplifies the architecture by avoiding upgrade-related complexities and risks, but also means that any future… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 92.1% |
| **Top-3 Unlocked** | ⚠️ 94.8% |

## Security Findings

_🟠 1 High · ⚪ 2 Informational_

### `H-01` — Centralized Control of Token Minting  *(Severity: High · Status: Unresolved)*

The `AlchemixToken` contract implements a `mint` function that allows an address with the `MINTER_ROLE` to create an arbitrary amount of new tokens. The `ADMIN_ROLE` has the authority to grant and revoke the `MINTER_ROLE`. Initially, the contract deployer holds both `ADMIN_ROLE` and `MINTER_ROLE`. This design centralizes significant control over the token supply. If the private key associated with the `ADMIN_ROLE` is compromised, or if the entity holding it acts maliciously, the token supply can be arbitrarily inflated, leading to a severe devaluation for all existing token holders. This represents a single point of failure for the token's economic stability (7.4 Economic, 7.5 Governance).

**Recommendation:** Implement robust operational security for the `ADMIN_ROLE` address, such as using a multi-signature wallet (e.g., Gnosis Safe) or a time-lock contract for critical actions like granting/revoking `MINTER_ROLE`. Consider introducing a maximum minting cap per period or a total supply cap to limit potential inflation. Explore mechanisms for progressive decentralization of the `MINTER_ROLE` or its administration over time, if aligned with the project's roadmap.


### `I-01` — Redundant Imports  *(Severity: Informational · Status: Unresolved)*

The `AlchemixToken` contract imports `Ownable` and `IDetailedERC20` but does not utilize any functionality or interfaces from these imported contracts. The contract uses `AccessControl` for role management, making `Ownable` redundant. `IDetailedERC20` is also not implemented or referenced (7.1 Architecture).

**Recommendation:** Remove unused imports (`import {Ownable} from "@openzeppelin/contracts/access/Ownable.sol";` and `import {IDetailedERC20} from "./interfaces/IDetailedERC20.sol";`) to improve code clarity and reduce compilation overhead.


### `I-02` — Outdated Pragma Directive for ABIEncoderV2  *(Severity: Informational · Status: Unresolved)*

The contract includes `pragma experimental ABIEncoderV2;`. While this pragma was necessary for Solidity versions 0.6.x and 0.7.x to enable the ABIEncoderV2, it became standard in Solidity 0.8.0 and is no longer required. Although not a vulnerability, its presence indicates the use of an older compiler feature flag (7.2 Code Security).

**Recommendation:** If the project intends to upgrade to Solidity 0.8.0 or newer, this pragma can be safely removed. For the current compiler version (0.6.12), it is technically still relevant, but it's worth noting for future upgrades.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdbdb...c8df`](https://etherscan.io/address/0xdbdb4d16eda451d0503b854cf79d55697f90c8df) |
| **Network** | Ethereum |
| **Price** | $3.2800 |
| **24h Volume** | $1.14M |
| **Liquidity** | $857.8K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 5y |
| **Top-10 Holders** | 61.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 716 buys / 794 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc3f279090a47e80990fe3a9c30d24cb117ef91a8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/alchemix-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*
