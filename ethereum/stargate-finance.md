---
token: Stargate Finance
ticker: STG
network: ethereum
risk_score: 66
status: high
date: 2026-06-10
---

# Stargate Finance (STG) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 66/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stargate-finance-eth)

---

## Audit Summary

The StargateToken contract is an ERC20 token with omnichain capabilities powered by LayerZero. It implements a standard lock/burn and mint/unlock mechanism for cross-chain transfers. The contract utilizes OpenZeppelin's battle-tested libraries for ERC20 and access control. Key findings include significant centralized control by the owner, inherent reliance on the LayerZero endpoint's security, and a minor concern regarding inline assembly for address decoding. The contract is not upgradeable, simplifying its security profile in that regard.

> **Final Recommendation:** Strengthen the operational security around the contract owner's private key, ideally by implementing a multi-signature wallet with robust access controls and potentially a time-lock for critical administrative actions. Thoroughly review and test the LayerZero endpoint configurations and maintain awareness of LayerZero's security updates. While the assembly for address decoding is functional, consider refactoring it for improved readability and safety using `abi.decode` if compatible with LayerZero's payload structure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract leverages OpenZeppelin's battle-tested ERC20 and SafeMath for token operations, enhancing code security (7.2). It implements a standard lock/burn and mint/unlock mechanism for… |
| **Governance / Economics** | 1/10 | High | The contract employs an `Ownable` access control pattern, granting the owner significant power over critical functions such as pausing token transfers and setting destination contracts (7.3). This… |
| **Upgrades** | 6/10 | Medium | The contract is deployed as a standard, non-upgradeable implementation (7.7). This design choice eliminates the complexities and risks associated with proxy upgrade mechanisms, such as storage… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 52.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Control by Owner  *(Severity: High · Status: Unresolved)*

The `Ownable` pattern grants the contract owner extensive control over critical functions, including `pauseSendTokens`, `setDestination`, and various LayerZero endpoint configurations (`setConfig`, `setSendVersion`, `setReceiveVersion`, `forceResumeReceive`). A compromise of the owner's private key could lead to the pausing of cross-chain transfers, misdirection of funds by setting malicious destination contracts, or manipulation of LayerZero configurations. (7.3 Access Control, 7.4 Economic, 7.8 Operations)

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for ownership of the contract to distribute control and reduce the single point of failure risk. Consider time-locks for critical administrative actions to allow for community review or emergency response.


### `M-01` — Reliance on External LayerZero Endpoint Security  *(Severity: Medium · Status: Unresolved)*

The contract's core cross-chain functionality relies entirely on the security and correct operation of the LayerZero endpoint. Any vulnerabilities, misconfigurations, or compromises within the LayerZero protocol or its specific endpoint implementation could directly impact the integrity of token transfers, potentially leading to loss of funds or incorrect token supply across chains. (7.6 External)

**Recommendation:** While direct mitigation within this contract is limited, it is crucial to maintain a strong understanding of LayerZero's security posture, monitor their announcements, and have contingency plans in place for potential LayerZero-related incidents. Ensure the LayerZero endpoint address used is the official and correct one.


### `L-01` — Assembly for Address Decoding  *(Severity: Low · Status: Unresolved)*

The `lzReceive` function uses an inline assembly block (`assembly { toAddress := mload(add(_to, 20)) }`) to extract an `address` from a `bytes` variable `_to`. While this pattern can be efficient, it relies on specific knowledge of how `bytes` are encoded in memory and assumes `_to` will always contain a 20-byte address at the expected offset. If the encoding of `_to` were to change or if `_to` were not exactly 20 bytes, this could lead to incorrect address extraction or unexpected behavior. (7.2 Code Security)

**Recommendation:** Consider using `abi.decode` directly if the `_to` parameter is consistently an `address` type encoded as `bytes`. For example, if `_to` is always `abi.encodePacked(address_value)`, then `(address toAddress, uint256 qty) = abi.decode(_payload, (address, uint256));` would be safer and more readable. If the current assembly is strictly necessary due to LayerZero's specific payload structure, ensure thorough testing covers edge cases for `_to`'s length and content.


### `I-01` — Renounce Ownership Disabled  *(Severity: Informational · Status: Unresolved)*

The `renounceOwnership()` function is overridden to be a no-op (`function renounceOwnership() public override onlyOwner {}`). This prevents the owner from accidentally or intentionally renouncing ownership, which can be a security feature to avoid leaving the contract unmanaged. However, it also means that ownership cannot be permanently removed without transferring it to another address. (7.3 Access Control, 7.8 Operations)

**Recommendation:** This is a design choice. If the intention is to always have an owner, this implementation is acceptable. Ensure that the owner address is securely managed and that there are clear operational procedures for ownership transfers.


### `I-02` — BUSL-1.1 License  *(Severity: Informational · Status: Unresolved)*

The contract uses the Business Source License 1.1 (BUSL-1.1). This is a non-open source license that typically restricts usage for a certain period or until specific conditions are met, after which it may convert to an open-source license like MIT. While not a security vulnerability, it's important for users and integrators to be aware of the licensing terms and their implications for usage and modification.

**Recommendation:** Ensure all parties interacting with or building upon this contract understand the terms and conditions of the BUSL-1.1 license.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xaf51...2cd6`](https://etherscan.io/address/0xaf5191b0de278c7286d6c7cc6ab6bb8a73ba2cd6) |
| **Network** | Ethereum |
| **Price** | $0.1383 |
| **24h Volume** | $518 |
| **Liquidity** | $14.7K |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 4y |
| **Top-10 Holders** | 93.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 561 buys / 393 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x3211c6cbef1429da3d0d58494938299c92ad5860)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stargate-finance-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-06-10*
