---
token: ViciCoin
ticker: VCNT
network: base
risk_score: 51
status: high
date: 2026-07-22
---

# ViciCoin (VCNT) — Smart Contract Security Analysis | Base

> **Risk Score: 51/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vicicoin-base)

---

## Audit Summary

This audit covers a TransparentUpgradeableProxy contract, a standard OpenZeppelin implementation. While the proxy contract itself is well-audited and robust, the security posture is significantly impacted by the unverified implementation contract it points to and the unknown security setup of its administrative control. These factors introduce substantial risks related to potential malicious upgrades and lack of transparency.

> **Final Recommendation:** Prioritize verifying the source code of the current implementation contract to enable a full security assessment. Implement robust security measures for the admin key, such as a multi-signature wallet or a dedicated `ProxyAdmin` contract, to mitigate the risk of a single point of failure. Establish a clear and secure upgrade process, including thorough testing and auditing of all new implementation versions before deployment to the production proxy.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The TransparentUpgradeableProxy contract itself is a robust and well-audited OpenZeppelin component (7.2 Code Security). It correctly implements the transparent proxy pattern, preventing selector… |
| **Governance / Economics** | 1/10 | High | The contract's economic and governance security is heavily dependent on the administrative control (7.3 Access Control, 7.5 Governance). The proxy allows a single admin address to initiate upgrades… |
| **Upgrades** | 2/10 | High | The contract utilizes the Transparent Proxy pattern for upgradeability (7.7 Upgrades), allowing the implementation logic to be changed. While the mechanism itself is standard, the unverified nature… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Other-Contract |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 61.3% |
| **Top-3 Unlocked** | ⚠️ 84.1% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low_

### `H-01` — Unverified Implementation Contract  *(Severity: High · Status: Unresolved)*

The implementation contract at address `0xa0f7218896821b5d87e15dd8c554e9f01fa31296` is not verified on Etherscan. This prevents any security analysis of the actual business logic that the proxy delegates to. Without verified source code, it is impossible to ascertain the contract's functionality, identify vulnerabilities, or confirm its intended behavior, posing a critical trust and security risk.

**Recommendation:** Immediately verify the source code of the implementation contract on Etherscan. This is crucial for transparency, allowing users and auditors to understand and trust the underlying logic. Conduct a thorough audit of the implementation contract once its source code is available.


### `H-02` — Centralized Upgrade Authority and Unknown Admin Setup  *(Severity: High · Status: Unresolved)*

The proxy's upgradeability and administrative functions are controlled by a single admin address. The prefill data indicates that the `admin_address` and `admin_kind` are null, suggesting the admin's security setup is not clearly identified or is not a standard `ProxyAdmin` contract. If this admin key is an Externally Owned Account (EOA) and is compromised, an attacker could upgrade the contract to a malicious implementation, leading to a complete loss of funds or control over the protocol.

**Recommendation:** Secure the admin key using a robust mechanism such as a multi-signature wallet (e.g., Gnosis Safe) or deploy a dedicated `ProxyAdmin` contract to manage the proxy. Ensure the admin address is publicly known and its security setup is transparent. Implement strict operational procedures for managing the admin key and executing upgrades.


### `M-01` — Potential for Malicious or Buggy Upgrades  *(Severity: Medium · Status: Unresolved)*

The upgradeability feature allows the contract's logic to be changed at any time by the admin. While this offers flexibility, it also introduces the risk that a new implementation could contain critical bugs, introduce backdoors, or deviate from expected functionality. This risk is exacerbated by the current unverified implementation, making it impossible to assess the baseline security.

**Recommendation:** Establish a rigorous upgrade process that includes comprehensive testing, independent security audits, and a public review period for all new implementation versions before they are deployed. Consider implementing a timelock for upgrades to provide users with a window to react to potentially malicious changes. Ensure all new implementations are thoroughly verified on Etherscan.


### `L-01` — Admin Cannot Directly Call Implementation Functions  *(Severity: Low · Status: Unresolved)*

The Transparent Proxy pattern explicitly prevents the admin address from directly calling functions on the implementation contract via the proxy's fallback function. This is a security feature to prevent selector clashes with proxy admin functions. However, it can lead to unexpected errors or confusion if the admin attempts to interact with the implementation directly through the proxy, requiring them to use a non-admin account or a `ProxyAdmin` contract.

**Recommendation:** Ensure all administrators are fully aware of the Transparent Proxy pattern's behavior, specifically that they cannot call implementation functions directly through the proxy. If direct interaction with the implementation is required for administrative tasks, it should be done via a non-admin account or through a dedicated `ProxyAdmin` contract, which is designed to manage the proxy.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xdcf5...bfd0`](https://basescan.org/address/0xdcf5130274753c8050ab061b1a1dcbf583f5bfd0) |
| **Network** | Base |
| **Price** | $15.6200 |
| **24h Volume** | $115.6K |
| **Liquidity** | $179.6K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 2y |
| **Top-10 Holders** | 82.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2675 buys / 2774 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xe8f16fbf4eafec04bcf0c06d768e7ba325f9d6de)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vicicoin-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-22*
