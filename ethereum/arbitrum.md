---
token: Arbitrum
ticker: ARB
network: ethereum
risk_score: 31
status: low
date: 2026-09-01
---

# Arbitrum (ARB) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 31/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/arbitrum-eth)

---

## Audit Summary

The L1ArbitrumToken contract serves as the L1 representation of the Arbitrum token, utilizing OpenZeppelin's upgradeable ERC20 standard and integrating with Arbitrum bridge components. The audit identified a critical dependency on the security and integrity of external bridge contracts for token minting, burning, and L2 registration. While the contract adheres to good coding practices and uses a secure upgradeability pattern, the significant trust assumptions on external systems elevate the overall risk. Minor issues related to public function access and design limitations were also noted.

> **Final Recommendation:** It is recommended to conduct a thorough audit of the `arbOneGateway`, `novaGateway`, and `novaRouter` contracts, as their security directly impacts the `L1ArbitrumToken`'s integrity and token supply. Implement robust monitoring for these external bridge components to detect any unauthorized activity. Consider restricting access to the `registerTokenOnL2` function to a trusted entity or a multisig to prevent potential griefing or suboptimal L2 registrations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The L1ArbitrumToken contract is an upgradeable ERC20 token leveraging OpenZeppelin's `ERC20Upgradeable` and `ERC20PermitUpgradeable` for robust token functionality and standard upgradeability. It… |
| **Governance / Economics** | 1/10 | High | The economic model of the `L1ArbitrumToken` is primarily driven by its minting and burning mechanisms, which are exclusively controlled by the `arbOneGateway` contract (7.4). This centralizes control… |
| **Upgrades** | 2/10 | High | The contract utilizes the Transparent Upgradeable Proxy pattern with OpenZeppelin's `Initializable` base, ensuring a secure and well-understood upgrade mechanism (7.7). The constructor correctly… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → RoleGatedExecutor |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 98.8% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Public `registerTokenOnL2` Allows Arbitrary Registrations  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `registerTokenOnL2` function is public and payable, allowing any external address to call it and initiate a token registration on L2. While this does not directly affect the L1 token balance, a malicious actor could repeatedly call this function with arbitrary or suboptimal `RegistrationParams`, incurring gas costs for the transaction and potentially registering the token with undesirable parameters on L2. This could lead to griefing attacks or inefficient L2 setups, consuming network resources and potentially causing confusion (7.3 Access Control, 7.4 Economic).

**Recommendation:** Consider restricting access to the `registerTokenOnL2` function to a trusted entity, such as a governance contract or a multisig wallet. This would prevent arbitrary calls and ensure that L2 registrations are performed only by authorized parties with carefully chosen parameters.


### `M-02` — Critical Trust Assumptions on External Bridge Contracts  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `L1ArbitrumToken` contract's core functionality, including `bridgeMint` and `bridgeBurn`, is entirely dependent on the `arbOneGateway` contract. Similarly, `registerTokenOnL2` relies on `novaGateway` and `novaRouter`. These external contracts are critical for the token's supply control and L2 integration. A compromise or malfunction of any of these trusted external bridge components would directly lead to unauthorized minting, burning, or manipulation of the token's L2 registration, severely impacting the token's integrity and value (7.6 External).

**Recommendation:** Ensure that the `arbOneGateway`, `novaGateway`, and `novaRouter` contracts are rigorously audited, highly secure, and managed with robust access controls (e.g., multisig, time-locks). Implement continuous monitoring for any suspicious activity originating from or targeting these addresses. Consider a multi-layered security approach for these critical components.


### `L-01` — `isArbitrumEnabled` Function Design Limitation  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `isArbitrumEnabled` function includes a `require(shouldRegisterGateway, "L1ArbitrumToken: not expecting gateway registration");` statement. Since `shouldRegisterGateway` is a private variable that is only temporarily set to `true` within the `registerTokenOnL2` function, `isArbitrumEnabled` will almost always revert when called externally. This design makes the `external view` function effectively unusable as a public informational query, which might be counter-intuitive for integrators or users expecting to check the token's Arbitrum enablement status (7.1 Architecture, 7.2 Code Security).

**Recommendation:** If `isArbitrumEnabled` is intended to be a publicly queryable status, consider removing the `shouldRegisterGateway` check or modifying the logic to reflect a persistent state. If its current behavior is intentional for internal bridge logic, consider making it `internal` or adding comments to clarify its specific use case and limitations.


### `I-01` — External Call in `transferAndCall` Function  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `transferAndCall` function performs an external call to the `onTokenTransfer` function of the recipient contract if the recipient is a contract. While the token transfer (`super.transfer`) occurs before the external call, adhering to the Checks-Effects-Interactions pattern, any external call introduces a potential reentrancy vector for other functions within the `L1ArbitrumToken` contract or other interacting protocols. This is a standard pattern for `transferAndCall` functionality (7.2 Code Security, 7.6 External).

**Recommendation:** No direct vulnerability is identified, as the pattern is correctly implemented. However, it is crucial for any contract interacting with `L1ArbitrumToken` via `transferAndCall` to be aware of this external call and ensure its own functions are reentrancy-safe, especially if they rely on the `L1ArbitrumToken`'s state after the transfer.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb507...4ad1`](https://etherscan.io/address/0xb50721bcf8d664c30412cfbc6cf7a15145234ad1) |
| **Network** | Ethereum |
| **Price** | $0.1346 |
| **24h Volume** | $64.5K |
| **Liquidity** | $32.7K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 3y |
| **Top-10 Holders** | 61.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 295 buys / 241 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x59354356ec5d56306791873f567d61ebf11dfbd5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/arbitrum-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*
