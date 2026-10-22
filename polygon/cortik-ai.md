---
token: Cortik AI
ticker: CTK
network: polygon
risk_score: 46
status: medium
date: 2026-10-22
---

# Cortik AI (CTK) — Smart Contract Security Analysis | Polygon

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cortik-ai-poly)

---

## Audit Summary

The Cortik contract is a standard ERC-20 token implementation with additional minting capabilities and administrative controls. While ownership has been renounced, the contract retains a centralized minting mechanism controlled by specific addresses (cee, cmg). Coverage: 7.1 Architecture (Standard ERC-20), 7.2 Code Security (SafeMath usage), 7.3 Access Control (Restricted minting), 7.4 Economic (Inflationary risk), 7.5 Governance (N/A), 7.6 External (Standard), 7.7 Upgrades (None), 7.8 Operations (Centralized).

> **Final Recommendation:** Token holders should be aware that the 'cee' and 'cmg' addresses possess the ability to mint new tokens, which may dilute the value of existing holdings. As ownership has been renounced, these addresses are the sole controllers of the supply expansion mechanism.

It is recommended that the project team provides transparency regarding the purpose and limitations of the minting function. If the minting capability is no longer required, the project should consider a migration to a fixed-supply contract or a time-locked minting schedule to increase trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The codebase follows standard ERC-20 patterns and utilizes SafeMath for arithmetic operations, ensuring protection against integer overflows. The logic for transfers and allowances is implemented… |
| **Governance / Economics** | 8/10 | Low | The economic model is inflationary due to the minting function, which allows authorized addresses to increase the total supply at will. While ownership of the contract has been renounced, the 'cee'… |
| **Upgrades** | 7/10 | Low | The contract is not upgradeable and does not utilize proxy patterns. Once deployed, the logic is immutable. This eliminates risks associated with malicious logic updates or proxy misconfigurations.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows the 'cee' and 'cmg' addresses to create an unlimited number of new tokens. This action directly increases the total supply and dilutes the ownership percentage of all existing token holders.

**Recommendation:** Implement a hard cap on the total supply or transition the minting authority to a multi-signature wallet or a decentralized governance contract to prevent unilateral supply expansion.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.5% of supply. Of that, 21.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.3% in wallets, 77.4% in other contracts. 2,191 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Cortik AI (CTK), rank #3520. 2,191 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.2M (DexScreener, all pools). 24h trading volume $21K (CoinGecko, all markets, daily snapshot). 24h trading volume $48K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 5% on sell. Market: $1.2M of DEX liquidity across 1 pools. Launch: 202 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9334...ca5a`](https://polygonscan.com/address/0x933479ba627356f7efaba030504bf1c65cffca5a) |
| **Network** | Polygon |
| **Price** | $3.4700 |
| **24h Volume** | $48.0K |
| **Liquidity** | $1.20M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 99.5% of supply |
| **Buy / Sell Tax** | 0.0% / 5.0% |
| **24h Transactions** | 153 buys / 234 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0xe0474cebfa5290f96ed7a7fa449dbaa666f14ee6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cortik-ai-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
