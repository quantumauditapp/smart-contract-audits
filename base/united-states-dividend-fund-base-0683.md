---
token: United States Dividend Fund🔥
ticker: USDF
network: base
risk_score: 56
status: medium
date: 2026-10-24
---

# United States Dividend Fund🔥 (USDF) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-base-0683)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance and vesting features. The protocol relies on a centralized owner to manage inflation, pool locking, and vesting releases. While the code follows standard OpenZeppelin patterns, the high degree of administrative control presents a significant centralization risk for token holders.

> **Final Recommendation:** The protocol should consider transitioning ownership to a multi-signature wallet or a decentralized governance DAO to mitigate the risks associated with a single point of failure. Implementing a timelock on sensitive functions like updateMintRate and lockPool would provide transparency and allow the community to react to administrative changes.

Users should be aware that the owner possesses the technical capability to dilute supply and restrict token transfers. Monitoring the owner's address for activity is recommended for all token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes well-audited OpenZeppelin libraries for ERC-20, Votes, and Permit functionality. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance risks are elevated due to the owner's ability to mint tokens and halt transfers. The owner can trigger inflation via updateMintRate, which directly impacts holder… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not implemented; the contract is immutable. 7.8 Operations are handled via direct owner calls. This lack of upgradeability ensures code consistency but prevents emergency patching if… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to call updateMintRate and release, which increases the total supply of the token. This allows the owner to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Implement a timelock on minting functions or move the minting authority to a decentralized governance contract to ensure community oversight.


### `CP-05` — Administrative Control Over Transfers  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to toggle a switch that determines whether transfers are permitted. This gives the owner the power to effectively freeze the token's liquidity.

**Recommendation:** Remove the ability to arbitrarily lock transfers or restrict this functionality to specific, time-bound scenarios with clear community-approved parameters.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 7,022 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

7,022 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $447K (DexScreener, all pools). 24h trading volume $640K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Its name presents it as a stable-value coin, yet it trades at $0.916 — it does not hold a peg. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $447K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2252...dbcd`](https://basescan.org/address/0x2252bed55d3d170829814db2303f6025bfeadbcd) |
| **Network** | Base |
| **Price** | $0.916 |
| **24h Volume** | $640.4K |
| **Liquidity** | $446.6K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 10h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1304 buys / 1276 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xb0d05f9d0795c9838e421fc0382ec3e734ea14786d34adad58028bcf82522af4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/united-states-dividend-fund-base-0683)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
