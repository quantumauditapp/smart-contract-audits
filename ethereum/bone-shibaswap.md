---
token: BONE SHIBASWAP
ticker: BONE
network: ethereum
risk_score: 41
status: medium
date: 2026-09-22
---

# BONE SHIBASWAP (BONE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bone-shibaswap-eth)

---

## Audit Summary

The BoneToken contract implements an ERC20 token with Compound-style delegation for governance. It leverages OpenZeppelin contracts for core ERC20 functionality and ownership. The primary risk identified is the centralized minting authority, which allows the owner to control the token supply. Other findings include a theoretical long-term limitation for block numbers and informational notes on checkpointing behavior and lack of a pause mechanism.

> **Final Recommendation:** It is strongly recommended to decentralize control over the `mint` function to mitigate the high economic risk associated with centralized token supply management. This could involve transferring ownership to a robust, community-governed DAO with a timelock, or implementing a fixed supply. Additionally, consider documenting the single-checkpoint-per-block behavior and evaluating the need for an emergency pause mechanism to enhance operational resilience.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The BoneToken contract is built upon battle-tested OpenZeppelin ERC20 and Ownable implementations, providing a solid foundation for token functionality. The custom delegation logic, inspired by… |
| **Governance / Economics** | 4/10 | Medium | The contract's economic model is significantly influenced by the `mint` function, which is controlled by a single owner (H-01). This centralized control over token supply poses a high economic risk… |
| **Upgrades** | 8/10 | Low | The BoneToken contract is not designed to be upgradeable, meaning its logic is immutable once deployed. This eliminates risks associated with proxy patterns or upgrade mechanisms, such as storage… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 50.2% |
| **Top-3 Unlocked** | ⚠️ 98.2% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 2 Informational_

### `H-01` — Centralized Minting Authority  *(Severity: High · Status: Unresolved)*

The `mint` function, protected by `onlyOwner`, allows the contract owner to create an arbitrary amount of new tokens. This introduces a significant centralization risk (7.3 Access Control), as a compromised or malicious owner could inflate the token supply, devaluing existing tokens and impacting the protocol's economy (7.4 Economic). While the owner is an 'Other-Contract', its nature (e.g., multisig, DAO, timelock) is not specified, leaving potential for a single point of failure.

**Recommendation:** Implement a robust governance mechanism (e.g., DAO with timelock) to control the minting function, or define a fixed supply/emission schedule. If the owner is already a robust governance contract, ensure its security and decentralization.


### `L-01` — Theoretical `block.number` Overflow in `safe32`  *(Severity: Low · Status: Unresolved)*

The `safe32` helper function, used to cast `block.number` to `uint32` for checkpoints, includes a `require(n < 2**32)` check (7.2 Code Security). While `block.number` on EVM chains is currently far below this limit, it is a theoretical long-term limitation. If the blockchain were to run for thousands of years, `block.number` could eventually exceed `2**32`, causing transactions involving checkpoints to revert.

**Recommendation:** Consider using `uint64` or `uint256` for `fromBlock` in the `Checkpoint` struct if extreme long-term compatibility (thousands of years) is a critical requirement. For practical purposes on current EVM chains, this is a very low risk.


### `I-01` — Single Checkpoint per Block for Vote Tracking  *(Severity: Informational · Status: Unresolved)*

The `_writeCheckpoint` function updates an existing checkpoint if `checkpoints[delegatee][nCheckpoints - 1].fromBlock == blockNumber` (7.2 Code Security). This design means that for any given delegatee, only one vote balance snapshot is recorded per block. If multiple token transfers or delegation changes affecting the same delegatee occur within the same block, intermediate vote balance changes will not be individually recorded, only the final state at the end of the block. This is a common design pattern for Compound-style voting systems and is generally acceptable, but it's important for users and integrators to understand this behavior.

**Recommendation:** Document this behavior clearly for users and integrators, explaining that vote changes within the same block are coalesced into a single checkpoint.


### `I-02` — Lack of Emergency Pause Mechanism  *(Severity: Informational · Status: Unresolved)*

The `BoneToken` contract does not include a mechanism to pause token transfers or delegation in emergency situations, such as a critical vulnerability discovery or a major external exploit affecting the ecosystem (7.8 Operations). While not strictly a vulnerability, a pause function can provide a crucial safety net for mitigating damage in unforeseen circumstances.

**Recommendation:** Consider implementing a pausable mechanism (e.g., using OpenZeppelin's `Pausable` contract) controlled by a robust governance system. This would allow the community or a trusted entity to temporarily halt operations if necessary.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9813...18d9`](https://etherscan.io/address/0x9813037ee2218799597d83d4a5b6f3b6778218d9) |
| **Network** | Ethereum |
| **Price** | $0.05238 |
| **24h Volume** | $44.6K |
| **Liquidity** | $1.39M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 5y |
| **Top-10 Holders** | 47.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 75 buys / 51 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xefb47fcfcad4f96c83d4ca676842fb03ef20a477)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bone-shibaswap-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*
