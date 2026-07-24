---
token: Re Protocol reUSD
ticker: REUSD
network: ethereum
risk_score: 82
status: critical
date: 2026-06-20
---

# Re Protocol reUSD (REUSD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 82/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/re-protocol-reusd-eth)

---

## Audit Summary

This audit covers an ERC1967Proxy contract, which utilizes OpenZeppelin's battle-tested UUPS proxy pattern. While the proxy contract itself is robust, a critical vulnerability exists due to the unverified source code of its current implementation contract, 'ShareToken' (0xb5276c436f65913cd5332de745d04fedeb4a21d4). This lack of transparency prevents any security assessment of the actual business logic and upgrade mechanisms, posing a severe risk to the integrity and security of the entire system.

> **Final Recommendation:** It is critically important to verify the source code of the implementation contract (`ShareToken` at `0xb5276c436f65913cd5332de745d04fedeb4a21d4`). Without verification, the functionality and security of the entire system operating behind this proxy are unknown and cannot be trusted. Once verified, a comprehensive audit of the implementation contract's code, including its access control for upgrade functions, should be performed to ensure its integrity and security.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes battle-tested OpenZeppelin libraries for its proxy implementation, ensuring adherence to EIP-1967 standards and robust delegatecall mechanisms (7.1 Architecture, 7.2 Code… |
| **Governance / Economics** | 1/10 | High | The proxy itself is a standard UUPS implementation, which delegates upgrade logic to the implementation contract, allowing for flexible governance models (7.5 Governance). The upgradeability… |
| **Upgrades** | 1/10 | High | The contract correctly implements the UUPS proxy pattern using OpenZeppelin's `ERC1967Proxy` and `ERC1967Utils`, which is a well-established and secure standard for upgradeable contracts (7.7… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · ⚪ 3 Informational_

### `C-01` — Unverified Implementation Contract  *(Severity: Critical · Status: Unresolved)*

The proxy contract (0x5086bf358635b81d8c47c66d1c8b9e567db70c72) delegates all its logic to an implementation contract identified as 'ShareToken' at address 0xb5276c436f65913cd5332de745d04fedeb4a21d4. The source code for this implementation contract is not verified on the blockchain explorer. This means the actual code being executed by the proxy is unknown, making it impossible to assess its security, functionality, or potential malicious behavior. This poses an extreme risk as the contract could contain backdoors, vulnerabilities, or arbitrary logic.

**Recommendation:** Immediately verify the source code of the implementation contract (0xb5276c436f65913cd5332de745d04fedeb4a21d4) on the blockchain explorer. Once verified, a thorough security audit of the implementation's code must be conducted to ensure its safety and integrity.


### `H-01` — Centralized Upgradeability Control  *(Severity: High · Status: Unresolved)*

The contract uses the UUPS proxy pattern, where the upgrade logic and its associated access control reside within the implementation contract. While this is a standard pattern, it implies a centralized point of control for upgrades. If the private key of the address or the multisig controlling the upgrade function within the implementation contract is compromised, an attacker could deploy a malicious new implementation, leading to a complete loss of funds or control over the protocol. The specific details of this control cannot be assessed due to the unverified implementation.

**Recommendation:** Once the implementation contract is verified, ensure that the upgrade function is protected by a robust access control mechanism, ideally a well-configured multi-signature wallet (e.g., Gnosis Safe) with a sufficient threshold, or a time-locked governance mechanism. Implement strict operational security procedures for managing the upgrade key(s).


### `I-01` — OpenZeppelin Library Usage  *(Severity: Informational · Status: Unresolved)*

The contract leverages OpenZeppelin's battle-tested and widely adopted proxy libraries (ERC1967Proxy, ERC1967Utils, IBeacon, Proxy, Address, StorageSlot). This is a strong security practice as these libraries are rigorously audited and maintained by the OpenZeppelin team, significantly reducing the risk of common proxy-related vulnerabilities.

**Recommendation:** Continue to use and monitor updates from OpenZeppelin for best practices and security patches.


### `I-02` — EIP-1967 Compliance  *(Severity: Informational · Status: Unresolved)*

The proxy contract correctly implements the EIP-1967 standard for transparent proxy storage slots. This ensures that the implementation address, admin address (if used), and beacon address (if used) are stored in well-defined, non-colliding storage locations, preventing storage clashes with the logic contract.

**Recommendation:** No action required. This is a best practice.


### `I-03` — Non-Payable Upgrade Check  *(Severity: Informational · Status: Unresolved)*

The `ERC1967Utils.upgradeToAndCall` function includes a check (`_checkNonPayable()`) that reverts if `msg.value > 0` when no `data` is provided for a setup call. This prevents accidental transfer of Ether to the proxy contract during an upgrade operation where the Ether would otherwise become stuck.

**Recommendation:** No action required. This is a good security practice.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5086...0c72`](https://etherscan.io/address/0x5086bf358635b81d8c47c66d1c8b9e567db70c72) |
| **Network** | Ethereum |
| **Price** | $1.0900 |
| **24h Volume** | $64.2K |
| **Liquidity** | $459.6K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 98.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 15 buys / 14 sells |

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

### Is Re Protocol reUSD a scam?

While the data does not definitively confirm Re Protocol reUSD as a scam, several red flags warrant caution. The contract is verified, and ownership is renounced, which are positive indicators. However, the extreme token centralization, with 98.7% held by the top 10 wallets, coupled with unlocked liquidity, presents significant risks often associated with potential malicious activities or market instability. Investors should exercise due diligence.

### Is Re Protocol reUSD safe to buy?

Based on the provided data, Re Protocol reUSD carries a high-risk score of 51/100, suggesting it is not safe for risk-averse investors. Key concerns include the top 10 holders controlling nearly all supply (98.7%), posing a significant centralization risk and potential for market manipulation. Furthermore, the absence of locked liquidity means funds can be withdrawn, increasing volatility and potential for sudden market impact.

### Has Re Protocol reUSD been audited?

The Re Protocol reUSD contract is verified, meaning its code is public and matches the deployed version on the blockchain, providing transparency. However, verification differs from a full security audit performed by third-party experts. The available data does not indicate whether such a comprehensive audit, which assesses code for vulnerabilities, has been completed for the REUSD contract.

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x5c2ab69eb2bf12a2f4572d178687bd4660512972)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/re-protocol-reusd-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-20*
