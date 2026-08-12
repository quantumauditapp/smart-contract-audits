---
token: Bubblemaps
ticker: BMT
network: bsc
risk_score: 51
status: high
date: 2026-08-12
---

# Bubblemaps (BMT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 51/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bubblemaps-bsc)

---

## Audit Summary

The MyOFT contract is an Omnichain Fungible Token (OFT) implementation built on LayerZero v2 and OpenZeppelin's Ownable standard. The contract itself is minimal, primarily inheriting functionality from well-audited external libraries. Key risks identified relate to the inherent centralization of administrative control, the critical dependency on the LayerZero protocol's security, and the potential for misconfiguration of cross-chain parameters by the owner. The owner is a multisig, which significantly mitigates single-point-of-failure risks.

> **Final Recommendation:** Ensure the `_delegate` address, which serves as the contract owner, is a highly secure and well-managed multisig wallet with robust operational procedures. Implement comprehensive monitoring for LayerZero protocol health and transaction statuses to quickly identify and respond to any cross-chain issues. Thoroughly review and test all LayerZero configuration changes before deployment to production to prevent misconfigurations that could impact user funds or transaction costs.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract (7.1 Architecture) is a straightforward implementation of LayerZero's OFT standard, inheriting from battle-tested OpenZeppelin and LayerZero libraries. This minimizes direct code… |
| **Governance / Economics** | 3/10 | High | The contract utilizes OpenZeppelin's Ownable pattern, granting significant administrative control to a single owner address (7.3 Access Control). This owner, designated as the `_delegate` in the… |
| **Upgrades** | 7/10 | Low | The MyOFT contract is not designed as an upgradeable proxy (7.7 Upgrades). It is a standard implementation contract, meaning its logic is immutable once deployed. This simplifies the upgrade safety… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low_

### `M-01` — Centralized Control by Owner/Delegate  *(Severity: Medium · Status: Unresolved)*

The MyOFT contract inherits from OpenZeppelin's Ownable, granting the designated `_delegate` address (which is the owner) significant administrative control. This owner can configure various LayerZero parameters, including setting send/receive libraries, minimum destination gas, and LayerZero token addresses. While the provided information indicates the owner is a multisig, this still represents a centralized point of control over critical cross-chain functionality.

**Recommendation:** Ensure the owner address is a robustly secured and actively managed multisig wallet. Implement strict internal governance procedures for any administrative actions, especially those involving LayerZero configuration changes. Consider implementing time-locks for critical parameter changes to allow for community review or emergency intervention.


### `M-02` — Critical Dependency on LayerZero Protocol Security  *(Severity: Medium · Status: Unresolved)*

The MyOFT contract's core functionality, specifically cross-chain token transfers, is entirely dependent on the security and correct operation of the external LayerZero v2 protocol and its endpoint. Any vulnerabilities, exploits, or operational failures within the LayerZero protocol itself could directly impact the OFT, potentially leading to frozen assets, loss of funds, or disruption of cross-chain services.

**Recommendation:** Acknowledge and monitor the inherent risks associated with relying on an external cross-chain messaging protocol. Stay informed about LayerZero security updates, audits, and any reported vulnerabilities. Implement robust monitoring for LayerZero endpoint health and cross-chain transaction finality.


### `M-03` — Potential for Misconfiguration of LayerZero Parameters  *(Severity: Medium · Status: Unresolved)*

The owner/delegate has the ability to set various LayerZero-specific parameters, such as `minDstGas`, `lzToken`, `sendLibrary`, and `receiveLibrary`. Incorrect or malicious configuration of these parameters could lead to several issues, including failed cross-chain transactions, unexpected or excessive transaction fees for users, or even the inability to transfer tokens across certain chains, effectively halting the OFT's primary function.

**Recommendation:** Establish a rigorous process for reviewing and testing all LayerZero parameter changes. Implement a 'dry run' or staging environment to validate configurations before applying them to the mainnet contract. Provide clear documentation and guidelines for the multisig signers regarding the implications of each configurable parameter.


### `L-01` — Lack of Direct Emergency Pause Mechanism  *(Severity: Low · Status: Unresolved)*

The MyOFT contract does not implement a direct, contract-specific emergency pause mechanism. While the underlying LayerZero protocol may have its own emergency controls, a dedicated pause function within the OFT contract could provide an additional layer of defense, allowing the owner to temporarily halt cross-chain transfers in response to a critical vulnerability or exploit specific to the OFT or its immediate environment.

**Recommendation:** Consider adding a `Pausable` mechanism (e.g., from OpenZeppelin) to the MyOFT contract. This would allow the owner to pause and unpause cross-chain operations in emergency situations, providing a circuit breaker for unforeseen events. Ensure that any pause mechanism is carefully designed to avoid creating new attack vectors or centralizing too much power.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7d81...1b62`](https://bscscan.com/address/0x7d814b9ed370ec0a502edc3267393bf62d891b62) |
| **Network** | BNB Chain |
| **Price** | $0.01753 |
| **24h Volume** | $236.1K |
| **Liquidity** | $328.5K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 91.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1165 buys / 1460 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x09f9789cf2dba13e6e1ce8cfdcd3f751d2917fc5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bubblemaps-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-12*
