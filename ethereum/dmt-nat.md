---
token: dmt-nat
ticker: DMT-NAT
network: ethereum
risk_score: 76
status: critical
date: 2026-08-11
---

# dmt-nat (DMT-NAT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 76/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dmt-nat-eth)

---

## Audit Summary

The Tap Bridge protocol consists of a bridge contract and a token contract. The bridge facilitates cross-chain transfers by minting and burning tokens, utilizing a centralized `canister` for signature verification and an `ADMIN_ROLE` for configuration. While the code leverages OpenZeppelin libraries and includes custom error handling, several significant risks were identified, including an immutable fee recipient, non-upgradeable cloned token instances, and a high reliance on the security of a single off-chain key.

> **Final Recommendation:** It is strongly recommended to address the identified high and medium severity issues. Prioritize making the fee recipient address configurable by the `ADMIN_ROLE` to ensure proper governance and operational flexibility. Evaluate the upgradeability strategy for cloned tokens to allow for future bug fixes and enhancements. Implement robust security measures and multi-signature controls for the `canister` key to mitigate the significant centralization risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture (7.1) utilizes OpenZeppelin contracts for ERC20 and AccessControl, enhancing code security (7.2). Custom error handling and event logging are well-implemented. However, a… |
| **Governance / Economics** | 1/10 | High | The economic model (7.4) includes a fee mechanism and a discount system, configurable by the `ADMIN_ROLE` (7.5 Governance). However, the `admin` address designated to receive fees is immutable… |
| **Upgrades** | 2/10 | High | While the `TapToken` contract is designed as an upgradeable ERC20, the `TapBridge` contract itself is not upgradeable (7.7 Upgrades). More critically, when `TapBridge` deploys new token instances… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Immutable Fee Recipient Address  *(Severity: High · Status: Unresolved)*

The `admin` address, which receives fees in `bridgeIn` and `bridgeOut` functions, is set in the constructor and declared as `private`. This makes it immutable after deployment. If the `ADMIN_ROLE` (which controls `setFee` and `setDiscount`) is transferred to a new entity, the original deployer will continue to receive all collected fees, creating a misalignment between control and revenue, and potentially leading to operational issues or disputes. (7.3 Access Control, 7.4 Economic, 7.8 Operations)

**Recommendation:** Introduce a function, restricted to the `ADMIN_ROLE`, to allow updating the `admin` address responsible for receiving fees. This would provide necessary flexibility and ensure that the fee recipient can be aligned with current governance or operational needs. Consider using a dedicated `FEE_RECIPIENT_ROLE` if the fee recipient is distinct from the general `ADMIN_ROLE`.


### `M-01` — Non-Upgradeable Cloned Token Instances  *(Severity: Medium · Status: Unresolved)*

While `TapToken` is an `ERC20Upgradeable` contract, the `TapBridge` contract uses `Clones.clone(tokenTemplate)` to deploy new token instances. These cloned instances are direct copies of the `tokenTemplate` implementation and are not upgradeable themselves. If a critical vulnerability or bug is discovered in the `TapToken` implementation, all already deployed token instances cannot be patched or upgraded. Only new token deployments would benefit from an updated `tokenTemplate` pointing to a new implementation. (7.7 Upgrades)

**Recommendation:** Re-evaluate the upgradeability strategy for cloned tokens. If upgradeability for individual token instances is desired, consider deploying proxy contracts (e.g., UUPS proxies) for each new token instead of direct clones. Alternatively, clearly document this limitation and ensure the `TapToken` implementation is thoroughly audited to minimize the risk of unpatchable vulnerabilities.


### `M-02` — Centralization Risk via Canister Key  *(Severity: Medium · Status: Unresolved)*

The `bridgeIn` function relies on a signature from the `canister` address to authorize token minting. This design introduces a significant centralization risk (7.6 External). If the private key associated with the `canister` address is compromised, an attacker could mint an arbitrary amount of any bridged token, leading to hyperinflation, a complete loss of trust, and potential economic collapse of the bridged assets. (7.4 Economic, 7.8 Operations)

**Recommendation:** Implement robust security measures for the `canister`'s private key, such as multi-signature wallets (e.g., Gnosis Safe), hardware security modules (HSMs), or a distributed key management system. Consider adding a time-lock or a governance-controlled pause mechanism for `bridgeIn` operations in case of a suspected compromise.


### `L-01` — Anti-Contract Check in bridgeOut Function  *(Severity: Low · Status: Unresolved)*

The `bridgeOut` function includes a check `if (_msgSender().code.length > 0) revert Errors.LikelyContract(_msgSender());` which prevents contract addresses from calling this function. While intended to mitigate certain risks (e.g., reentrancy from malicious contracts), this check can restrict legitimate use cases, such as users interacting via smart contract wallets, multi-signature wallets, or other DeFi protocols. (7.1 Architecture)

**Recommendation:** Carefully consider the trade-offs of this restriction. If the intention is to prevent reentrancy, ensure other safeguards are in place. If the goal is to prevent specific types of contract interactions, evaluate if this blanket restriction is necessary or if more targeted checks could be implemented. Removing this check would increase composability but might require additional security considerations.


### `I-01` — Inconsistent AccessControl Versions  *(Severity: Informational · Status: Unresolved)*

The `TapToken` contract imports `AccessControlUpgradeable`, while the `TapBridge` contract imports `AccessControl` (the non-upgradeable version). While `TapBridge` is not currently upgradeable, this inconsistency could lead to confusion or potential issues if `TapBridge` were to be made upgradeable in the future without careful consideration of the `AccessControlUpgradeable` pattern. (7.1 Architecture)

**Recommendation:** For consistency and future-proofing, consider using `AccessControlUpgradeable` in `TapBridge` if there's any long-term plan for it to become upgradeable. If `TapBridge` is definitively not intended to be upgradeable, this is a minor stylistic inconsistency rather than a vulnerability, but it's good practice to maintain consistency across related contracts.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2491...1247`](https://etherscan.io/address/0x249130f5e2dd4cf278180c0df8273f3592ad1247) |
| **Network** | Ethereum |
| **Price** | $0.00000009 |
| **24h Volume** | $45.8K |
| **Liquidity** | $801.4K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 71 buys / 50 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xb44cc02c4ffa5ad68cc66ab404800a4f0029e5b6a9752b7cffc1bf8bbaaa92a3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dmt-nat-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
