---
token: Centrifuge
ticker: CFG
network: ethereum
risk_score: 38
status: medium
date: 2026-08-31
---

# Centrifuge (CFG) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/centrifuge-eth)

---

## Audit Summary

The audit of the Centrifuge CFG token contracts (CFG and DelegationToken) identified a critical access control vulnerability related to the public `mint` function, which could allow unauthorized token creation. Other aspects, such as delegation logic and arithmetic operations, appear robust. The contracts are not upgradeable. A full review of the base ERC20 contract is recommended.

> **Final Recommendation:** Immediately address the critical access control vulnerability related to the `public` `mint` function in `DelegationToken`. Ensure that token creation is strictly controlled by an authorized entity or a robust governance mechanism. Additionally, conduct a comprehensive audit of the underlying `protocol-v3/misc/ERC20.sol` contract to verify its security and adherence to ERC-20 standards, especially regarding sensitive functions like `mint` and `burn`. Document the full access control architecture, including the role and permissions of the `ward` address.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The technical architecture is based on a standard ERC-20 token with added delegation capabilities, leveraging Solidity 0.8.28 for enhanced safety. The `delegateWithSig` function correctly uses nonces… |
| **Governance / Economics** | 3/10 | High | The token implements a standard delegation mechanism for governance, allowing holders to delegate voting power. This design is common for decentralized governance systems (7.5 Governance). The… |
| **Upgrades** | 3/10 | High | The provided contracts do not implement any explicit upgradeability patterns (e.g., proxy contracts). This means the contracts are immutable once deployed (7.7 Upgrades). Any future changes or bug… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 48.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Public `mint` function allows unauthorized token creation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DelegationToken` contract declares `function mint(address to, uint256 value) public override(ERC20)`. If the overridden `ERC20.mint` function (or the underlying `_mint` function it calls) does not implement proper access control (e.g., `onlyOwner`, `onlyMinter`), then any external caller can invoke this `mint` function to create an arbitrary amount of tokens. This would lead to an infinite supply and complete devaluation of the token. The provided code snippet for `DelegationToken` does not add any access control to this `public` function.

**Recommendation:** Ensure that the `mint` function in `DelegationToken` (or its base `ERC20` implementation) is adequately protected by an access control mechanism, such as `onlyOwner` or `onlyMinter`, to prevent unauthorized token creation. If the intention is for `mint` to be callable by specific roles, those roles must be enforced.


### `L-01` — Dependency on unprovided `ERC20` implementation  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `DelegationToken` contract inherits from `ERC20` located at `protocol-v3/misc/ERC20.sol`. The full source code for this base `ERC20` contract was not provided for review. The security and correctness of `DelegationToken` heavily depend on the robustness and proper implementation of this external `ERC20` contract, especially concerning access control for functions like `mint` and `burn`, and standard ERC-20 behaviors (7.6 External).

**Recommendation:** Conduct a thorough audit of the `protocol-v3/misc/ERC20.sol` contract to ensure it adheres to security best practices and correctly implements ERC-20 standards, particularly regarding access control for sensitive functions like `mint` and `burn`.


### `I-01` — Unspecified `rely` access control mechanism  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `CFG` contract constructor calls `rely(ward)`. This suggests the use of a `DSAuth`-like access control pattern where a `ward` address is granted permissions. However, the `rely` function and any corresponding `auth` checks are not present in the provided code. Without the full implementation of this access control system, the scope of the `ward`'s privileges and the overall access control model cannot be fully assessed (7.3 Access Control).

**Recommendation:** Ensure that the `rely` and `auth` mechanisms are correctly implemented and that the `ward` address's permissions are clearly defined and limited to necessary administrative functions. Document the full access control architecture.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcccc...8a94`](https://etherscan.io/address/0xcccccccccc33d538dbc2ee4feab0a7a1ff4e8a94) |
| **Network** | Ethereum |
| **Price** | $0.1079 |
| **24h Volume** | $118.5K |
| **Liquidity** | $1.04M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 46.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 106 buys / 57 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x267d01a3b23fe2340482242db5396f7544d36f398862efa591e92a079348cd9c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/centrifuge-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-31*
