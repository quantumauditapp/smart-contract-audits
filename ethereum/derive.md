---
token: Derive
ticker: DRV
network: ethereum
risk_score: 47
status: high
date: 2026-07-14
---

# Derive (DRV) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 47/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/derive-eth)

---

## Audit Summary

The audit focused on the `TransparentUpgradeableProxy` contract. While the proxy itself is a standard, well-audited OpenZeppelin component, the overall system presents critical risks due to the unverified source code of its implementation contract and the unknown ownership structure of the `ProxyAdmin` contract that controls upgrades. These factors introduce significant technical, governance, and upgradeability concerns.

> **Final Recommendation:** It is critical to verify the source code of the implementation contract (0x4909ad99441ea5311b90a94650c394cea4a881b8) to allow for a comprehensive security audit of its logic and functionality. Additionally, the ownership of the `ProxyAdmin` contract (0xaa7b17c2539437efa236fed262a5815358ae2cc3) should be publicly disclosed and ideally managed by a robust multi-signature wallet or a time-locked governance mechanism to mitigate centralization risks and enhance upgrade security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The audited `TransparentUpgradeableProxy` contract (7.1 Architecture, 7.2 Code Security) utilizes the robust and well-audited OpenZeppelin transparent proxy pattern, effectively mitigating selector… |
| **Governance / Economics** | 2/10 | High | The governance and economic security (7.4 Economic, 7.5 Governance) of the system are severely impacted by the lack of transparency regarding the implementation contract and the `ProxyAdmin`'s… |
| **Upgrades** | 1/10 | High | The system employs the Transparent Proxy pattern (7.7 Upgrades) for upgradeability, a standard and secure mechanism when properly managed. However, the upgrade process carries significant risks due… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | Other-Contract |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 2 Informational_

### `C-01` — Unverified Implementation Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The proxy contract (0xb1d1eae60eea9525032a6dcb4c1ce336a1de71be) points to an implementation contract (0x4909ad99441ea5311b90a94650c394cea4a881b8) whose source code is not publicly verified on the blockchain explorer. This prevents any security analysis of the actual business logic, potential vulnerabilities (e.g., reentrancy, access control flaws, integer overflows), and economic implications of the system. Users and auditors cannot ascertain the contract's behavior or safety.

**Recommendation:** Immediately verify the source code of the implementation contract (0x4909ad99441ea5311b90a94650c394cea4a881b8) on the blockchain explorer. Once verified, a full audit of the implementation's logic should be conducted to identify and mitigate any vulnerabilities.


### `H-01` — Unknown/Unverified Ownership of ProxyAdmin Contract  *(Severity: High · Status: Unresolved)*

The `TransparentUpgradeableProxy` deploys and relies on a `ProxyAdmin` contract (0xaa7b17c2539437efa236fed262a5815358ae2cc3) to manage upgrades. The ownership structure of this `ProxyAdmin` contract is not publicly verifiable or disclosed. If the owner is a single Externally Owned Account (EOA), it represents a single point of failure, making the entire system vulnerable to compromise if that EOA's private key is lost or stolen. This also centralizes control over all future upgrades.

**Recommendation:** Publicly disclose the ownership details of the `ProxyAdmin` contract. It is strongly recommended that the `ProxyAdmin`'s ownership be transferred to a robust multi-signature wallet (e.g., Gnosis Safe) with a sufficient threshold, or a time-locked governance contract, to enhance security, decentralize control, and provide a delay for critical operations.


### `I-01` — Use of Transparent Proxy Pattern  *(Severity: Informational · Status: Unresolved)*

The contract utilizes the Transparent Proxy Pattern, a well-established and audited upgradeability pattern from OpenZeppelin. This pattern effectively prevents selector clashes between the proxy and the implementation contract for non-admin calls, ensuring predictable behavior and reducing potential attack vectors.

**Recommendation:** No specific recommendation. Continue to follow best practices for managing the `ProxyAdmin` and its ownership.


### `I-02` — Immutable Admin Address in Proxy  *(Severity: Informational · Status: Unresolved)*

The `_admin` variable in the `TransparentUpgradeableProxy` contract is declared as `immutable`. This design choice ensures that the proxy's direct link to its `ProxyAdmin` cannot be changed after deployment, preventing unauthorized modifications to the admin address at the proxy level. This enhances the internal security and predictability of the proxy contract itself.

**Recommendation:** No specific recommendation. This is a good security practice for the proxy contract.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb1d1...71be`](https://etherscan.io/address/0xb1d1eae60eea9525032a6dcb4c1ce336a1de71be) |
| **Network** | Ethereum |
| **Price** | $0.1207 |
| **24h Volume** | $9.4K |
| **Liquidity** | $32.6K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 4mo |
| **Top-10 Holders** | 88.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 196 buys / 210 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x20ae5557f7d6ce39a6e5370c331106a87a80ea5c1bec686361bde2d9f5e82631)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/derive-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-14*
