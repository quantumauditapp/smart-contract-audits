---
token: 金蝶圣甲
ticker: 金蝶圣甲
network: bsc
risk_score: 0
status: low
date: 2026-10-24
---

# 金蝶圣甲 (金蝶圣甲) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-63fb6e-bsc)

---

## Audit Summary

The FlapTaxTokenV3 is a minimal clone (EIP-1167) implementation of an ERC-20 token with custom tax and migration logic. The contract ownership has been formally renounced, rendering all privileged administrative functions permanently inaccessible. The architecture is immutable, and the core token logic adheres to standard ERC-20 patterns.

> **Final Recommendation:** The contract is secure due to the renunciation of ownership and the immutable nature of the EIP-1167 clone pattern. No further action is required as the administrative attack surface has been eliminated.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes a robust EIP-1167 minimal clone architecture, ensuring bytecode immutability. 7.1 Architecture and 7.2 Code Security are sound, as the implementation relies on well-vetted… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic and 7.5 Governance risks are mitigated by the renunciation of ownership. No entity can trigger the migration functions or modify the tax state, ensuring the economic parameters are… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are impossible for this contract due to its nature as an EIP-1167 minimal clone. The implementation logic is permanently bound to the proxy, preventing any future logic changes. 7.8… |

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

The ten largest holders own 81.7% of supply. Of that, 80.0% burned, 1.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.4% in wallets, 0.2% in other contracts. 18,215 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as 金蝶圣甲 (Golden Butterfly Sacred Armor) (金蝶圣甲), market cap $5M, rank #1680. 18,215 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $482K (DexScreener, all pools). 24h trading volume $410K (CoinGecko, all markets, daily snapshot). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Chinese Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 3% on buy, 3% on sell. Market: $482K of DEX liquidity across 6 pools. Launch: 98 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4f0c...7777`](https://bscscan.com/address/0x4f0c550bfe484f957d5c7dd26f9a630a92a17777) |
| **Network** | BNB Chain |
| **Price** | $0.02185 |
| **24h Volume** | $1.28M |
| **Liquidity** | $481.9K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 81.7% of supply |
| **Buy / Sell Tax** | 3.0% / 3.0% |
| **24h Transactions** | 3104 buys / 1139 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x3e86832b28854b5c7a86e8666ac4ab92cda1843e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-63fb6e-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
