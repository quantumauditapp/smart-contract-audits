---
token: Coinbase Wrapped XRP
ticker: CBXRP
network: base
risk_score: 57
status: high
date: 2026-07-24
---

# Coinbase Wrapped XRP (CBXRP) — Smart Contract Security Analysis | Base

> **Risk Score: 57/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-xrp-base)

---

## Audit Summary

The FiatTokenV2_2 contract serves as the implementation logic for a fiat-backed ERC-20 token, deployed via a ZeppelinOS legacy proxy. The contract includes features such as blacklisting, pausing, and EIP-712 signed transactions (permit, transferWithAuthorization). While the core logic appears robust for its intended purpose, the audit identified significant centralization risks due to EOA control over critical administrative and upgrade functions. Additionally, a custom bit-packed storage solution for balances and blacklist states introduces complexity and potential upgrade risks.

> **Final Recommendation:** It is strongly recommended to transition critical administrative roles (owner, pauser, blacklister) and the proxy admin role from single EOAs to a robust multi-signature wallet or a well-tested DAO governance system. This would significantly reduce the risk of a single point of failure and enhance the overall security posture of the protocol. Additionally, for future upgrades, extreme caution must be exercised with the custom bit-packed storage layout to prevent data corruption.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 5/10 | Medium | The contract demonstrates a robust implementation of EIP-712 signed transactions, including an anti-front-running check for `receiveWithAuthorization`. The `_chainId()` function correctly uses the… |
| **Governance / Economics** | 1/10 | High | The token design is highly centralized, with critical administrative functions such as minting, burning, pausing, and blacklisting controlled by a single EOA owner (7.3 Access Control, 7.5… |
| **Upgrades** | 1/10 | High | The contract utilizes a ZeppelinOS legacy proxy pattern, which is a known and understood upgrade mechanism. The `initializeV2_2` function correctly prevents re-initialization (7.7 Upgrades). However… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Zeppelin Os Legacy |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 80.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Upgrade Control by EOA Admin  *(Severity: High · Status: Unresolved)*

The proxy contract's upgradeability is controlled by a single External Owned Account (EOA) at `0x7fec9bc54c94d4ed5d98bcfadaebcbc55aa0c24e`. If this EOA's private key is compromised, an attacker could unilaterally upgrade the contract to a malicious implementation, potentially leading to loss of funds or complete control over the token supply.

**Recommendation:** Migrate the proxy admin role from a single EOA to a robust multi-signature wallet (e.g., Gnosis Safe) with a high threshold of signers, or a time-locked governance contract. This distributes control and adds a layer of security against a single point of failure.


### `H-02` — Centralized Administrative Control by EOA Owner  *(Severity: High · Status: Unresolved)*

Critical administrative functions such as minting, burning, pausing, and blacklisting are controlled by a single EOA owner at `0x9c4955ad8b8ec15aea30fa7d751a59699c179144`. A compromise of this EOA would grant an attacker the ability to freeze user funds, manipulate token supply, or blacklist legitimate users, severely impacting the protocol's integrity and user trust.

**Recommendation:** Transfer ownership of critical administrative roles to a multi-signature wallet or a decentralized autonomous organization (DAO) governance system. Implement a timelock for sensitive operations to provide a delay for review and potential intervention.


### `M-01` — Complex Custom Bit-Packed Storage for Balances and Blacklisting  *(Severity: Medium · Status: Unresolved)*

The contract uses a custom storage pattern where `balanceAndBlacklistStates` stores both the account balance (lower 255 bits) and blacklist status (highest bit) in a single `uint256`. While this saves storage slots, it is a non-standard and complex design that increases the risk of subtle bugs, especially during future upgrades or if the bit manipulation logic is not perfectly maintained. Incorrect handling could lead to balance corruption or unintended blacklist states.

**Recommendation:** Ensure rigorous testing and formal verification of any future contract upgrades that interact with `balanceAndBlacklistStates`. Document the storage layout meticulously. Consider refactoring to separate storage variables for balances and blacklist status in a future major upgrade, if gas costs allow, to improve clarity and reduce complexity.


### `L-01` — Older Solidity Compiler Version  *(Severity: Low · Status: Unresolved)*

The contract is compiled with Solidity version 0.6.12. While this version is stable, it predates several security enhancements and optimizations introduced in newer versions, particularly Solidity 0.8.0+, which includes built-in overflow/underflow checks for arithmetic operations by default.

**Recommendation:** Consider upgrading to a more recent and actively maintained Solidity compiler version (e.g., 0.8.x) in future contract iterations. This would leverage the latest compiler features, bug fixes, and built-in safety mechanisms, potentially reducing the attack surface.


### `I-01` — Self-Blacklisting of Contract Address During Initialization  *(Severity: Informational · Status: Unresolved)*

The `initializeV2_2` function explicitly blacklists `address(this)` (the contract itself) after migrating deprecated blacklist accounts. This means the token contract address cannot hold or transfer tokens, as it will always be considered blacklisted.

**Recommendation:** While this might be an intentional design choice to prevent tokens from being locked in the contract, it's an unusual pattern. Ensure this behavior is clearly documented and understood by all stakeholders to avoid confusion or unexpected issues if tokens are accidentally sent to the contract address.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcb58...a4af`](https://basescan.org/address/0xcb585250f852c6c6bf90434ab21a00f02833a4af) |
| **Network** | Base |
| **Price** | $1.0560 |
| **24h Volume** | $1.28M |
| **Liquidity** | $371.2K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 84.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 875 buys / 771 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xb90fe999be6869af0afc557dccfbe169ea3403d6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-xrp-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-24*
