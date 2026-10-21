---
token: Balances
ticker: BALANCE
network: ethereum
risk_score: 60
status: medium
date: 2026-10-21
---

# Balances (BALANCE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/balances-eth)

---

## Audit Summary

The contract at the provided address is not verified on the Ethereum block explorer. Consequently, the source code is unavailable for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or potential backdoors.

> **Final Recommendation:** Do not interact with this contract. The absence of verified source code is a major red flag that prevents any assessment of security, safety, or functionality. Without transparency, there is no way to ensure that the contract does not contain malicious functions such as honeypot mechanisms or unauthorized minting capabilities.

Investors should prioritize projects that provide verified source code on block explorers and undergo third-party security audits. Given the unlocked liquidity and lack of verification, the probability of capital loss is extremely high.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Unverifiable due to lack of source code. 7.3 Access Control: Cannot be audited. 7.6 External: Liquidity is currently unlocked, posing a high risk of… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic: Tokenomics are opaque. 7.5 Governance: No information available on ownership or administrative privileges. 7.8 Operations: High risk of centralized control over token supply or trading. |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: The contract's upgradeability status is unknown. Without source code, it is impossible to determine if the contract is immutable or contains proxy patterns that allow for logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 48.9% |
| **Top-3 Unlocked** | ⚠️ 99.4% |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, making it impossible to verify the contract's logic, security, or administrative permissions.

**Recommendation:** Publish and verify the source code on the block explorer to allow for community and security review.


### `H-01` — Unlocked Liquidity  *(Severity: High · Status: Unresolved)*

Liquidity for this token is currently unlocked, which allows the deployer or owner to remove all liquidity from the pool at any time, potentially resulting in a total loss of funds for holders.

**Recommendation:** Lock liquidity in a reputable, time-locked smart contract to ensure long-term stability and investor protection.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 5 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 63% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.6% of supply. What remains: 3.6% in wallets, 77.0% in other contracts. 1,131 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,131 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $261K (DexScreener, all pools). 24h trading volume $1.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $261K of DEX liquidity across 15 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3620...ea07`](https://etherscan.io/address/0x3620540c994433d7b4a628c46d2ed5f92572ea07) |
| **Network** | Ethereum |
| **Price** | $0.07152 |
| **24h Volume** | $1.42M |
| **Liquidity** | $163.0K |
| **Volume / Liquidity** | 8.7× |
| **Token Age** | 7h |
| **Top-10 Holders** | 80.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1391 buys / 794 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xd262227cd6ad883b3d85c5138f017f90aaac0ff3ce69136c36a7280dbd009a03)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/balances-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
