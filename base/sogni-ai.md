---
token: Sogni AI
ticker: SOGNI
network: base
risk_score: 48
status: medium
date: 2026-10-31
---

# Sogni AI (SOGNI) — Smart Contract Security Analysis | Base

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sogni-ai-base)

---

## Audit Summary

SogniToken is a standard ERC-20 implementation utilizing OpenZeppelin's AccessControl and ERC20Burnable modules. The contract provides standard token functionality with centralized minting capabilities restricted by role-based access control. No critical vulnerabilities were identified in the core transfer logic, though the minting authority represents a centralized risk factor.

> **Final Recommendation:** The protocol should transition the MINTER_ROLE to a multi-signature wallet or a time-locked governance contract to mitigate the risk of centralized abuse. Ensure that the private keys associated with the minter role are stored in a secure, cold-storage environment to prevent unauthorized minting events.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows industry-standard patterns using OpenZeppelin libraries for 7.1 Architecture and 7.2 Code Security. 7.3 Access Control is correctly implemented via roles, ensuring only… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic stability is subject to the minting authority's actions, which can dilute existing holders. 7.5 Governance is currently centralized, lacking a decentralized mechanism for minting… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. This ensures immutability of the current logic, preventing unauthorized code changes. The lack of upgradeability is a strength for… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows an address with the MINTER_ROLE to create new tokens at will. This increases the total supply and dilutes the value of existing holdings, representing a significant centralization of power.

**Recommendation:** Restrict the minting authority to a multi-signature wallet or a decentralized governance contract to prevent single-point-of-failure risks.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xfa2b…52bb — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The holder list from the security indexer adds up to 106.2% of supply, so it does not describe real balances. That happens with rebasing and reflection tokens, whose balances change without transfers, and with contracts that report balances they do not hold. Concentration is unknown and priced as an unknown — neither a whale nor safe.

**Recommendation:** Check the largest holders on the block explorer, which reads current balances.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Sogni AI (SOGNI), market cap $3M, rank #1991. 31,586 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $281K (DexScreener, all pools). 24h trading volume $115K (CoinGecko, all markets, daily snapshot). 24h trading volume $86K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.00794 on 2025-08-14; the price is now 90.0124% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $281K of DEX liquidity across 1 pools. Launch: 486 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe014...40fd`](https://basescan.org/address/0xe014d2a4da6e450f21b5050120d291e63c8940fd) |
| **Network** | Base |
| **Price** | $0.0008206 |
| **24h Volume** | $86.3K |
| **Liquidity** | $280.5K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 521 buys / 429 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xcc68cb8b514a2216d2eece3a0e8597ce483610eb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sogni-ai-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*
