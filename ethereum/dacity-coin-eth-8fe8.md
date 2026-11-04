---
token: Dacity Coin
ticker: DACITY
network: ethereum
risk_score: 70
status: high
date: 2026-11-04
---

# Dacity Coin (DACITY) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dacity-coin-eth-8fe8)

---

## Audit Summary

The audited contract is a standard ERC-20 token implementation utilizing OpenZeppelin libraries. It contains no privileged roles, administrative backdoors, or complex logic, making it highly predictable and secure by design. The code adheres to standard interface specifications.

> **Final Recommendation:** The contract is secure and follows best practices for a standard ERC-20 token. No further action is required for the current implementation.

Ensure that any future integrations or extensions to this token maintain the same level of simplicity and avoid adding unnecessary administrative functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows the standard ERC-20 pattern (7.1 Architecture) with robust implementation via OpenZeppelin (7.2 Code Security). There are no access control mechanisms (7.3 Access Control) as… |
| **Governance / Economics** | 2/10 | High | The contract lacks governance (7.5 Governance) and economic parameters (7.4 Economic) as it is a simple token. There are no minting or burning functions that could impact supply dynamics. Operations… |
| **Upgrades** | 6/10 | Medium | The contract is not upgradeable (7.7 Upgrades). It is a static implementation, ensuring that the logic cannot be altered post-deployment. This eliminates risks associated with proxy patterns or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0x4c1c…d74a) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The holder list from the security indexer adds up to 128.8% of supply, so it does not describe real balances. That happens with rebasing and reflection tokens, whose balances change without transfers, and with contracts that report balances they do not hold. Concentration is unknown and priced as an unknown — neither a whale nor safe.

**Recommendation:** Check the largest holders on the block explorer, which reads current balances.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

252 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $104K (DexScreener, all pools). 24h trading volume $395K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $104K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x0dc4...f3b7`](https://etherscan.io/address/0x0dc4bc369ff564543738ebb04f2f1e6f4343f3b7) |
| **Network** | Ethereum |
| **Price** | $0.00116 |
| **24h Volume** | $394.8K |
| **Liquidity** | $103.7K |
| **Volume / Liquidity** | 3.8× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 335 buys / 165 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x443788ef13a2108291a44c60537d62a107042e52e0440152053af7a54d52c9cb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dacity-coin-eth-8fe8)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
