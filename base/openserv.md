---
token: OpenServ
ticker: SERV
network: base
risk_score: 54
status: medium
date: 2026-09-28
---

# OpenServ (SERV) — Smart Contract Security Analysis | Base

> **Risk Score: 54/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/openserv-base)

---

## Audit Summary

The BridgeToken contract, implemented as a BeaconProxy, provides standard ERC-20 functionalities along with owner-controlled minting, burning, and metadata updates. It incorporates EIP-712 Permit functionality. While the code adheres to good practices for ERC-20 and proxy patterns, significant centralization risks exist due to the owner's control over token supply and the BeaconProxy's upgrade mechanism. The owner is an external contract, which can mitigate some single-point-of-failure risks if it's a robust multi-sig or governance system.

> **Final Recommendation:** Strengthen the security of the owner address and the Beacon contract, as these represent significant centralization risks. Consider implementing a `transferOwnership` mechanism if future owner changes are desired without requiring a full contract upgrade. Ensure all external integrations are aware that metadata changes can invalidate existing EIP-712 permit signatures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract implements ERC-20 standards correctly, including transfer, approval, and balance management with appropriate checks for zero addresses and sufficient balances (7.2 Code Security).… |
| **Governance / Economics** | 5/10 | Medium | The contract grants the owner significant control over the token's economic parameters, specifically the ability to `mint` and `burn` arbitrary amounts of tokens (7.4 Economic, 7.3 Access Control).… |
| **Upgrades** | 1/10 | High | The contract is designed as an implementation for a BeaconProxy, which allows for upgradeability (7.7 Upgrades). The `initializer` modifier correctly prevents re-initialization of the implementation… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 82.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 3 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Immutable Owner After Initialization  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract's owner is set during the `initialize` function via the `owner_` parameter and stored in `_state.owner`. There is no dedicated `transferOwnership` or `renounceOwnership` function provided in the `TokenImplementation` contract. This means that once initialized, the owner address cannot be changed through a standard function call. While an upgrade via the BeaconProxy pattern could theoretically change the owner by modifying the storage slot directly, the lack of a explicit transfer mechanism increases operational rigidity and could complicate owner management or recovery in certain scenarios.

**Recommendation:** Consider adding a `transferOwnership(address newOwner_)` function, protected by `onlyOwner`, to allow for a secure and explicit transfer of administrative control. This would enhance operational flexibility and provide a standard way to manage the owner role.


### `M-02` — Centralized Control of Token Supply  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `mint` and `burn` functions are protected by the `onlyOwner` modifier, allowing the contract owner to arbitrarily increase or decrease the total supply of tokens. While this is a common design for bridge or wrapped tokens, it introduces a high degree of centralization and economic risk. A compromise of the owner's private key or the owner contract could lead to uncontrolled token supply manipulation, devaluing the token or causing significant financial loss to users.

**Recommendation:** Ensure the owner address (0x8d2de8d2f73f1f4cab472ac9a881c9b123c79627) is secured with robust multi-signature controls, time-locks, or a well-audited governance mechanism. Implement strict operational procedures for minting and burning, and consider transparent reporting of such operations.


### `M-03` — Beacon Proxy Centralization Risk  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract is an implementation for a BeaconProxy. This pattern means that the `BridgeToken` proxy's logic can be updated by changing the implementation address stored in the Beacon contract. The security of the Beacon contract itself, and the entity controlling its upgrades, is a critical single point of failure. If the Beacon or its owner is compromised, all associated proxies could be upgraded to a malicious implementation, leading to potential loss of funds or control.

**Recommendation:** Implement stringent security measures for the Beacon contract and its owner. This should include multi-signature wallets, time-locks for upgrade proposals, and thorough auditing of any new implementation contracts before they are set in the Beacon. Clearly communicate the upgradeability mechanism and its associated risks to users.


### `L-01` — Metadata Update Invalidates EIP-712 Permit Signatures  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `updateDetails` function allows the owner to change the token's `name` and `symbol`. When these parameters change, the EIP-712 domain separator, which is derived from the token's name, version, chain ID, and verifying contract, will also change. This will invalidate any existing EIP-712 `permit` signatures that were generated using the old domain separator. While this behavior is inherent to the EIP-712 standard when domain parameters are modified, it could lead to unexpected failures for users or dApps relying on pre-signed permits.

**Recommendation:** Inform users and integrated dApps that changes to the token's name or symbol via `updateDetails` will invalidate previously signed EIP-712 permits. Ensure clear communication channels are in place to announce such updates.


### `I-01` — `TokenState` Contract Not Provided for Full Review  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `TokenImplementation` contract inherits from `TokenState`, which is responsible for defining the contract's storage layout and likely includes critical state variables such as `balances`, `allowances`, `totalSupply`, and `nonces` for EIP-712 permits. The source code for `TokenState` was not provided for this audit. While the `TokenImplementation` appears to correctly interact with `_state`, a full review of `TokenState` is necessary to confirm its storage layout, variable types, and overall security, especially for proxy compatibility and nonce management.

**Recommendation:** Provide the source code for the `TokenState` contract for a comprehensive security review, ensuring its storage layout is compatible with the proxy pattern and that all state management logic is robust and secure.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5576...37ea`](https://basescan.org/address/0x5576d6ed9181f2225aff5282ac0ed29f755437ea) |
| **Network** | Base |
| **Price** | $0.02308 |
| **24h Volume** | $79.6K |
| **Liquidity** | $834.5K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 39.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 55 buys / 62 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x3416f5fa0ade2d3de6935d4b204d9fe0b68c0ea6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/openserv-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-28*
