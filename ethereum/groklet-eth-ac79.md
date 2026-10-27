---
token: Groklet
ticker: GROKLET
network: ethereum
risk_score: 60
status: medium
date: 2026-10-27
---

# Groklet (GROKLET) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/groklet-eth-ac79)

---

## Audit Summary

The Groklet token is a standard ERC-20 implementation with added tax and swap functionality. Ownership has been renounced, effectively disabling administrative functions previously restricted to the owner. However, the 'taxwallet' remains a privileged entity with significant control over token economics and liquidity, and a critical initialization issue exists in the transfer logic.

> **Final Recommendation:** The project should immediately address the uninitialized state variable to prevent potential transfer failures. Given the centralization of power in the taxwallet, it is recommended to transition these functions to a multi-signature wallet or a decentralized governance contract to improve trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows a standard ERC-20 pattern with integrated tax logic. 7.1 Architecture is straightforward, though 7.2 Code Security reveals a critical uninitialized state variable in the… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic controls are centralized under the taxwallet, which can manipulate fees and extract tokens. 7.5 Governance is non-existent due to renounced ownership, leaving the community with no… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are static following the renouncement of ownership. The contract is immutable, preventing future logic changes. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟠 1 High · 🟡 2 Medium · ⚪ 6 Informational_

### `CD-01` — Uninitialized State Variable in Transfer Logic  *(Severity: High · Status: Unresolved)*

The _transfer function utilizes a state variable that is never initialized. This can lead to undefined behavior or transaction reverts during token transfers.

**Recommendation:** Ensure all state variables are properly initialized in the constructor before being accessed in the transfer path.


### `CP-05` — Centralized Control over Transfer Functionality  *(Severity: Medium · Status: Unresolved)*

The taxwallet controls the manualSwap function, which acts as a switch for internal swap logic. This allows the controller to potentially halt or alter the token's ability to process transfers and liquidity swaps.

**Recommendation:** Implement a time-lock or multi-signature requirement for the taxwallet to prevent unilateral changes to the transfer mechanism.


### `CP-07` — Privileged Fee Manipulation  *(Severity: Medium · Status: Unresolved)*

The taxwallet can adjust buy and sell taxes via the reduceFee function. While this is intended for fee management, it grants the controller the ability to set arbitrary fee structures.

**Recommendation:** Hardcode fee limits or implement a maximum fee cap to protect users from sudden, excessive tax increases.


### `CP-08` — Dormant Administrative Functions  *(Severity: Informational · Status: Unresolved)*

The removeLimit2 function allows for the modification of transaction and wallet limits. Since ownership has been renounced, these functions are currently unreachable and pose no active risk.

**Recommendation:** Remove these functions in future deployments to reduce contract size and eliminate dead code.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 43.9% of supply. Of that, 17.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 10.1% in wallets, 16.6% in other contracts. 477 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

477 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $24K (DexScreener, all pools). 24h trading volume $37K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $24K of DEX liquidity across 1 pools. Launch: 468 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xbe7e...3feb`](https://etherscan.io/address/0xbe7e21746fad3f6f83e22d02910bec250a493feb) |
| **Network** | Ethereum |
| **Price** | $0.00000077 |
| **24h Volume** | $36.9K |
| **Liquidity** | $24.1K |
| **Volume / Liquidity** | 1.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 43.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 98 buys / 73 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x5aac09083d2980351142473e35dd7455920c2b07)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/groklet-eth-ac79)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
