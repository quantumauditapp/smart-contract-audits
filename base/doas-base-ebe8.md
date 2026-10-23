---
token: DOAS
ticker: DOAS
network: base
risk_score: 56
status: medium
date: 2026-10-23
---

# DOAS (DOAS) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/doas-base-ebe8)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance and vesting features. The protocol relies on a centralized owner to manage inflation and liquidity pool access. While the code follows standard OpenZeppelin patterns, the high degree of administrative control presents a significant trust requirement for token holders.

> **Final Recommendation:** Token holders should be aware that the owner possesses significant control over the token supply and transferability. It is recommended to transition ownership to a multi-signature wallet or a decentralized governance contract to mitigate single-point-of-failure risks.

Ensure that all administrative actions are communicated transparently to the community. The current implementation of minting and pool locking is functional but requires high trust in the current owner's address.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes robust OpenZeppelin standards for ERC-20, Votes, and Permit functionality. Code security is high due to the use of audited libraries and standard patterns. 7.1 Architecture… |
| **Governance / Economics** | 3/10 | High | Economic parameters are governed by the owner, who can mint tokens up to a 2% annual cap. 7.4 Economic and 7.5 Governance rely entirely on the owner's address. 7.6 External dependencies are minimal… |
| **Upgrades** | 4/10 | Medium | The contract is not upgradeable, eliminating 7.7 Upgrades risk. 7.8 Operations are limited to the owner's ability to pause or mint, which is transparently defined in the source code. |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total supply of tokens. This allows the owner to dilute the holdings of all existing token holders at their discretion, provided they stay within the 2% annual cap.

**Recommendation:** Consider implementing a time-lock for minting operations or moving the minting authority to a decentralized governance DAO to prevent unilateral supply increases.


### `CP-05` — Centralized Control Over Token Transfers  *(Severity: Medium · Status: Unresolved)*

The owner can use lockPool and unlockPool to toggle a switch that controls whether transfers are permitted. This gives the owner the ability to effectively freeze or unfreeze the token's utility or liquidity at any time.

**Recommendation:** Remove the ability for the owner to arbitrarily lock transfers, or restrict this functionality to a time-bound emergency pause mechanism that requires community approval for extended durations.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,818 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,818 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $106K (DexScreener, all pools). 24h trading volume $419K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $106K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x202e...0049`](https://basescan.org/address/0x202eeff8c29fa58825985b1c4fcfad5250f80049) |
| **Network** | Base |
| **Price** | $0.2435 |
| **24h Volume** | $419.4K |
| **Liquidity** | $106.0K |
| **Volume / Liquidity** | 4.0× |
| **Token Age** | 17h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1728 buys / 1715 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xfa086b8414576f934d395c015e1d565fb6b3c176ad4a653ab61cbfad4be7b6bc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/doas-base-ebe8)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
