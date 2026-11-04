---
token: WIN界
ticker: WIN界
network: bsc
risk_score: 1
status: low
date: 2026-11-04
---

# WIN界 (WIN界) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/win-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a standard ERC-20 token implemented as an EIP-1167 minimal clone. The contract ownership has been renounced on-chain, rendering all privileged administrative functions dormant and inaccessible. The codebase follows standard OpenZeppelin patterns for upgradeable contracts, though the clone deployment ensures the implementation logic is immutable. No critical vulnerabilities were identified during the analysis.

> **Final Recommendation:** The contract is in a secure, immutable state due to the renouncement of ownership and the use of the EIP-1167 clone pattern. No further action is required for the current deployment. Users should verify the contract address against official documentation to ensure they are interacting with the intended deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture utilizes a robust EIP-1167 minimal clone pattern, ensuring gas-efficient deployment and immutable logic. Code security is high, leveraging audited OpenZeppelin libraries for ERC-20… |
| **Governance / Economics** | 10/10 | Low | Governance is effectively decentralized as ownership has been renounced, preventing any future modification of tax or migration parameters. 7.4 Economic: Parameters are fixed. 7.5 Governance… |
| **Upgrades** | 10/10 | Low | The contract is deployed as an EIP-1167 minimal clone, which is inherently immutable and cannot be upgraded. 7.7 Upgrades: Not applicable due to clone architecture. The implementation logic is… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 82.3% of supply. Of that, 60.3% burned, 6.0% locked, 3.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 2.4% in wallets, 9.8% in other contracts. 14,263 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as WIN界 (WIN界), market cap $4M, rank #1929. 14,263 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 69% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $194K (DexScreener, all pools). 24h trading volume $136K (CoinGecko, all markets, daily snapshot). 24h trading volume $265K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Chinese Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 1% on sell. Market: $194K of DEX liquidity across 2 pools. Launch: 70 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3f15...7777`](https://bscscan.com/address/0x3f15b50f4631ca33ebf06bef7b6f9ad2448d7777) |
| **Network** | BNB Chain |
| **Price** | $0.001742 |
| **24h Volume** | $263.9K |
| **Liquidity** | $133.7K |
| **Volume / Liquidity** | 2.0× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 82.3% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 1676 buys / 997 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x35f8b07934a1eb33d23dcbd113c4fef6ab257710)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/win-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
