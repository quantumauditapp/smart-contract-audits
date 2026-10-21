---
token: Cheems
ticker: CHEEMS
network: bsc
risk_score: 0
status: low
date: 2026-09-20
---

# Cheems (CHEEMS) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cheems-bsc)

---

## Audit Summary

The ERC20Mintable contract implements a standard ERC20 token with ownership and a designated minter role. The code is based on OpenZeppelin contracts, demonstrating good practices for security and adherence to standards. Key functionalities include token transfers, allowances, and a mechanism for the owner to set a minter who can then airdrop the initial token supply. While the contract exhibits a high degree of centralization through the owner and minter roles, this is a common design pattern for simple utility tokens and is clearly defined. No critical or high-severity technical vulnerabilities were identified.

> **Final Recommendation:** While the contract is technically sound, the high degree of centralization through the owner and minter roles necessitates robust operational security. Implement multi-signature wallets for the owner and minter addresses to mitigate the risk of single-point-of-failure. Ensure secure key management practices are in place for all privileged accounts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract is built upon well-audited OpenZeppelin libraries (Context, Ownable, ERC20), which significantly reduces the risk of common vulnerabilities (7.2 Code Security). Solidity version 0.8.6… |
| **Governance / Economics** | 6/10 | Medium | The contract features a highly centralized access control model (7.3 Access Control). The `owner` has significant power, including the ability to transfer ownership, set the `minter` address, and… |
| **Upgrades** | 10/10 | Low | The provided contract is not designed as an upgradeable proxy (7.7 Upgrades). Therefore, there are no upgrade-specific risks such as storage collisions, initializer issues, or proxy-logic mismatches.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.1% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address, TeamFinance |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 2 Informational_

### `M-01` — Centralized Control by Owner and Minter  *(Severity: Medium · Status: Unresolved)*

The contract grants significant power to the `owner` and the designated `minter` address. The `owner` can transfer ownership, set the `minter`, and withdraw any ERC20 tokens from the contract. The `minter` has exclusive control over the `airdrop` function, which is the sole mechanism for distributing the initial token supply. This centralization means that a compromise of either the owner's or minter's private key could lead to unauthorized token distribution or asset drain.

**Recommendation:** Consider implementing a multi-signature wallet for the `owner` and `minter` roles to enhance security and distribute control. For critical operations like `setMinter` or `transferOwnership`, a time-lock mechanism could be added to provide a window for community or governance intervention in case of a malicious action.


### `L-01` — Initial Supply Minted to Contract Address  *(Severity: Low · Status: Unresolved)*

The constructor mints the entire initial token supply (`_total`) to the contract's own address (`address(this)`). This design choice means that no tokens are initially assigned to the deployer or any other address. All subsequent distribution of these tokens relies entirely on the `airdrop` function, which is controlled by the `minter`. If the `minter` is not set correctly or becomes inaccessible, the initial supply could be locked within the contract.

**Recommendation:** Ensure that the `minter` address is set immediately after deployment to a trusted and secure entity. Clear documentation should be provided to users explaining this distribution mechanism and the role of the `minter` in releasing the initial supply.


### `I-01` — Owner's Ability to Withdraw Arbitrary ERC20 Tokens  *(Severity: Informational · Status: Unresolved)*

The `withdraw` function allows the `onlyOwner` to transfer any specified ERC20 token from the contract's balance to an arbitrary recipient. While this function is typically included as an emergency measure to recover accidentally sent tokens, it also means that if the contract were to hold other valuable ERC20 tokens (e.g., from user deposits in a future integration), the owner would have the unilateral ability to drain them.

**Recommendation:** Acknowledge the power granted to the owner by this function. If the contract's scope expands to hold other valuable assets, consider implementing a more granular or time-locked withdrawal mechanism, or requiring multi-signature approval for such operations.


### `I-02` — No External General Minting Function  *(Severity: Informational · Status: Unresolved)*

Despite the contract being named `ERC20Mintable`, the internal `_mint` function is only called once in the constructor to establish the initial supply. There is no external function provided to mint additional tokens beyond this initial amount. The `airdrop` function only distributes existing tokens from the contract's balance. This implies a fixed total supply after deployment, which might be contrary to user expectations based on the contract name.

**Recommendation:** Clarify the token's supply mechanism in documentation. If the intent is a fixed supply after initial distribution, consider renaming the contract to better reflect this, or explicitly state that no further minting is possible post-deployment. If future minting is desired, an `onlyMinter` or `onlyOwner` function to call `_mint` would be required.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0df0...b413`](https://bscscan.com/address/0x0df0587216a4a1bb7d5082fdc491d93d2dd4b413) |
| **Network** | BNB Chain |
| **Price** | $0.00000052 |
| **24h Volume** | $63.5K |
| **Liquidity** | $5.22M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 2y |
| **Top-10 Holders** | 79.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 360 buys / 392 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x38231d4ef9d33ebea944c75a21301ff6986499c3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cheems-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-20*
