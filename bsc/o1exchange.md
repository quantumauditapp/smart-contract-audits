---
token: o1.exchange
ticker: O
network: bsc
risk_score: 39
status: medium
date: 2026-08-20
---

# o1.exchange (O) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 39/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/o1exchange-bsc)

---

## Audit Summary

The audit reviewed the `MyOFT` and `MyOFTAdapter` contracts, which implement LayerZero's Omnichain Fungible Token (OFT) and OFT Adapter functionalities. The contracts leverage battle-tested OpenZeppelin and LayerZero libraries. Key findings highlight the inherent centralization risks associated with owner privileges and the critical dependency on LayerZero's underlying infrastructure. No critical or high-severity technical vulnerabilities were identified.

> **Final Recommendation:** It is crucial to ensure the multisig controlling the owner address is secured with robust operational procedures, including stringent key management and transaction signing policies. Regularly review the necessity and scope of the `bridgingEnabled` flag and `whitelist` to ensure they align with the project's evolving operational requirements and risk tolerance. Maintain continuous vigilance regarding LayerZero protocol updates and security advisories, as the system's security is inherently tied to its underlying infrastructure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture (7.1) is robust, utilizing standard inheritance from OpenZeppelin and LayerZero libraries for core functionalities. Code security (7.2) is enhanced by Solidity 0.8.x's… |
| **Governance / Economics** | 3/10 | High | The contracts exhibit a medium level of governance and economic risk (7.4, 7.5) primarily due to the centralized control held by the `owner` address. The owner possesses significant privileges… |
| **Upgrades** | 7/10 | Low | These contracts are not designed as upgradeable proxies (7.7) and do not implement any upgrade mechanisms. Therefore, there are no specific upgrade safety concerns for these particular deployments.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 42.1% |
| **Top-3 Unlocked** | 65.3% |

## Security Findings

_🟡 1 Medium · ⚪ 2 Informational_

### `M-01` — Centralization Risk due to Owner Privileges  *(Severity: Medium · Status: Unresolved)*

The `owner` of the `MyOFTAdapter` contract holds significant centralized control over critical functionalities. The owner can enable or disable bridging for all users via `setBridgingEnabled`, manage a whitelist of addresses that can bypass bridging restrictions using `setWhitelist`, and recover any ERC20 tokens sent to the contract via the `sweep` function. While the provided context indicates the owner is a multisig, these extensive privileges still represent a single point of control that could lead to censorship, denial of service, or fund manipulation if the multisig is compromised or acts maliciously.

**Recommendation:** Ensure the multisig controlling the owner address is highly secure with strong operational procedures, including robust key management, quorum requirements, and clear policies for transaction execution. Consider implementing time-locks or additional governance mechanisms for highly sensitive functions if further decentralization is desired in the future.


### `I-01` — Dependency on LayerZero Protocol Security  *(Severity: Informational · Status: Unresolved)*

The `MyOFT` and `MyOFTAdapter` contracts are built upon and heavily rely on the LayerZero protocol for their omnichain functionality. This includes interactions with LayerZero endpoints and the underlying messaging infrastructure. The security and operational integrity of these contracts are therefore directly dependent on the security of the LayerZero protocol itself (7.6 External). Any vulnerabilities, compromises, or operational issues within the LayerZero ecosystem could directly impact the functionality and security of these deployed contracts.

**Recommendation:** Maintain continuous monitoring of LayerZero's security posture, official announcements, and any reported vulnerabilities. Ensure that the LayerZero endpoint addresses configured in the contracts are correct and trusted. Implement robust monitoring for cross-chain transactions and LayerZero's operational status.


### `I-02` — Configurable Bridging Control Mechanism  *(Severity: Informational · Status: Unresolved)*

The `MyOFTAdapter` contract includes a configurable bridging control mechanism through the `bridgingEnabled` flag and a `whitelist` mapping. When `bridgingEnabled` is set to `false`, only addresses present in the `whitelist` are permitted to initiate bridging operations via the `_debit` function. This feature provides the owner with a powerful tool to pause or restrict token bridging, either globally or for specific users. This is a design choice that offers flexibility for operational control but also introduces a potential point of centralized control over user access to bridging services.

**Recommendation:** Clearly document the intended use cases and operational policies for the `bridgingEnabled` flag and the `whitelist`. Communicate these controls transparently to users. Regularly review the necessity and scope of these controls to ensure they align with the project's long-term decentralization goals and risk management strategy.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x500a...d1c4`](https://bscscan.com/address/0x500a02a20b0b0a3f3efccfc0559543f5743bd1c4) |
| **Network** | BNB Chain |
| **Price** | $0.4799 |
| **24h Volume** | $220.1K |
| **Liquidity** | $2.36M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 96.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3274 buys / 3148 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x1a9b68ca1dcacb106c4b853e2d9c915f0cfe2e56)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/o1exchange-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-20*
