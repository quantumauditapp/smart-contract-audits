---
token: NODF
ticker: NODF
network: base
risk_score: 56
status: medium
date: 2026-10-27
---

# NODF (NODF) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nodf-base-cdba)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance, voting, and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates and pool access. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over token supply and transferability introduces significant trust requirements for token holders.

> **Final Recommendation:** To improve security, consider transitioning the owner role to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks. Additionally, implement timelocks on all privileged functions, particularly those affecting token supply and transferability, to provide transparency and allow the community to react to administrative changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes well-tested OpenZeppelin libraries for ERC-20, voting, and permit functionality. 7.1 Architecture and 7.2 Code Security are robust, leveraging standard patterns for state… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized under the owner's control. The owner can adjust inflation rates via updateMintRate, impacting token dilution. 7.6 External dependencies are… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, which provides security against unauthorized logic changes but prevents patching if vulnerabilities are… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to mint new tokens and adjust the yearly inflation rate through the updateMintRate and release functions. This allows the owner to unilaterally dilute the holdings of all existing token holders.

**Recommendation:** Implement a timelock on the updateMintRate function and consider capping the total supply or moving the minting authority to a decentralized governance mechanism.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the transferability of tokens by calling lockPool and unlockPool. This grants the owner the ability to freeze user funds or restrict trading at their discretion.

**Recommendation:** Remove the ability for the owner to arbitrarily lock transfers, or implement a multi-signature requirement for these functions to prevent abuse by a single compromised account.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 20 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

20 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $568K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $568K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3d1e...bb1d`](https://basescan.org/address/0x3d1e6ea3321f8359ed843fc081eed2a3715cbb1d) |
| **Network** | Base |
| **Price** | $0.07025 |
| **24h Volume** | $1.31M |
| **Liquidity** | $568.4K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 10h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1024 buys / 1008 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x6d04e53c35d90d1af4d8dc52624446d16ef548cc4bb8112acd67e55c8c959758)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nodf-base-cdba)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
