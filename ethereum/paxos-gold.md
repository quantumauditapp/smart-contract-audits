---
token: Paxos Gold
ticker: PAXG
network: ethereum
risk_score: 11
status: low
date: 2026-08-11
---

# Paxos Gold (PAXG) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 11/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/paxos-gold-eth)

---

## Audit Summary

The audit of the PAXG token implementation (0x7da4c5d9eca180a03765a6d27196f2a0380fa543) revealed a critical storage collision within its custom freezing mechanism, which directly overwrites a deprecated but existing storage variable. The contract also employs complex and risky assembly-based storage migration during upgrades. While leveraging OpenZeppelin's upgradeable access control, the overall storage architecture and upgrade process present significant security risks.

> **Final Recommendation:** Address the critical storage collision immediately by redesigning the freezing mechanism to use a non-colliding storage slot. Thoroughly review and refactor the `_migratePAXGStorage` function, ideally replacing assembly-based slot manipulation with safer, Solidity-native storage management or a well-tested migration library. Consolidate or clearly deprecate all redundant freezing mechanisms and storage variables to improve clarity and reduce the attack surface. Consider migrating to a more modern proxy pattern like UUPS for enhanced upgrade safety and decentralization of control.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The technical architecture benefits from inheriting OpenZeppelin's upgradeable access control (7.3 Access Control) and standard ERC-20 token functionalities (7.1 Architecture). However, a critical… |
| **Governance / Economics** | 9/10 | Low | The contract implements a centralized control model with an owner/admin role for critical operations, including pausing transfers and managing freezing (7.3 Access Control, 7.8 Operations). It also… |
| **Upgrades** | 6/10 | Medium | The contract utilizes an `AdminUpgradeabilityProxy` pattern, allowing for future logic upgrades (7.7 Upgrades). However, the upgrade process involves a highly complex and risky `_migratePAXGStorage`… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Zeppelin Os Legacy |
| **Admin** | Timelock — 24h delay |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 78.3% |
| **Top-3 Unlocked** | ⚠️ 98.2% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 8 Informational_

### `M-03` — Complex and Risky Assembly-Based Storage Migration  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_migratePAXGStorage` function directly manipulates storage slots (4, 5, 6, 8, 14, 15) using inline assembly. While intended for migration during upgrades, direct `sload`/`sstore` operations are highly error-prone and bypass Solidity's type safety and storage layout guarantees. A single byte offset error or misunderstanding of the previous storage layout could lead to irreversible data corruption or loss of critical state. This is a high-risk operation, especially in an upgradeable context (7.2 Code Security, 7.7 Upgrades).

**Recommendation:** Thoroughly review and refactor the `_migratePAXGStorage` function. If possible, replace assembly-based slot manipulation with safer, Solidity-native storage management patterns or leverage well-tested migration libraries. If assembly is unavoidable, ensure exhaustive testing, formal verification, and clear documentation of the exact storage layout being migrated from and to. Consider using a `bytes32` constant for each slot to improve readability and reduce magic numbers.


### `L-01` — Truncation Risk in `_setBalanceData`  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `_setBalanceData` function in `BaseStorageV3` casts `uint256` inputs (`balance`, `shares`) to `uint64` using `StorageLib.toUint64Balance` and `StorageLib.toUint64Shares`. If the input `uint256` values exceed `type(uint64).max`, they will be silently truncated. While this might be an intentional design choice for specific tokenomics, it introduces a potential for loss of precision or unexpected behavior if not carefully managed by all calling functions (7.2 Code Security).

**Recommendation:** Implement explicit checks (e.g., `require(balance <= type(uint64).max, "Balance exceeds uint64 limit")`) before casting `uint256` values to `uint64` within `StorageLib.toUint64Balance` and `StorageLib.toUint64Shares`. This ensures that truncation is prevented or explicitly handled, providing clearer error messages and preventing unexpected state changes.


### `I-01` — Legacy Proxy Pattern Used  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses `AdminUpgradeabilityProxy`, which is an older OpenZeppelin proxy pattern. While functional, newer patterns like UUPS (e.g., `UUPSUpgradeable`) offer better decentralization of upgrade control by allowing the implementation contract to manage upgrades, rather than relying on a separate proxy admin contract (7.1 Architecture, 7.7 Upgrades).

**Recommendation:** Consider migrating to a UUPS proxy pattern in future upgrades. UUPS proxies allow the implementation contract to manage its own upgrades, which can simplify the upgrade process and potentially enhance decentralization by removing the need for a separate proxy admin address to initiate upgrades.


### `I-02` — Critical Storage Collision: Freezing Mechanism Overwrites `supplyControllerDeprecated`  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `PAXG` contract defines `_PAXG_FROZEN_SLOT = 7` for its custom freezing mechanism, which uses inline assembly (`sstore(slot, 1)`/`sstore(slot, 0)`). However, in the inherited `BaseStorageV3` contract, storage slot 7 is occupied by the `address public supplyControllerDeprecated;` variable. This means that any call to `_freeze` or `_unfreeze` will directly overwrite or read from the `supplyControllerDeprecated` variable, leading to severe data corruption, unexpected behavior, and potential loss of critical state or control. This is a direct and unmitigated storage collision (7.2 Code Security, 7.7 Upgrades).

**Recommendation:** Immediately rectify the storage collision. The `_PAXG_FROZEN_SLOT` must be changed to a slot that is guaranteed to be unused and will not collide with any current or future inherited storage variables. A safer approach would be to use Solidity's native `mapping(address => bool) internal frozenAddresses;` and ensure it's placed at a non-colliding slot, avoiding direct assembly for this purpose.


### `I-03` — Inconsistent Freezing Mechanisms and Deprecated Storage  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract exhibits an inconsistent approach to address freezing. `PAXG` implements its own freezing logic using `_PAXG_FROZEN_SLOT` (which critically collides with `supplyControllerDeprecated`). Simultaneously, `BaseStorageV3` defines a `mapping(address => bool) internal frozen;` at slot 6, along with `_isFrozen` and `_setFrozen` functions that operate on it. Although `_migratePAXGStorage` clears slot 6, the continued presence of these functions and the `frozen` mapping creates ambiguity and could lead to misinterpretation or accidental use of the deprecated freezing mechanism, resulting in inconsistent state or une

**Recommendation:** Consolidate the freezing logic into a single, well-defined mechanism. Remove or clearly mark as `internal pure` or `private` any deprecated freezing functions or storage variables that are no longer intended for use. Ensure that all parts of the system consistently refer to the intended freezing state. If `BaseStorageV3`'s `frozen` mapping is truly deprecated, its functions (`_isFrozen`, `_setFrozen`) should be removed or overridden to revert.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 33.6% of supply. What remains: 33.6% in wallets, 0.0% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as PAX Gold (PAXG), market cap $1.8B, rank #54. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $28.7M (DexScreener, all pools). 24h trading volume $420K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — a timelock with a 24h delay — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Gold. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: a timelock with a 24h delay. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $28.7M of DEX liquidity across 21 pools. Launch: 2273 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4580...af78`](https://etherscan.io/address/0x45804880de22913dafe09f4980848ece6ecbaf78) |
| **Network** | Ethereum |
| **Price** | $4,476.3600 |
| **24h Volume** | $420.0K |
| **Liquidity** | $16.11M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 6y |
| **Top-10 Holders** | 33.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 71 buys / 75 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x9c4fe5ffd9a9fc5678cfbd93aa2d4fd684b67c4c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/paxos-gold-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
