---
token: Recall
ticker: RECALL
network: base
risk_score: 74
status: critical
date: 2026-07-26
---

# Recall (RECALL) — Smart Contract Security Analysis | Base

> **Risk Score: 74/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/recall-base)

---

## Audit Summary

The Recall token contract is an upgradeable ERC20 token leveraging OpenZeppelin's battle-tested libraries for access control, pausability, and UUPS proxy functionality. It also integrates with the Axelar Interchain Token Standard. While the code quality is high and standard patterns are followed, the initial configuration assigns all critical administrative, minting, and pausing roles to a single deployer address. This centralization introduces significant single points of failure, elevating the overall risk level.

> **Final Recommendation:** To enhance the security posture of the Recall token contract, it is strongly recommended to decentralize control over critical administrative roles. Transfer the `ADMIN_ROLE`, `MINTER_ROLE`, and `PAUSER_ROLE` from the initial deployer EOA to a robust multi-signature wallet or a decentralized autonomous organization (DAO) governance mechanism. This will mitigate the significant single-point-of-failure risks identified in this report and improve the overall resilience against malicious actors or key compromise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates strong technical foundations (7.1 Architecture, 7.2 Code Security). It utilizes OpenZeppelin's upgradeable contracts for ERC20, AccessControl, Pausable, and UUPS, ensuring… |
| **Governance / Economics** | 1/10 | High | The contract implements robust access control via OpenZeppelin's `AccessControlUpgradeable` (7.3 Access Control). However, all critical roles (ADMIN_ROLE, MINTER_ROLE, PAUSER_ROLE) are initially… |
| **Upgrades** | 1/10 | High | The contract correctly implements the UUPSUpgradeable proxy pattern (7.7 Upgrades), which is a secure and widely adopted standard for upgradeability. The `_authorizeUpgrade` function is appropriately… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 54.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control of Critical Roles  *(Severity: High · Status: Unresolved)*

The `initialize` function assigns the `ADMIN_ROLE`, `MINTER_ROLE`, and `PAUSER_ROLE` to the `msg.sender` (deployer EOA). The `ADMIN_ROLE` has the ability to manage all other roles, unpause the contract, and authorize contract upgrades. This creates a single point of failure where a compromise of the deployer's EOA could lead to complete control over the token's functionality, including arbitrary minting, halting operations, and deploying malicious contract logic (7.3 Access Control, 7.5 Governance, 7.8 Operations).

**Recommendation:** Transfer the `ADMIN_ROLE`, `MINTER_ROLE`, and `PAUSER_ROLE` to a multi-signature wallet or a robust DAO governance contract immediately after deployment and initialization. This distributes control and significantly reduces the risk associated with a single compromised private key.


### `M-01` — Pausability as a Centralized Denial-of-Service Vector  *(Severity: Medium · Status: Unresolved)*

The `PAUSER_ROLE` has the ability to call `pause()`, which halts all token transfers, minting, and burning operations. While the `ADMIN_ROLE` can `unpause()`, the unilateral ability of a single `PAUSER_ROLE` holder to stop all token activity presents a significant centralization risk and potential for denial of service (7.3 Access Control, 7.4 Economic). A malicious or compromised `PAUSER_ROLE` could disrupt the protocol's operations.

**Recommendation:** Consider implementing a timelock for the `pause()` function or requiring multiple parties (e.g., a multi-signature wallet) to approve pausing. Alternatively, restrict the `PAUSER_ROLE` to a trusted, highly secure entity or a governance mechanism with appropriate checks and balances.


### `M-02` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The `MINTER_ROLE` has the authority to mint an arbitrary amount of new tokens to any address. If the `MINTER_ROLE` is controlled by a single EOA and that EOA is compromised, an attacker could mint an unlimited supply of tokens, leading to hyperinflation and severe devaluation of existing tokens (7.4 Economic). This centralized control over token supply poses a significant economic risk.

**Recommendation:** Implement a minting cap, rate limit, or transfer the `MINTER_ROLE` to a multi-signature wallet or a controlled contract that enforces specific minting policies. This would introduce checks and balances to prevent uncontrolled token issuance.


### `L-01` — Reliance on External Axelar Interchain Token Service  *(Severity: Low · Status: Unresolved)*

The contract integrates with the Axelar Interchain Token Standard and relies on the `_interchainTokenService` address for interchain functionality, specifically for deriving the `interchainTokenId`. The security and availability of this external service are critical to the token's cross-chain operations (7.6 External). Any vulnerabilities or disruptions in the Axelar service could indirectly impact the token's intended functionality.

**Recommendation:** Acknowledge and continuously monitor the security and operational status of the Axelar Interchain Token Service. While this is an inherent dependency and not a direct vulnerability in the Recall contract's logic, understanding and managing this external risk is crucial.


### `I-01` — Fixed Deployer Address for Interchain Token ID Derivation  *(Severity: Informational · Status: Unresolved)*

The `deployer` address is set once during `initialize` to `msg.sender` and is subsequently used in the `interchainTokenId()` function to derive the unique token identifier via the Axelar Interchain Token Service. This means the `deployer` address is a permanently fixed component in the token's interchain identity (7.1 Architecture).

**Recommendation:** No direct security recommendation. This is an architectural design choice for Axelar integration. Ensure that the `deployer` address used during initialization is a stable and known entity, as its identity is permanently linked to the token's interchain ID.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1f16...0671`](https://basescan.org/address/0x1f16e03c1a5908818f47f6ee7bb16690b40d0671) |
| **Network** | Base |
| **Price** | $0.03907 |
| **24h Volume** | $130.8K |
| **Liquidity** | $480.4K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 61.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 629 buys / 848 sells |

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

## Frequently Asked Questions

### Is Recall a scam?

Based on automated analysis, Recall scores 64/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is Recall safe to buy?

Our scanner flagged a risk score of 64/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has Recall been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x0abe41c8aaa9282429e06ebed48be36298981d94)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/recall-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-26*
