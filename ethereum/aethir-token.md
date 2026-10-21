---
token: Aethir Token
ticker: ATH
network: ethereum
risk_score: 75
status: high
date: 2026-09-22
---

# Aethir Token (ATH) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 75/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aethir-token-eth)

---

## Audit Summary

The AethirToken contract, an ERC20Permit implementation, features a whitelisting mechanism for token distribution controlled by an owner multisig. Critical vulnerabilities were identified, including a fundamental flaw in the token transfer mechanism that prevents distribution of minted tokens, and a re-whitelisting vulnerability allowing users to bypass transfer limits. These issues severely impact the token's intended functionality and economic model. Additionally, the contract exhibits high centralization of power with the owner.

> **Final Recommendation:** Immediate action is required to address the critical vulnerabilities identified. The token distribution mechanism must be corrected to enable token transfers, and the re-whitelisting vulnerability in `_afterTokenTransfer` must be patched to prevent unauthorized token acquisition. A thorough review of the token's economic model and access control is recommended to assess the implications of high centralization. Consider implementing a more decentralized distribution strategy or additional safeguards for owner-controlled functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 3/10 | High | The contract utilizes OpenZeppelin's ERC20 and Ownable for foundational security. However, the custom `transferToWhitelisted` function contains a critical logic error by misusing… |
| **Governance / Economics** | 1/10 | High | The token's economic model is highly centralized, with the owner (a multisig wallet) possessing extensive control over the token supply and distribution (7.4 Economic, 7.5 Governance). The owner can… |
| **Upgrades** | 2/10 | High | The AethirToken contract is not designed with upgradeability features, such as a proxy pattern. This means the contract's logic is immutable once deployed, eliminating upgrade-related risks but… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 88.9% |
| **Top-3 Unlocked** | ⚠️ 98.9% |

## Security Findings

_🔴 2 Critical · 🟠 1 High · 🟡 1 Medium_

### `C-01` — Critical Logic Error in Token Distribution (`SafeERC20.safeTransfer(this, ...)` Misuse)  *(Severity: Critical · Status: Unresolved)*

The `transferToWhitelisted` function, intended to distribute tokens from the contract's balance, incorrectly uses `SafeERC20.safeTransfer(this, to, amount)`. `SafeERC20.safeTransfer` is designed for a contract to transfer *another* ERC20 token it holds. To transfer its *own* tokens (which were minted to `address(this)`), the contract must use the internal `_transfer(address(this), to, amount)` function. As implemented, `transferToWhitelisted` will fail to move tokens, effectively locking all minted tokens within the contract and making the token unusable for its intended purpose of distribution.

**Recommendation:** Replace `SafeERC20.safeTransfer(this, to, amount);` with `_transfer(address(this), to, amount);` in the `transferToWhitelisted` function. Ensure that the contract's internal balance is correctly managed for transfers.


### `C-02` — Re-whitelisting/Re-transfer Vulnerability via `_afterTokenTransfer`  *(Severity: Critical · Status: Unresolved)*

The `_afterTokenTransfer` override contains logic that allows whitelisted users to bypass their `allowedAmount` limits. If a whitelisted user sends tokens back to the `AethirToken` contract address, the `_afterTokenTransfer` function reduces their `transferredAmount[from]` and `totalTransferred`. This means a user can receive tokens via `transferToWhitelisted`, send them back to the contract, and then receive more tokens, effectively resetting their `transferredAmount` and exceeding their `allowedAmount`. This breaks the core whitelisting mechanism and can lead to unauthorized token inflation or distribution beyond intended limits.

**Recommendation:** Remove or completely redesign the `_afterTokenTransfer` logic. Transfers *to* the token contract address should generally not affect internal whitelisting state variables like `transferredAmount` or `totalTransferred`. If a burn mechanism is intended, it should be explicit and not tied to general transfers to the contract address.


### `H-01` — Centralized Control and Minting Power  *(Severity: High · Status: Unresolved)*

The `AethirToken` contract grants the `owner` (a multisig wallet) extensive and centralized control over critical functions. The owner can `mint` tokens up to the `MAX_SUPPLY`, `transferToWhitelisted` any amount to whitelisted addresses, and fully manage the whitelisting parameters (`addWhitelisted`, `removeWhitelisted`, `updateWhitelistedMaxAmount`, `updateWhitelistedAddress`). This high degree of centralization means that the integrity of the token supply and distribution relies entirely on the security and good faith of the multisig signers. A compromise of the multisig or malicious intent could lead to significant economic damage or misuse of funds.

**Recommendation:** While a multisig improves security over a single EOA, consider further decentralization or implementing time-locks for critical actions like large mints or significant changes to whitelisting parameters. Explore integrating with a governance module for key decisions, or at minimum, ensure robust operational security procedures for the multisig.


### `M-01` — Unconventional Token Holding Pattern  *(Severity: Medium · Status: Unresolved)*

The `mint` function calls `_mint(address(this), amount)`, which means all newly minted tokens are held by the `AethirToken` contract itself. This is an unusual pattern for an ERC20 token. Typically, tokens are minted to a specific treasury, vesting contract, or the owner's address for subsequent distribution. Holding all tokens within the token contract makes it a single point of failure for distribution (assuming the `transferToWhitelisted` function worked correctly). This design choice increases the contract's complexity and reliance on the owner's actions for any token movement.

**Recommendation:** Consider revising the minting strategy. Mint tokens directly to a dedicated treasury contract or a controlled distribution contract. This separates the token logic from the token holding and distribution responsibilities, improving modularity and potentially security.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbe0e...226b`](https://etherscan.io/address/0xbe0ed4138121ecfc5c0e56b40517da27e6c5226b) |
| **Network** | Ethereum |
| **Price** | $0.005491 |
| **24h Volume** | $168.0K |
| **Liquidity** | $354.4K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 2y |
| **Top-10 Holders** | 78.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 220 buys / 215 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xd31d41dffa3589bb0c0183e46a1eed983a5e5978)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aethir-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*
