---
token: Nexchain AI
ticker: NEX
network: ethereum
risk_score: 9
status: low
date: 2026-10-12
---

# Nexchain AI (NEX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nexchain-ai-eth)

---

## Audit Summary

The NexchainAI contract is a standard ERC-20 token implementation. The audit found no critical, high, or medium severity vulnerabilities. The contract lacks complex logic, privileged functions, or upgradeability, contributing to a low overall risk profile.

> **Final Recommendation:** The NexchainAI contract is a standard ERC-20 token with no identified vulnerabilities. It is recommended to ensure that the deployment process was secure and that the contract address is correctly communicated to users. For any future integrations or extensions, thorough testing and security reviews should be conducted to maintain the current high security standard.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The NexchainAI contract implements a standard ERC-20 token with no custom or complex logic beyond the basic token functionalities (7.1 Architecture). All standard ERC-20 functions are present and… |
| **Governance / Economics** | 10/10 | Low | The NexchainAI contract functions purely as an ERC-20 token without any integrated governance mechanisms or complex economic models (7.5 Governance). Token transfers are solely governed by standard… |
| **Upgrades** | 10/10 | Low | The NexchainAI contract is not designed as a proxy and therefore is not upgradeable (7.7 Upgrades). This eliminates risks associated with upgradeability, such as proxy implementation mismatches or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — TeamFinance |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 21.5% of supply. What remains: 21.5% in wallets, 0.0% in other contracts. 660 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

660 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked, lock term not visible  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is held by TeamFinance, but the lock's end date is not published in the data we can read — its duration is unverified. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $300K (DexScreener, all pools). 24h trading volume $2.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $300K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x918f...a959`](https://etherscan.io/address/0x918f03d7727aad7b68f9048dabdd7c1bfbf4a959) |
| **Network** | Ethereum |
| **Price** | $0.008919 |
| **24h Volume** | $2.32M |
| **Liquidity** | $299.7K |
| **Volume / Liquidity** | 7.8× |
| **Token Age** | 7h |
| **Top-10 Holders** | 21.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1261 buys / 720 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x1ac97b51ca74fd1f395c343b305d58e4c2b01aca)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nexchain-ai-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
