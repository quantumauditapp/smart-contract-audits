---
token: JPY Coin
ticker: JPYC
network: ethereum
risk_score: 88
status: critical
date: 2026-09-18
---

# JPY Coin (JPYC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 88/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jpy-coin-eth)

---

## Audit Summary

The FiatTokenV1 contract serves as the implementation for an ERC-20 compatible token, incorporating features like pausing, blocklisting, minting/burning, and UUPS upgradeability. The contract demonstrates robust access control for critical functions and adheres to Solidity 0.8.x's default overflow/underflow protection. However, a significant issue was identified where the contract blocklists itself, preventing the rescue of its own tokens if accidentally sent to the contract address. Other findings include limitations in EIP-712 versioning during upgrades and the inherent centralization of control, albeit mitigated by a multisig owner.

> **Final Recommendation:** Address the high-severity issue of self-blocklisting to ensure that FiatTokenV1 tokens accidentally sent to the contract can be rescued. Review the EIP-712 versioning strategy to allow for potential updates during future upgrades without requiring a full re-initialization. Continue to enforce robust operational security for all privileged roles, especially the multisig owner, to safeguard against centralized control risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract exhibits good technical design, adhering to ERC-20 standards and utilizing Solidity 0.8.11 for built-in overflow/underflow protection (7.2 Code Security). Access control mechanisms for… |
| **Governance / Economics** | 1/10 | High | The economic model centers around a controlled supply via minters, managed by a `minterAdmin` (7.4 Economic). While the `owner` role holds significant power over critical functions such as pausing… |
| **Upgrades** | 1/10 | High | The contract implements the UUPS upgradeability pattern, ensuring future flexibility and maintainability (7.7 Upgrades). The `initialize` function correctly uses an `initializedVersion` check to… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Uups |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — FiatTokenV1 Tokens Locked Due to Self-Blocklisting  *(Severity: High · Status: Unresolved)*

The `initialize` function explicitly blocklists the contract's own address by setting `blocklisted[address(this)] = 1;`. This action prevents any `_transfer` operation where the `from` address is the contract itself, due to the `notBlocklisted(from)` modifier. Consequently, if FiatTokenV1 tokens are accidentally sent to the FiatTokenV1 contract address, the `rescueERC20` function (inherited from `Rescuable`) will fail when attempting to transfer these tokens out, as it would call `_transfer` with `from = address(this)`. This leads to the permanent locking of any FiatTokenV1 tokens sent to the contract address.

**Recommendation:** Remove the line `blocklisted[address(this)] = 1;` from the `initialize` function. Instead, implement a specific check within the `_transfer` function to prevent transfers *to* `address(this)` if the intent is to prevent tokens from being held by the contract, or ensure that the `rescueERC20` function explicitly bypasses the blocklist check for `address(this)` when rescuing its own token.


### `M-01` — Hardcoded EIP-712 Version Limits Upgrade Flexibility  *(Severity: Medium · Status: Unresolved)*

The `VERSION` string used for the EIP-712 domain separator is hardcoded to '1' in the `initialize` function. While the `initialize` function prevents re-initialization, this means that if a future upgrade requires changing the token's `name` or the EIP-712 `VERSION` (e.g., for a major protocol revision), the `DOMAIN_SEPARATOR` cannot be updated. This could lead to incompatibility with existing signed messages or limit branding flexibility in future versions.

**Recommendation:** Consider making the EIP-712 `VERSION` configurable by the owner or `minterAdmin` through a dedicated function, or ensure that future upgrade plans account for the immutability of this parameter. If the token name is expected to remain constant, this issue's impact is reduced.


### `L-01` — Centralized Control by Owner Role  *(Severity: Low · Status: Unresolved)*

The `owner` role possesses significant control over critical contract functions, including the ability to pause/unpause the contract, blocklist/unblocklist addresses, update the `minterAdmin`, and initiate contract upgrades. While the prefill indicates the owner is a multisig, this still represents a centralized point of control. A compromise or malicious action by the multisig signers could lead to severe consequences for the protocol and its users.

**Recommendation:** Maintain strict operational security practices for the multisig wallet controlling the `owner` role. Consider exploring further decentralization strategies for critical governance functions in future iterations, such as time-locks for sensitive operations or community-driven governance mechanisms.


### `I-01` — Storage Layout Management for UUPS Upgrades  *(Severity: Informational · Status: Unresolved)*

As a UUPS upgradeable contract, `FiatTokenV1` relies on careful management of its storage layout across different implementation versions. Adding, removing, or reordering state variables in future contract upgrades without proper planning and adherence to UUPS storage guidelines can lead to storage collisions, data corruption, and unexpected behavior in the upgraded contract.

**Recommendation:** Establish and strictly follow a robust storage layout management strategy for all future upgrades. Utilize tools like `hardhat-upgrades` or `openzeppelin-upgrades` to detect storage layout incompatibilities during development and testing. Document the storage slot usage for all state variables to aid in future upgrade planning.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe7c3...3c29`](https://etherscan.io/address/0xe7c3d8c9a439fede00d2600032d5db0be71c3c29) |
| **Network** | Ethereum |
| **Price** | $0.00643 |
| **24h Volume** | $563.0K |
| **Liquidity** | $63.0K |
| **Volume / Liquidity** | 8.9× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 368 buys / 353 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xe00cdf9dcd96fb1bcf834ee5187332210611974d90f14cc6ab632613793d0c8d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jpy-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-18*
