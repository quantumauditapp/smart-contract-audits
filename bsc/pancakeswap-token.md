---
token: PancakeSwap Token
ticker: CAKE
network: bsc
risk_score: 72
status: critical
date: 2026-08-11
---

# PancakeSwap Token (CAKE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 72/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pancakeswap-token-bsc)

---

## Audit Summary

The audit of the provided BEP20 token contract identified a critical functional flaw: the token's total supply is uninitialized and there is no mechanism to mint new tokens, rendering the contract unusable for transfers. Additionally, the contract employs a standard Ownable pattern, centralizing administrative control, and exhibits a low-severity front-running risk common to ERC-20 allowance mechanisms. The contract otherwise demonstrates good code quality and utilizes established libraries for secure arithmetic and address interactions.

> **Final Recommendation:** It is critical to address the uninitialized total supply by implementing a minting mechanism, either in the constructor for an initial supply or through an owner-controlled mint function. Without this, the token contract is non-functional. For administrative control, consider enhancing the owner's security by using a multi-signature wallet or a time-locked governance contract, especially given the owner is an OZ_ProxyAdmin, which suggests a more robust setup might be intended.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract demonstrates strong technical foundations by utilizing the SafeMath library (7.2 Code Security) to prevent integer overflows/underflows and the Address library for secure external… |
| **Governance / Economics** | 1/10 | High | The contract implements the Ownable pattern (7.3 Access Control), centralizing administrative control to a single owner address, which is noted to be an OZ_ProxyAdmin externally. This introduces a… |
| **Upgrades** | 2/10 | High | The provided contract is not designed as an upgradeable proxy (7.7 Upgrades) and does not contain any upgrade-specific logic. Therefore, direct upgrade safety concerns for this specific contract are… |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Uninitialized Total Supply and No Minting Mechanism  *(Severity: Critical · Status: Unresolved)*

The `_totalSupply` state variable is initialized to 0 in the contract and there are no functions (e.g., `_mint` or an initial supply in the constructor) provided in the code to increase it. Consequently, the `totalSupply()` function will always return 0, and the `_balances` mapping will remain empty. This renders the token untransferable and completely unusable, as no tokens can ever exist or be moved.

**Recommendation:** Implement a mechanism to initialize and/or increase the `_totalSupply`. This could involve minting an initial supply in the constructor or adding an owner-controlled `mint` function to create new tokens and assign them to specific addresses.


### `M-01` — Centralized Control by Owner  *(Severity: Medium · Status: Unresolved)*

The contract utilizes the `Ownable` pattern, granting a single `owner` address exclusive control over critical administrative functions such as `transferOwnership` and `renounceOwnership`. While common, this introduces a single point of failure. If the owner's private key is compromised, an attacker could gain full administrative control over the contract. The prefill indicates the owner is an 'OZ_ProxyAdmin', which suggests a more robust external governance mechanism might be in place, but from the contract's perspective, it's a single address.

**Recommendation:** Consider implementing a multi-signature wallet for the owner address or integrating a time-locked governance mechanism for critical operations. This would distribute control and add a delay to sensitive actions, enhancing security and decentralization.


### `L-01` — Front-Running Risk in `decreaseAllowance`  *(Severity: Low · Status: Unresolved)*

The `decreaseAllowance` function, while an improvement over directly setting allowance to zero, is still susceptible to front-running. If a user broadcasts a transaction to `decreaseAllowance`, an attacker monitoring the mempool could front-run this transaction by quickly spending the remaining allowance before the decrease takes effect. This is a known pattern in ERC-20 tokens.

**Recommendation:** Users should be aware of this inherent risk when interacting with allowance mechanisms. While no direct code change is typically made for this, users can mitigate risk by approving only necessary amounts or by using a transaction relay service that obscures transaction details until confirmation.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0e09...ce82`](https://bscscan.com/address/0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82) |
| **Network** | BNB Chain |
| **Price** | $1.4500 |
| **24h Volume** | $178.3K |
| **Liquidity** | $3.92M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 3y |
| **Top-10 Holders** | 96.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 209 buys / 268 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x7f51c8aaa6b0599abd16674e2b17fec7a9f674a1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pancakeswap-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*
