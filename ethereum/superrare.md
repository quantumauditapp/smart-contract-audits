---
token: SuperRare
ticker: RARE
network: ethereum
risk_score: 47
status: medium
date: 2026-09-27
---

# SuperRare (RARE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 47/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/superrare-eth)

---

## Audit Summary

The SuperRareToken contract, implemented as an upgradeable ERC-20 token, utilizes OpenZeppelin's `ERC20PresetMinterPauserUpgradeable` and includes EIP-2612 permit functionality. The contract's architecture is generally sound, leveraging established upgradeability patterns. Key strengths include the use of a TransparentUpgradeableProxy with a multisig admin for upgrades, and a correctly implemented EIP-2612 permit function. Identified issues primarily relate to redundant code, use of an older Solidity version, and the inherent centralization of control associated with minter/pauser roles, which is common for such token designs.

> **Final Recommendation:** It is recommended to review the necessity of the `InitializableV2` contract and consider streamlining the initialization logic to reduce redundancy. While the use of Solidity 0.7.3 is functional, planning for an upgrade to a more recent compiler version (e.8.x) would leverage built-in security features and align with current best practices. Most importantly, ensure that the powerful `MINTER_ROLE` and `PAUSER_ROLE` are managed by robust, multi-signature governance mechanisms with clearly defined operational procedures to mitigate the risks associated with centralized control over token supply and transfer functionality.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The technical implementation of the SuperRareToken contract is robust, leveraging battle-tested OpenZeppelin upgradeable contracts (7.2 Code Security). The EIP-2612 permit function is correctly… |
| **Governance / Economics** | 2/10 | High | The contract design grants significant power to accounts holding `DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, and `PAUSER_ROLE` (7.3 Access Control). The `MINTER_ROLE` allows for an increase in total token… |
| **Upgrades** | 1/10 | High | The contract is designed for upgradeability using the TransparentUpgradeableProxy pattern, with the implementation inheriting from OpenZeppelin's `Initializable` contracts (7.7 Upgrades). The `init`… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 4-of-7 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 97.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control over Token Supply and Operations  *(Severity: Medium · Status: Unresolved)*

The `SuperRareToken` contract, by inheriting `ERC20PresetMinterPauserUpgradeable`, grants significant control to specific roles. Accounts with the `MINTER_ROLE` can mint new tokens, potentially increasing the total supply beyond the initial amount. Accounts with the `PAUSER_ROLE` can pause all token transfers, effectively freezing the token. The `DEFAULT_ADMIN_ROLE` has the power to grant and revoke these roles. While the proxy's admin is a multisig, the direct control over token mechanics remains centralized within these roles, posing a risk if compromised or misused.

**Recommendation:** Ensure that the `DEFAULT_ADMIN_ROLE`, `MINTER_ROLE`, and `PAUSER_ROLE` are assigned to trusted, multi-signature wallets or robust governance mechanisms. Clearly document the policies and procedures for exercising these powers, especially regarding minting and pausing, to maintain transparency and accountability. Consider implementing time-locks or additional governance checks for critical operations like minting large quantities or pausing.


### `L-01` — EIP-2612 Permit Front-Running Risk  *(Severity: Low · Status: Unresolved)*

The `permit` function implements EIP-2612, allowing users to approve token transfers off-chain using a signed message. While beneficial for gasless approvals, this introduces a potential front-running risk. If a signed `permit` message is broadcast or leaked before the transaction is mined, a malicious actor could front-run the transaction, submitting their own transaction with the same signed message to approve themselves as the `spender` or to approve a different `spender` for the `owner`'s tokens. The `deadline` parameter offers some mitigation but does not eliminate the risk entirely.

**Recommendation:** Educate users about the risks associated with sharing signed `permit` messages. Advise users to set reasonable `deadline` values and to only sign messages from trusted interfaces. While this is an inherent characteristic of EIP-2612, clear user guidance can help mitigate the practical impact.


### `I-01` — Redundant `InitializableV2` Contract  *(Severity: Informational · Status: Unresolved)*

The `InitializableV2` contract introduces an `isInitialized` flag and associated functions (`initialize`, `_requireIsInitialized`, `_isInitialized`). This functionality is already provided by OpenZeppelin's `Initializable` contract, which `InitializableV2` itself inherits from. While `isInitialized` is private and won't cause storage collisions with OpenZeppelin's `_initialized` variable, its presence is redundant and adds unnecessary complexity to the codebase without apparent additional benefit.

**Recommendation:** Consider removing `InitializableV2` and directly inheriting `Initializable` from OpenZeppelin, ensuring proper initialization calls are made to the base `Initializable` contract. If `InitializableV2` was intended for a specific purpose beyond basic initialization, clarify its role or integrate its unique logic directly into `SuperRareToken` if minimal.


### `I-02` — Use of Older Solidity Version (0.7.3)  *(Severity: Informational · Status: Unresolved)*

The contract is compiled with Solidity version 0.7.3. While functional, newer versions (e.g., 0.8.x) include important security enhancements such as default integer overflow/underflow checks, which reduce the risk of common arithmetic vulnerabilities. Although OpenZeppelin contracts for 0.7.x typically include SafeMath, custom logic might still be susceptible if not carefully handled.

**Recommendation:** Consider upgrading the Solidity compiler version to 0.8.x or higher, along with updating OpenZeppelin dependencies to their corresponding versions. This would leverage built-in safety features and ensure compatibility with the latest best practices. A thorough re-audit would be required after such an upgrade.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xba5b...6350`](https://etherscan.io/address/0xba5bde662c17e2adff1075610382b9b691296350) |
| **Network** | Ethereum |
| **Price** | $0.01976 |
| **24h Volume** | $191.7K |
| **Liquidity** | $117.5K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 1y |
| **Top-10 Holders** | 56.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 787 buys / 706 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xc5e82ff54924a7232a3e91ca252d505f4e4417afa2b6a8507dfb691182cd0b16)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/superrare-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-27*
