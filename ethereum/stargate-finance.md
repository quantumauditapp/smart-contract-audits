---
token: Stargate Finance
ticker: STG
network: ethereum
risk_score: 100
status: critical
date: 2026-06-10
---

# Stargate Finance (STG) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stargate-finance-eth)

---

## Audit Summary

The StargateToken contract, an Omnichain Fungible Token (OFT) built on LayerZero, facilitates cross-chain token transfers using a lock/burn and unlock/mint mechanism. The contract leverages OpenZeppelin's ERC20 and Ownable for core functionality and access control. A critical vulnerability was identified in the `lzReceive` function's assembly-based address decoding, which could lead to tokens being minted or unlocked to unintended addresses. Additionally, the contract exhibits a high degree of centralized control by the owner and uses an older Solidity compiler version. The contract is immutable, lacking upgradeability.

> **Final Recommendation:** The Stargate Omnichain Fungible Token contract presents a robust cross-chain architecture but contains a critical vulnerability in its `lzReceive` function's address decoding. Immediate attention is required to address this high-severity issue to prevent potential loss or misdirection of funds. Additionally, the centralized control by the owner should be mitigated, ideally through a multi-signature setup. We recommend a comprehensive review of the LayerZero integration and a potential upgrade to a newer Solidity compiler version. For projects requiring the highest level of security and ongoing support, consider our Premium Deploy option, which includes continuous monitoring, incident response planning, and advanced security features.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The technical architecture (7.1) of the Omnichain Fungible Token (OFT) is well-structured, utilizing a standard lock/burn and mint/unlock mechanism for cross-chain transfers via LayerZero. The contrac |
| **Governance / Economics** | 1/10 | High | The contract's economic model (7.4) is based on a standard OFT design, ensuring token supply consistency across chains through locking/burning and minting/unlocking. Governance (7.5) is highly central |
| **Upgrades** | 2/10 | High | The contract is deployed as an immutable implementation, meaning its logic cannot be changed post-deployment (7.7 Upgrades). This design choice eliminates upgrade-related risks but also prevents bug f |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 52.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Unsafe `_to` Address Decoding in `lzReceive`  *(Severity: High · Status: Unresolved)*

The `lzReceive` function uses inline assembly (`mload(add(_to, 20))`) to decode the `_to` address from the `_payload`. This assembly code assumes that `_to` is a `bytes` type representing a 20-byte address. If a malicious or malformed `_payload` provides a `_to` value that is not exactly 20 bytes, the assembly code could extract an incorrect or arbitrary `toAddress`. This could lead to tokens being minted or unlocked to an unintended address, potentially resulting in loss of funds or unauthorized token distribution.

**Recommendation:** Replace the inline assembly with a safer Solidity-native conversion for `bytes` to `address`. Ensure `_to.length == 20` before attempting conversion. A robust approach would be `require(_to.length == 20, 'OFT: invalid to address length'); address toAddress = address(uint160(bytes20(_to)));`.


### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The `OmnichainFungibleToken` contract inherits `Ownable`, granting significant control to a single `owner` address. The owner can `pauseSendTokens`, effectively halting all cross-chain token transfers. Furthermore, the owner can `setDestination` for LayerZero routing and configure LayerZero endpoint parameters (`setConfig`, `setSendVersion`, `setReceiveVersion`, `forceResumeReceive`). A compromised or malicious owner could disrupt operations, redirect funds, or misconfigure the LayerZero integration, posing a significant risk to the protocol's integrity and user funds.

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the `owner` address to distribute control and require multiple approvals for critical operations. For highly sensitive functions, consider introducing a time-lock mechanism to allow for community review or emergency intervention periods.


### `L-01` — Older Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

The contract is compiled with Solidity version `0.7.6`. While `SafeMath` from OpenZeppelin is used to prevent integer overflows/underflows, newer Solidity versions (e.g., `0.8.x` and above) include native overflow/underflow checks by default. Using an older compiler version means foregoing these built-in safety features and potentially missing out on other compiler improvements and optimizations.

**Recommendation:** Consider upgrading the Solidity compiler version to `0.8.x` or higher. This would allow for the removal of `SafeMath` (as native checks are enabled) and benefit from other compiler enhancements. This upgrade would require careful testing and potentially minor code adjustments to ensure compatibility.


### `I-01` — Immutability and Lack of Upgradeability  *(Severity: Informational · Status: Unresolved)*

The `StargateToken` contract is deployed as a standard implementation without any proxy or upgradeability pattern. This means its logic is immutable once deployed and cannot be modified or patched in case of future vulnerabilities or feature requirements. The `renounceOwnership` function is also overridden to be empty, preventing the owner from relinquishing control. While immutability can be a security feature by guaranteeing unchanging behavior, it also means any discovered critical bug cannot be fixed without a redeployment and migration.

**Recommendation:** If future modifications, bug fixes, or feature enhancements are anticipated, consider adopting a well-audited upgradeability pattern (e.g., UUPS proxy) for future deployments. If immutability is a deliberate design choice, ensure extremely thorough testing and auditing to minimize the risk of unfixable issues.


### `I-02` — Reliance on LayerZero Endpoint Security  *(Severity: Informational · Status: Unresolved)*

The security and functionality of the `OmnichainFungibleToken` are heavily dependent on the underlying LayerZero protocol and its `ILayerZeroEndpoint` implementation. The contract trusts the LayerZero endpoint for message authenticity (`msg.sender == address(endpoint)`) and relies on its correct operation for cross-chain communication. Any vulnerabilities, misconfigurations, or operational issues within the LayerZero endpoint could directly impact the safety and availability of cross-chain token transfers for this OFT.

**Recommendation:** Maintain continuous monitoring of the LayerZero protocol's security posture, updates, and operational status. Ensure the configured LayerZero endpoint address is correct, trusted, and regularly audited. Implement robust off-chain monitoring for LayerZero message failures or anomalies.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xaf51...2cd6`](https://etherscan.io/address/0xaf5191b0de278c7286d6c7cc6ab6bb8a73ba2cd6) |
| **Network** | Ethereum |
| **Price** | $0.404 |
| **24h Volume** | $1.03M |
| **Liquidity** | $1.08M |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 4y |
| **Top-10 Holders** | 94.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 561 buys / 393 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x3211c6cbef1429da3d0d58494938299c92ad5860)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stargate-finance-eth)
- Security data: [GoPlus Labs](https://gopluslabs.io)

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
