---
token: Shiro Neko
ticker: SHIRO
network: ethereum
risk_score: 28
status: low
date: 2026-09-13
---

# Shiro Neko (SHIRO) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/shiro-neko-eth)

---

## Audit Summary

The ShiroToken contract implements an ERC20 token with several anti-bot and anti-whale mechanisms, including transfer cooldowns, limits, and an external verifier. The contract exhibits a high degree of centralization, relying heavily on owner privileges for critical operations and parameter management. Key risks include a critical dependency on an external verifier, irreversible configuration of AMM pairs and routers, and potential reentrancy in the owner's token withdrawal function. The contract is not upgradeable.

> **Final Recommendation:** It is highly recommended to review the `IVerifier` contract's security and ensure its integrity, as it is a critical external dependency. Consider implementing a multi-signature wallet for the `owner` role to mitigate centralization risks and enhance security for critical operations. For the `withdrawStuckTokens` function, implement a reentrancy guard or use a pull-over-push pattern for ETH withdrawals to protect against potential reentrancy. Evaluate the necessity of irreversible AMM/router configurations and consider adding functionality for the owner to update or remove these if needed for future flexibility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes Solidity 0.8.28, benefiting from built-in overflow/underflow checks. Standard OpenZeppelin libraries are used for ERC20 and Ownable functionalities, enhancing code security… |
| **Governance / Economics** | 6/10 | Medium | The ShiroToken contract exhibits significant centralization, with the `owner` having extensive control over critical parameters such as `limitsEnabled`, `cooldownEnabled`, `isExcludedFromLimits`… |
| **Upgrades** | 9/10 | Low | The ShiroToken contract is not designed to be upgradeable. It does not implement any proxy patterns (e.g., UUPS, Transparent, Beacon). Therefore, there are no upgrade-specific risks (7.7). Any… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.9% (≈ permanent lock) |
| **LP Locked** | 99.9% — Null Address |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium_

### `C-01` — Critical External Dependency on IVerifier  *(Severity: Critical · Status: Unresolved)*

The `_transfer` function critically relies on an external `IVerifier` contract for authorization during transfers (`verifier.verify(from, to)`). If the `IVerifier` contract is compromised, malicious, or malfunctions, it could arbitrarily block legitimate transfers or allow unauthorized ones, leading to a complete breakdown of the token's transfer mechanism. This represents a single point of failure for the entire token system (7.6).

**Recommendation:** Thoroughly audit the `IVerifier` contract for vulnerabilities. Implement robust monitoring for the `IVerifier` contract's behavior. Consider adding a mechanism for the owner to pause transfers or replace the `IVerifier` contract in an emergency, or to disable the verification requirement if the verifier becomes unresponsive or malicious. Ensure the `IVerifier` contract's access control and upgradeability are secure.


### `H-01` — High Centralization of Control by Owner  *(Severity: High · Status: Unresolved)*

The `owner` role, protected by OpenZeppelin's `Ownable` contract, possesses extensive control over critical contract parameters and functionalities. This includes enabling/disabling transfer limits and cooldowns, excluding addresses from limits, setting AMM pairs and routers, and marking addresses as bots. This high degree of centralization introduces significant trust assumptions and potential for abuse or single point of failure if the owner's private key is compromised (7.5, 7.8).

**Recommendation:** Consider migrating ownership to a multi-signature wallet (e.g., Gnosis Safe) to distribute control and require multiple approvals for critical operations. Implement a timelock for sensitive owner actions to provide a window for community review or emergency intervention. Clearly communicate the extent of owner privileges to token holders.


### `H-02` — Irreversible AMM Pair and Router Configuration  *(Severity: High · Status: Unresolved)*

The `setAutomatedMarketMakerPair` and `setRouter` functions include a `require` statement (`require(!automatedMarketMakerPairs[account], AMMAlreadySet());` and `require(!routers[account], RouterAlreadySet());`) that prevents an address from being set as an AMM pair or router if it has already been configured. This means once an address is marked as an AMM pair or router (by setting `value` to `true`), it cannot be unset or changed. This design limits flexibility and could lead to issues if a configured AMM or router becomes deprecated, compromised, or needs to be updated (7.4).

**Recommendation:** Remove the `require` statements that prevent re-setting AMM pairs or routers. This would allow the owner to update or remove configurations as needed, providing greater flexibility and adaptability to future changes in the DeFi ecosystem. Alternatively, implement a separate function to remove or replace existing configurations.


### `M-01` — Potential Reentrancy in `withdrawStuckTokens` (Owner Risk)  *(Severity: Medium · Status: Unresolved)*

The `withdrawStuckTokens` function, when withdrawing ETH (`tkn == ZERO_ADDRESS`), uses a low-level `call{value: amount}("")` to send ETH to `msg.sender`. If `msg.sender` (the owner) is a malicious contract, it could potentially reenter this function before the contract's balance is updated, leading to a reentrancy attack against the owner's funds. While this primarily affects the owner, it's a common vulnerability pattern (7.2).

**Recommendation:** Implement the Checks-Effects-Interactions pattern by setting `amount = 0` or updating the contract's state *before* the external call. Alternatively, use OpenZeppelin's `ReentrancyGuard` or a pull-over-push pattern for withdrawals to prevent reentrant calls.


### `M-02` — `tx.origin` Usage for Exclusion and Cooldown  *(Severity: Medium · Status: Unresolved)*

The contract uses `tx.origin` in the constructor for `_excludeFromLimits` and within the `_transfer` function for `_holderLastTransferBlock` and `isBot` checks. While `tx.origin` is not used for direct authorization in a way that would enable a critical phishing attack (e.g., `require(tx.origin == owner)`), its general use can be a vector for phishing attacks where a user is tricked into interacting with a malicious contract that then calls the legitimate contract. In such a scenario, `tx.origin` would still refer to the user's EOA, potentially bypassing some intended restrictions if the malicious contract is not itself excluded (7.2).

**Recommendation:** While the current usage is less critical, it's generally recommended to avoid `tx.origin` where possible. For `_holderLastTransferBlock` and `isBot` checks, consider using `msg.sender` instead of `tx.origin` if the intent is to track the direct caller. For exclusions, ensure that any contract interacting with the token is also properly excluded if needed.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb0ac...e058`](https://etherscan.io/address/0xb0ac2b5a73da0e67a8e5489ba922b3f8d582e058) |
| **Network** | Ethereum |
| **Price** | $0. |
| **24h Volume** | $152.3K |
| **Liquidity** | $124.9K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 55.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 207 buys / 143 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xd293d05e83035a757d510e2a5ebfe705c4f05b1f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/shiro-neko-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-13*
