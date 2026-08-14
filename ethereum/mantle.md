---
token: Mantle
ticker: MNT
network: ethereum
risk_score: 60
status: high
date: 2026-08-14
---

# Mantle (MNT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 60/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mantle-eth)

---

## Audit Summary

The L1MantleToken contract implements an upgradeable ERC-20 token with burnable, permit, and voting functionalities. It features a controlled minting mechanism with a time interval and a dynamic cap. The contract leverages OpenZeppelin's battle-tested libraries and follows best practices for upgradeability and access control, with critical functions protected by a robust multisig ownership structure. While the technical implementation is strong, the centralized control over minting and mint cap adjustments by the owner multisig introduces a notable economic risk.

> **Final Recommendation:** Ensure the multisig controlling minting and parameter changes operates with full transparency and community oversight. Regularly review the minting policy and communicate any changes to the token supply or mint cap clearly to stakeholders. Maintain vigilance over the multisig signers and their security practices to prevent unauthorized access to critical functions and uphold the integrity of the token supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The L1MantleToken contract is built upon well-audited OpenZeppelin libraries, ensuring a strong foundation for ERC-20 functionality, burning, and access control (7.3 Access Control). Solidity version… |
| **Governance / Economics** | 2/10 | High | The contract's economic model centers around a controlled minting mechanism, where new tokens can be minted by the owner, which is a robust 6/14 multisig (7.4 Economic). This centralization of… |
| **Upgrades** | 1/10 | High | The contract utilizes the TransparentUpgradeableProxy pattern, with the implementation logic residing in L1MantleToken. The upgrade process is secured by an OpenZeppelin ProxyAdmin, which is owned by… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Timelock |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 2 Low_

### `H-01` — Centralized Minting Authority  *(Severity: High · Status: Unresolved)*

The `mint` function is protected by the `onlyOwner` modifier, meaning only the contract owner can mint new tokens. While the owner is a robust 6/14 multisig, this design centralizes the control over the token's supply, giving the multisig significant power to inflate the token supply. This is a fundamental design choice but represents a high-impact point of control (7.3 Access Control, 7.4 Economic).

**Recommendation:** Acknowledge this as a design decision. Ensure the multisig governance process for minting is transparent, well-documented, and subject to community oversight. Consider implementing a timelock for minting operations or a more decentralized minting mechanism if future protocol evolution allows.


### `M-01` — Owner's Control Over Mint Cap Numerator  *(Severity: Medium · Status: Unresolved)*

The `setMintCapNumerator` function, which determines the maximum percentage of total supply that can be minted in an interval, is callable only by the owner (multisig). Although there's an upper bound (`MINT_CAP_MAX_NUMERATOR`), the owner can adjust this value at any time. Frequent or unexpected changes to this parameter could impact market perception and token economics (7.5 Governance, 7.4 Economic).

**Recommendation:** Implement a timelock for changes to `mintCapNumerator` to provide transparency and allow stakeholders to react. Clearly communicate any proposed changes to this parameter well in advance. Consider a more decentralized governance mechanism for such critical parameter adjustments in the future.


### `L-01` — Reliance on `block.timestamp` for `nextMint`  *(Severity: Low · Status: Unresolved)*

The `nextMint` timestamp is calculated and updated using `block.timestamp`. While `block.timestamp` is generally reliable, miners can manipulate it within a small range (up to 900 seconds on Ethereum). For a `MIN_MINT_INTERVAL` of 365 days, this manipulation is negligible and does not pose a significant risk of accelerating the minting schedule (7.2 Code Security).

**Recommendation:** Given the very long `MIN_MINT_INTERVAL`, the impact of `block.timestamp` manipulation is minimal. No immediate action is required, but for future designs involving shorter time intervals, `block.number` or an oracle-based timestamp might be considered for greater robustness.


### `L-02` — Missing Zero Address Check for `_recipient` in `mint`  *(Severity: Low · Status: Unresolved)*

The `mint` function does not explicitly check if the `_recipient` address is `address(0)`. While OpenZeppelin's underlying `_mint` function would revert if `to` is `address(0)`, an explicit check in the `mint` function would provide clearer intent and a more specific error message, preventing accidental burning of tokens to the zero address (7.2 Code Security).

**Recommendation:** Add an explicit check at the beginning of the `mint` function: `if (_recipient == address(0)) revert MantleToken_ImproperlyInitialized();` or a custom error for zero address recipients.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3c3a...f354`](https://etherscan.io/address/0x3c3a81e81dc49a522a592e7622a7e711c06bf354) |
| **Network** | Ethereum |
| **Price** | $0.4437 |
| **24h Volume** | $118.7K |
| **Liquidity** | $2.96M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 86.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 54 buys / 61 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x9aac67deef711d438ad711ae495b8cb43a6ee1a8)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mantle-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*
