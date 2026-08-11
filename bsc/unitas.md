---
token: Unitas
ticker: UP
network: bsc
risk_score: 52
status: high
date: 2026-08-11
---

# Unitas (UP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 52/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/unitas-bsc)

---

## Audit Summary

The UnitasOFT contract is an Omnichain Fungible Token (OFT) built on LayerZero v2, inheriting from LayerZero's OFT and OpenZeppelin's Ownable contracts. It serves as a standard ERC-20 token with cross-chain capabilities. The contract itself contains minimal custom logic, primarily acting as a wrapper for the underlying LayerZero OFT implementation. The primary risks identified are related to the inherent centralization of control by the owner multisig over LayerZero configurations and the reliance on the security and operational integrity of the LayerZero protocol.

> **Final Recommendation:** It is recommended to thoroughly review and secure the operational procedures for the owner multisig, ensuring robust key management and a transparent decision-making process for all LayerZero configurations. Implement comprehensive monitoring for LayerZero endpoint and relayer activity to detect anomalies. Additionally, consider establishing an emergency response plan for potential LayerZero protocol-level issues or misconfigurations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract `UnitasOFT` is well-structured, inheriting from battle-tested OpenZeppelin `Ownable` and LayerZero `OFT` libraries (7.1 Architecture). It introduces no custom complex logic, reducing the… |
| **Governance / Economics** | 2/10 | High | The contract utilizes an `Ownable` pattern, with a 3/5 multisig (`0x0958d8ab8bd86ce7451156dff0783152bea21514`) acting as the owner (7.3 Access Control). This multisig holds significant administrative… |
| **Upgrades** | 7/10 | Low | The `UnitasOFT` contract is not designed as an upgradeable proxy (7.7 Upgrades). This eliminates risks associated with proxy implementation bugs or upgrade path vulnerabilities. However, it means… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 2 Informational_

### `H-01` — Centralization of Control by Owner Multisig  *(Severity: High · Status: Unresolved)*

The `UnitasOFT` contract inherits `Ownable`, granting a single owner address (a 3/5 multisig) extensive administrative control. This owner can configure critical LayerZero parameters such as `setPeer`, `setSendVersion`, `setReceiveVersion`, `setConfig`, `setPrecrime`, `setOracle`, `setFeeCollector`, and `setTreasury` through the inherited `OFT` and `OApp` functions. Malicious or erroneous actions by the multisig signers could lead to severe consequences, including disabling cross-chain transfers, redirecting fees, or compromising the integrity of the token bridge.

**Recommendation:** Ensure the multisig signers are highly trusted individuals, and that robust internal governance procedures, including strict review and approval processes, are in place for all administrative actions. Consider implementing a timelock for critical operations to provide a window for community review or emergency intervention.


### `H-02` — Reliance on LayerZero Protocol Security  *(Severity: High · Status: Unresolved)*

As an Omnichain Fungible Token (OFT) built on LayerZero v2, the contract's cross-chain functionality is entirely dependent on the security and operational integrity of the LayerZero protocol. This includes the security of LayerZero endpoints, relayers, oracles, and precrime mechanisms. Vulnerabilities or exploits within the LayerZero infrastructure, or issues with external actors (e.g., relayers censoring messages, oracles providing incorrect data), could directly impact the `UnitasOFT` token, potentially leading to loss of funds, frozen assets, or incorrect state synchronization across chains.

**Recommendation:** While direct mitigation within the `UnitasOFT` contract is limited, it is crucial to stay updated on LayerZero's security announcements and best practices. Implement robust monitoring for LayerZero-related events and transactions. Consider diversifying cross-chain solutions or implementing circuit breakers if the protocol's design allows for such measures in case of a LayerZero-wide incident.


### `M-01` — Risk of Owner Misconfiguration  *(Severity: Medium · Status: Unresolved)*

The owner multisig has the ability to configure various LayerZero parameters. Incorrectly setting these parameters, such as an invalid `peer` address, an unsupported `sendVersion` or `receiveVersion`, or an erroneous `config` for a specific `eid`, could lead to cross-chain messages failing, tokens becoming stuck on a particular chain, or unintended behavior. While the owner is a multisig, human error or a lapse in judgment during configuration remains a risk.

**Recommendation:** Implement a rigorous testing and verification process for all LayerZero configuration changes before deployment to production. Utilize a staging environment to simulate changes and ensure they function as expected. Document all configuration parameters and their intended values.


### `I-01` — Non-Upgradeable Contract  *(Severity: Informational · Status: Unresolved)*

The `UnitasOFT` contract is deployed as a standard implementation contract and is not designed to be upgradeable via proxy patterns. This means that once deployed, its logic cannot be modified. Any future bug fixes, feature enhancements, or protocol changes would necessitate deploying an entirely new contract and migrating existing token holders, which can be a complex and costly process.

**Recommendation:** Acknowledge the implications of a non-upgradeable contract. For critical infrastructure, consider the long-term implications of immutability versus the flexibility of upgradeability. If future upgrades are anticipated, a proxy pattern might be considered for future iterations.


### `I-02` — Minimal Custom Logic  *(Severity: Informational · Status: Unresolved)*

The `UnitasOFT` contract primarily acts as a wrapper, inheriting functionality from `OFT` and `Ownable` without introducing significant custom logic or state variables beyond the constructor. While this reduces the attack surface for new vulnerabilities within `UnitasOFT` itself, it means that the security profile is largely determined by the underlying LayerZero and OpenZeppelin libraries.

**Recommendation:** Continue to rely on well-audited and maintained external libraries. Ensure that any future custom logic introduced into similar contracts undergoes thorough security review.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0000...0000`](https://bscscan.com/address/0x000008d2175f9aeaddb2430c26f8a6f73c5a0000) |
| **Network** | BNB Chain |
| **Price** | $0.3782 |
| **24h Volume** | $246.0K |
| **Liquidity** | $1.24M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 97.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1568 buys / 1609 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x6f8cb5850cb131c9027e68399118e035ba1d2182)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/unitas-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
