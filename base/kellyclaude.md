---
token: KellyClaude
ticker: KELLYCLAUDE
network: base
risk_score: 32
status: medium
date: 2026-08-13
---

# KellyClaude (KELLYCLAUDE) — Smart Contract Security Analysis | Base

> **Risk Score: 32/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kellyclaude-base)

---

## Audit Summary

The ClankerToken contract is an ERC-20 token with extensions for burning, permits, and voting, designed for cross-chain functionality via a Superchain Token Bridge. The contract exhibits a robust foundation using OpenZeppelin standards. Key risks include the centralized control held by the `_admin` address over critical token parameters and the inherent dependency on the security of the external Superchain Token Bridge for supply management. The contract is not upgradeable, which simplifies its security profile but limits future flexibility.

> **Final Recommendation:** It is crucial to implement robust security measures for the `_admin` key, such as using a hardware wallet or a multi-signature wallet, to mitigate the risks associated with centralized control. Thoroughly review and understand the operational implications of the `initialSupplyChainId_` check during deployment to ensure the intended initial token distribution. Additionally, maintain awareness of the security posture of the `Predeploys.SUPERCHAIN_TOKEN_BRIDGE` as the token's supply management is directly dependent on it.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract is built upon well-audited OpenZeppelin ERC-20 standards, including extensions for burning, permits, and voting, which enhances its code security (7.2). The architecture (7.1) clearly… |
| **Governance / Economics** | 5/10 | Medium | The economic model (7.4) relies on a fixed `maxSupply_` for initial minting, contingent on the deployment chain ID, and allows for dynamic supply adjustments via `crosschainMint`/`crosschainBurn` by… |
| **Upgrades** | 9/10 | Low | The ClankerToken contract is implemented as a standard, non-upgradeable contract (7.7). This design choice eliminates the complexities and potential risks associated with upgrade mechanisms (e.g.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control of Admin Role  *(Severity: High · Status: Unresolved)*

The `_admin` address has extensive control over critical contract functions, including the ability to update the token's `_image`, `_metadata`, and, most significantly, to transfer the `_admin` role to any other address via `updateAdmin()`. This centralized control (7.3) creates a single point of failure; if the `_admin` key is compromised, an attacker could seize control of these parameters, potentially impacting the token's branding, perceived value, and future operational integrity (7.8).

**Recommendation:** Consider implementing a multi-signature wallet for the `_admin` role to require multiple approvals for sensitive operations like `updateAdmin()`, `updateImage()`, and `updateMetadata()`. Alternatively, introduce a timelock mechanism for admin role transfers to provide a window for community or team intervention in case of a compromised key.


### `M-01` — Dependency on External Superchain Token Bridge  *(Severity: Medium · Status: Unresolved)*

The `crosschainMint` and `crosschainBurn` functions, which directly affect the token's total supply, are exclusively callable by `Predeploys.SUPERCHAIN_TOKEN_BRIDGE`. This design (7.6) makes the token's supply management entirely dependent on the security and correct functioning of this external bridge. Any vulnerability or compromise within the Superchain Token Bridge could lead to unauthorized minting or burning of ClankerTokens, directly impacting the token's economic stability (7.4).

**Recommendation:** Ensure a thorough understanding and ongoing monitoring of the security posture of the `Predeploys.SUPERCHAIN_TOKEN_BRIDGE`. While direct control over the bridge's security may be limited, awareness of its audit status, operational procedures, and any reported vulnerabilities is crucial for assessing the overall risk to ClankerToken.


### `M-02` — Admin Control Over Token Metadata and Image  *(Severity: Medium · Status: Unresolved)*

The `_admin` address has the authority to unilaterally change the token's `_metadata` and `_image` strings via `updateMetadata()` and `updateImage()` functions. While these are typically off-chain representations, malicious or accidental changes to these publicly visible attributes could negatively impact user perception, trust, and the token's branding (7.4). This centralized control (7.3) over mutable data could be exploited to misrepresent the token.

**Recommendation:** Consider whether these metadata fields truly require mutable control by a single admin. If mutability is necessary, implement a timelock for changes or a multi-signature approval process to add a layer of security and transparency before updates are finalized. Clearly communicate the implications of these mutable fields to token holders.


### `L-01` — Conditional Initial Supply Minting Logic  *(Severity: Low · Status: Unresolved)*

The constructor's initial minting of `maxSupply_` to `msg.sender` is conditional on `block.chainid == initialSupplyChainId_`. If the contract is deployed on a chain where this condition is false, the `msg.sender` (deployer) will receive zero tokens, potentially leading to an unexpected empty initial supply for the deployer (7.8). While this might be an intentional design for multi-chain deployment strategies, it introduces a subtle point of failure if the `initialSupplyChainId_` is misconfigured or misunderstood during deployment (7.1).

**Recommendation:** Ensure that the `initialSupplyChainId_` parameter is carefully chosen and verified during deployment to match the intended chain for initial supply distribution. Document this behavior clearly to prevent deployment errors or misunderstandings regarding the initial token allocation.


### `I-01` — Lack of Upgradeability  *(Severity: Informational · Status: Unresolved)*

The ClankerToken contract is deployed as a standard, non-upgradeable contract. This means there is no built-in mechanism (e.g., proxy pattern) to modify the contract's logic after deployment (7.7). While this simplifies the contract's architecture and removes upgrade-related risks, it also implies that any future bug fixes, feature enhancements, or changes to the token's core functionality would require a complete redeployment of the contract and a potentially complex migration of existing token holders and associated liquidity.

**Recommendation:** Acknowledge the implications of non-upgradeability. For a token contract, this is often a desired security feature, as it guarantees immutability of core logic. If future flexibility is ever considered critical, a new contract would need to be deployed. Ensure all current functionality is thoroughly tested and deemed final.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x50d2...cb07`](https://basescan.org/address/0x50d2280441372486beecdd328c1854743ebacb07) |
| **Network** | Base |
| **Price** | $0.00000845 |
| **24h Volume** | $67.3K |
| **Liquidity** | $793.0K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 52.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 211 buys / 462 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x7eac33d5641697366eaec3234147fd98ba25f01acca66a51a48bd129fc532145)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kellyclaude-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-13*
