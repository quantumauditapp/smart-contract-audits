---
token: OutBurn
ticker: OUTBURN
network: ethereum
risk_score: 40
status: medium
date: 2026-09-02
---

# OutBurn (OUTBURN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/outburn-eth)

---

## Audit Summary

The ClankerToken contract is an ERC20 token implementation leveraging well-audited OpenZeppelin libraries. It includes standard features like burning, permit, and voting, along with custom administrative functions for metadata management and admin role updates. The primary risks identified relate to the centralized control vested in the `_admin` role and the lack of clarity regarding the `_verified` state's impact on contract functionality.

> **Final Recommendation:** It is recommended to implement robust security measures for the `_admin` private key, such as a multi-signature wallet, to mitigate the risks associated with centralized control. For critical administrative actions like `updateAdmin`, consider adding a time-lock mechanism to provide a window for community review or intervention. Additionally, clarify and document the intended purpose and impact of the `_verified` state to ensure transparency and prevent future misinterpretations of its role within the contract's functionality.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good technical practices by inheriting from battle-tested OpenZeppelin ERC20 extensions (ERC20Burnable, ERC20Permit, ERC20Votes), which significantly reduces the risk of… |
| **Governance / Economics** | 3/10 | High | The token's economic model is a standard fixed-supply ERC20, with initial minting occurring only on a specific chain ID, which is a robust design choice (7.4 Economic). The `_originalAdmin` is… |
| **Upgrades** | 8/10 | Low | The ClankerToken contract is implemented as a standard, non-upgradeable contract (7.7 Upgrades). This design choice eliminates the complexities and potential risks associated with proxy upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control of Admin Role  *(Severity: High · Status: Unresolved)*

The `_admin` role has significant power, including the ability to transfer itself via `updateAdmin` and modify token-related metadata (`updateImage`, `updateMetadata`). This creates a single point of failure; if the `_admin` key is compromised or transferred to an untrusted address, it could lead to a complete loss of control over these critical functions, potentially allowing malicious updates to token information or an irreversible transfer of administrative power.

**Recommendation:** Consider implementing a multi-signature wallet for the `_admin` role to require multiple approvals for critical actions. For the `updateAdmin` function specifically, implement a time-lock mechanism (e.g., a timelock controller) to introduce a delay before the new admin address becomes active, allowing for community oversight or emergency intervention.


### `M-01` — Lack of Clarity on `_verified` State Impact  *(Severity: Medium · Status: Unresolved)*

The `verify()` function, callable only once by the `_originalAdmin`, sets the `_verified` boolean flag to `true`. However, the contract logic does not use this `_verified` state to gate or modify any other critical functionality (e.g., transfers, burning, admin actions). Its purpose is unclear from the code, potentially leading to confusion among users or developers regarding its intended role and impact on the token's behavior.

**Recommendation:** Clearly document the intended purpose of the `_verified` state. If it is meant to enable or disable specific features, implement the corresponding conditional logic within the contract. If it is purely an informational flag, explicitly state this in documentation to manage expectations.


### `L-01` — Mutable Metadata and Image URLs  *(Severity: Low · Status: Unresolved)*

The `_admin` role has the ability to update the `_image`, `_metadata`, and `_context` strings via `updateImage` and `updateMetadata` functions. While this provides flexibility for branding and informational updates, it also means that the public-facing information associated with the token can be changed at any time by the `_admin`. This could potentially be used to mislead users if malicious or inaccurate data is set.

**Recommendation:** Ensure clear communication to token holders and the community that these fields are mutable. For projects aiming for higher decentralization, consider integrating these updates into a governance mechanism or adding a time-lock to provide transparency and community review before changes take effect.


### `I-01` — Robust Immutable Admin and Initial Minting Logic  *(Severity: Informational · Status: Resolved)*

The `_originalAdmin` address is declared as `immutable`, ensuring that the address with the one-time `verify()` capability cannot be changed after deployment. Additionally, the initial token minting in the constructor is conditionally executed based on `block.chainid == initialSupplyChainId_`. These design choices enhance security by preventing critical parameters from being altered and ensuring that the initial supply is minted only on the intended blockchain, reducing deployment-related risks.

**Recommendation:** No recommendation; this is a positive security feature.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa5a6...fb07`](https://etherscan.io/address/0xa5a6a5b3ae5603510100a400e2d73fd1309bfb07) |
| **Network** | Ethereum |
| **Price** | $0.00000071 |
| **24h Volume** | $1.9K |
| **Liquidity** | $71.1K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 16h |
| **Top-10 Holders** | 95.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 648 buys / 1296 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xd222813453b49adc7c52368ff320d317f510892e5396695afca5d14aeffd533a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/outburn-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-02*
