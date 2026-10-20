---
token: Akita
ticker: AKITA
network: ethereum
risk_score: 41
status: medium
date: 2026-09-27
---

# Akita (AKITA) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 41/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/akita-eth)

---

## Audit Summary

The Akita contract implements a standard ERC20 token with OpenZeppelin's ERC20 and ERC20Permit functionalities. It includes a recovery mechanism for accidentally sent ETH and ERC20 tokens, controlled by a single 'recovery' address. While the core token logic is robust due to OpenZeppelin's battle-tested libraries, the centralized control over recovery functions introduces a significant access control risk.

> **Final Recommendation:** It is strongly recommended to secure the `recovery` address with a robust multi-signature wallet solution to mitigate the single point of failure risk. This will require multiple trusted parties to approve critical operations such as recovering funds or changing the recovery address, significantly enhancing the security posture of the contract's operational control. Additionally, consider implementing a mechanism for recovering other token standards (e.g., ERC-721, ERC-1155) if there's a possibility of them being accidentally sent to the contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Akita contract demonstrates strong technical foundations by inheriting from battle-tested OpenZeppelin ERC20 and ERC20Permit implementations, ensuring robust token functionality (7.2 Code… |
| **Governance / Economics** | 1/10 | High | The economic model is straightforward, with a fixed total supply minted to a single receiver at deployment, aligning with standard ERC20 tokenomics (7.4 Economic). There is no formal on-chain… |
| **Upgrades** | 6/10 | Medium | The Akita contract is not designed with an upgradeability pattern (7.7 Upgrades), meaning its logic is immutable once deployed. This eliminates risks associated with proxy implementation bugs or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control of Recovery Functions  *(Severity: High · Status: Unresolved)*

The `recovery` address has sole control over critical functions: `recoverETH()`, `recoverERC20()`, and `updateRecovery()`. This means a single external owned account (EOA) or a single point of failure controls the ability to withdraw any ETH or ERC20 tokens accidentally sent to the contract, and can also transfer this control to another address. If this `recovery` address is compromised, all funds held by the contract (e.g., from accidental transfers) could be permanently lost or stolen by an attacker (7.3 Access Control, 7.8 Operations).

**Recommendation:** Implement a multi-signature wallet (e.g., Gnosis Safe) for the `recovery` address. This would require multiple trusted parties to authorize any recovery operation or change to the recovery address, significantly reducing the risk associated with a single point of failure.


### `L-01` — Lack of Time-Lock or Delay for Critical Operations  *(Severity: Low · Status: Unresolved)*

The `updateRecovery()` function allows the `recovery` address to instantly change itself to a new address. While controlled by `onlyRecovery`, an immediate change without a time-lock or delay period could be problematic if the `recovery` address is compromised. An attacker could quickly change the recovery address before the legitimate owner has a chance to react, potentially locking out the original owner from future recovery operations (7.3 Access Control, 7.8 Operations).

**Recommendation:** Consider adding a time-lock mechanism to the `updateRecovery()` function. This would introduce a delay (e.g., 24-72 hours) between initiating a recovery address change and its actual activation, providing a window for detection and intervention in case of a compromised `recovery` key.


### `I-01` — Limited Recovery Scope for Non-ERC20 Tokens  *(Severity: Informational · Status: Unresolved)*

The contract includes functions to recover accidentally sent ETH (`recoverETH`) and ERC20 tokens (`recoverERC20`). However, there is no mechanism to recover other types of tokens, such as ERC-721 (NFTs) or ERC-1155 tokens, if they are mistakenly sent to the contract address. Any such tokens would be permanently locked within the contract (7.4 Economic, 7.8 Operations).

**Recommendation:** Assess the likelihood of non-ERC20 tokens being accidentally sent to the contract. If this is a significant concern, consider implementing additional recovery functions for other token standards (e.g., `recoverERC721`, `recoverERC1155`) or explicitly documenting that such assets are unrecoverable.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x7def...56be`](https://etherscan.io/address/0x7def4573628021500c3207994935a51801fb56be) |
| **Network** | Ethereum |
| **Price** | $0.01341 |
| **24h Volume** | $97.9K |
| **Liquidity** | $122.5K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 89.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 132 buys / 102 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x9845376f915509168cbfa8d9481f707bd5a7cc760f349a5e7fb7a0dfad465b2b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/akita-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-27*
