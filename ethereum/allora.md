---
token: Allora
ticker: ALLO
network: ethereum
risk_score: 91
status: critical
date: 2026-06-10
---

# Allora (ALLO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 91/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/allora-eth)

---

## Audit Summary

This audit focuses on the provided OpenZeppelin ERC1967 Transparent Proxy contract. The proxy itself utilizes well-audited and standard components. However, the critical finding is that the source code for the underlying implementation contract (AlloOFTUpgradeable) is unverified, preventing a comprehensive security assessment of the system's core logic. Additionally, while upgrade control is managed by a multisig, the absence of a timelock for upgrades introduces a higher operational risk.

> **Final Recommendation:** Prioritize verifying and thoroughly auditing the source code for the `AlloOFTUpgradeable` implementation contract to ensure its security and integrity. Implement a timelock mechanism for all critical administrative operations, especially contract upgrades, to provide a delay period for public scrutiny and emergency response. Regularly review and update multisig signers and their security practices to maintain robust access control over the system's upgradeability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The proxy contract (ERC1967Proxy) is built upon battle-tested OpenZeppelin libraries, ensuring a robust foundation for its core functionality (7.2 Code Security). The architecture correctly… |
| **Governance / Economics** | 1/10 | High | The governance model for upgrades employs a 2-of-3 multisig for the `ProxyAdmin` (7.5 Governance), which is a strong access control mechanism, reducing the risk of a single point of failure (7.3… |
| **Upgrades** | 1/10 | High | The system utilizes the EIP-1967 Transparent Proxy pattern, a well-established and secure method for upgradeability (7.7 Upgrades). This pattern correctly separates the admin interface from the… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Multisig 2-of-3 |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Unverified Implementation Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The core logic of the system resides in the implementation contract (AlloOFTUpgradeable at 0xb21c7c5a7be430ea3517892e63f905c109b06278), but its source code is not publicly verified. This prevents any security assessment of the actual business logic, making it impossible to identify vulnerabilities such as reentrancy, access control flaws, or economic exploits. Users and auditors cannot independently verify the contract's behavior or safety.

**Recommendation:** Immediately verify and publish the source code for the `AlloOFTUpgradeable` implementation contract on block explorers. Conduct a thorough security audit of this implementation contract to identify and remediate any vulnerabilities. Ensure that all future implementation upgrades also have their source code verified.


### `H-01` — Lack of Timelock for Critical Operations (Upgrades)  *(Severity: High · Status: Unresolved)*

While the upgrade mechanism is controlled by a 2-of-3 multisig, there is no timelock in place for executing upgrades. This means that once the required multisig approvals are obtained, an upgrade can be deployed instantly. This lack of a delay period prevents users, the community, or automated monitoring systems from reacting to a potentially malicious or erroneous upgrade before it takes effect, increasing the risk of irreversible damage or fund loss.

**Recommendation:** Integrate a timelock contract into the upgrade process. The `ProxyAdmin` should be owned by a timelock, which in turn is controlled by the multisig. This ensures that any proposed upgrade has a mandatory delay period (e.g., 24-72 hours) before it can be executed, allowing for review and potential intervention.


### `M-01` — Reliance on External Contracts for Core Logic  *(Severity: Medium · Status: Unresolved)*

The security and functionality of the entire system are entirely dependent on the `AlloOFTUpgradeable` implementation contract. Any vulnerability within this external contract, whether due to design flaws, coding errors, or malicious intent, will directly impact the proxy and its users. This risk is exacerbated by the unverified source code of the implementation.

**Recommendation:** Ensure rigorous security practices for the development, testing, and auditing of the implementation contract. Implement robust monitoring for the implementation contract's behavior and state. Consider formal verification or extensive fuzzing for critical components of the implementation.


### `L-01` — Centralized Upgrade Authority  *(Severity: Low · Status: Unresolved)*

Although the upgrade authority is managed by a 2-of-3 multisig, this still represents a centralized point of control. If a majority of the multisig signers are compromised, collude, or act maliciously, they could unilaterally upgrade the contract to a harmful implementation, potentially leading to loss of funds or system compromise.

**Recommendation:** While a multisig is a strong control, consider further decentralizing the upgrade authority over time, possibly by integrating a more distributed governance mechanism or a larger, more diverse set of signers. Implement strict operational security procedures for all multisig signers, including hardware wallets, secure key management, and multi-factor authentication.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8408...0489`](https://etherscan.io/address/0x8408d45b61f5823298f19a09b53b7339c0280489) |
| **Network** | Ethereum |
| **Price** | $0.4922 |
| **24h Volume** | $2.5K |
| **Liquidity** | $6.0K |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 93.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xae347990c244c4b7ee42c85b24026ceed0bc4c844934f9a8030c7f8223a73ecc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/allora-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
