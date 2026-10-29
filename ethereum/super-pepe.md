---
token: Super Pepe
ticker: SP
network: ethereum
risk_score: 1
status: low
date: 2026-10-29
---

# Super Pepe (SP) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/super-pepe-eth)

---

## Audit Summary

The audited contract is a standard ERC-20 token implementation utilizing OpenZeppelin libraries. It contains no privileged administrative functions, backdoors, or custom transfer logic, making it highly secure and predictable. The code adheres to industry standards for token behavior.

> **Final Recommendation:** The contract is secure and ready for deployment. No further changes are required as the implementation relies entirely on battle-tested, standard library code.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows the standard ERC-20 pattern with no deviations. 7.1 Architecture is clean and modular, 7.2 Code Security is high due to the use of audited libraries, and 7.3 Access Control… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance items are not applicable as the token lacks minting, burning, or administrative governance features. The token supply is fixed upon deployment. There are no economic… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the contract is not a proxy. 7.8 Operations are straightforward, as the contract is immutable and requires no maintenance. The lack of upgradeability ensures that… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 15.1% of supply. What remains: 15.1% in wallets, 0.0% in other contracts. 579 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Super Pepe (SP). 579 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $408K (DexScreener, all pools). 24h trading volume $25.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (pepe). Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $408K of DEX liquidity across 5 pools. Launch: 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8bb6...179c`](https://etherscan.io/address/0x8bb6aa42be6551d9843ce3f4ec5297b6c0d9179c) |
| **Network** | Ethereum |
| **Price** | $0.01818 |
| **24h Volume** | $2.25M |
| **Liquidity** | $408.3K |
| **Volume / Liquidity** | 5.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | 15.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1122 buys / 485 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x7b0462ffc91785028b67d6411a410661e909fc98e7f8d7657c8fc9f23f45df0a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/super-pepe-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
