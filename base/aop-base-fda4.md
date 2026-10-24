---
token: AOP
ticker: AOP
network: base
risk_score: 76
status: high
date: 2026-10-24
---

# AOP (AOP) — Smart Contract Security Analysis | Base

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aop-base-fda4)

---

## Audit Summary

The audit evaluated the DERC20 token contract deployed on Base. The implementation builds on established OpenZeppelin components including ERC20Votes, ERC20Permit, and standard Ownable access controls. Two medium-severity issues were identified relating to privileged inflation minting via updateMintRate and trading restrictions via lockPool and unlockPool state switches.

> **Final Recommendation:** The development team should place privileged administrative functions, particularly lockPool, unlockPool, and updateMintRate, behind a transparent timelock contract to give token holders advance notice of economic or transfer policy changes. Additionally, the project should continue managing the contract with a robust multi-signature scheme and consider eventually renouncing or freezing transfer-locking capabilities once liquidity pools are permanently established.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | Under 7.1 Architecture, the contract implements standard OpenZeppelin ERC-20, permit, and governance voting patterns with clean separation of duties. In terms of 7.2 Code Security, the contract… |
| **Governance / Economics** | 3/10 | High | For 7.4 Economic considerations, the contract enforces a hard cap on annual inflation via MAX_YEARLY_MINT_RATE_WAD (maximum 2% per year), protecting holders from runaway dilution. However, under 7.5… |
| **Upgrades** | 4/10 | Medium | Regarding 7.7 Upgrades, the contract is deployed as an immutable non-proxy contract, eliminating logic swap vulnerabilities and storage collision risks. Administrative parameters such as tokenURI and… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Privileged Annual Inflation Minting  *(Severity: Medium · Status: Unresolved)*

The contract owner can invoke the updateMintRate function, which triggers mintInflation and creates new tokens up to a 2% annual cap. While the release function also releases vested tokens to claimants, updateMintRate directly increases the total circulating token supply, causing gradual dilution to existing token holders.

**Recommendation:** Impose a timelock on mint rate adjustments and consider establishing automated, decentralized distribution rules for newly minted tokens to ensure predictability for holders.


### `CP-05` — Privileged Trading Lock Switch  *(Severity: Medium · Status: Unresolved)*

The owner has exclusive authority to call lockPool and unlockPool, modifying the isPoolUnlocked flag and setting the designated pool address. When locked, token transfers involving the pool can be blocked or restricted, effectively preventing token holders from buying or selling tokens on decentralized exchanges.

**Recommendation:** Implement a one-way irreversible unlock mechanism once public trading commences, or bound lockPool execution behind a timelock to prevent arbitrary disruption of market liquidity.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 10,008 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

10,008 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $108K (DexScreener, all pools). 24h trading volume $483K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $108K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x73d3...5920`](https://basescan.org/address/0x73d36a52a6041788012d086ffc746516895b5920) |
| **Network** | Base |
| **Price** | $1.0600 |
| **24h Volume** | $482.5K |
| **Liquidity** | $108.1K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 5h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2936 buys / 2613 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xb9c4c92495c0d30c5cb59bdadb550fde0ca48a946449e5fd3fff8d437df436ee)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aop-base-fda4)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
