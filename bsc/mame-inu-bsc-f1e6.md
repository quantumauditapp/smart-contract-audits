---
token: Mame Inu
ticker: MAME
network: bsc
risk_score: 7
status: low
date: 2026-10-06
---

# Mame Inu (MAME) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mame-inu-bsc-f1e6)

---

## Audit Summary

The FlapTaxTokenV3 contract is an ERC-20 token deployed as an EIP-1167 minimal clone, making its logic immutable. Ownership of the contract has been renounced, rendering all owner-restricted functions, including those controlling transfer fees and states, permanently inactive. No critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** Given the immutable nature of the EIP-1167 minimal clone and the renounced ownership, the FlapTaxTokenV3 contract exhibits a very low-risk profile. Users should verify the contract address and its deployment parameters to ensure they are interacting with the intended, fixed logic. No further security actions are required for this specific contract beyond standard due diligence.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The FlapTaxTokenV3 contract implements standard ERC-20 functionality, including `transfer`, `transferFrom`, and `approve`. It is deployed as an EIP-1167 minimal clone, ensuring its bytecode and logic… |
| **Governance / Economics** | 7/10 | Low | The governance risk for FlapTaxTokenV3 is minimal due to the renounced ownership (7.5 Governance). The `transferOwnership()` and `renounceOwnership()` functions are permanently inactive, preventing… |
| **Upgrades** | 9/10 | Low | The FlapTaxTokenV3 contract is deployed as an EIP-1167 minimal clone, which means its implementation is fixed and cannot be upgraded or modified after deployment (7.7 Upgrades). While it uses… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xc324…5cab — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 94% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint/owner authority, mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 49.8% of supply. Of that, 29.2% burned — not holders that can sell, so excluded from the concentration score. What remains: 17.0% in wallets, 3.6% in other contracts. 1,610 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Mame Inu (MAME), market cap $3M, rank #2173. 1,610 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $201K (DexScreener, all pools). 24h trading volume $710K (CoinGecko, all markets, daily snapshot). 24h trading volume $454K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Four.meme Ecosystem (BNB Memes). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 1% on buy, 0.99% on sell. Market: $201K of DEX liquidity across 3 pools. Launch: 11 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 11 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 11 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x39d9...7777`](https://bscscan.com/address/0x39d9b36aa0e7a1fee97d6ff614420f7308ba7777) |
| **Network** | BNB Chain |
| **Price** | $0.003196 |
| **24h Volume** | $453.5K |
| **Liquidity** | $188.9K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 11d |
| **Top-10 Holders** | 49.8% of supply |
| **Buy / Sell Tax** | 1.0% / 1.0% |
| **24h Transactions** | 3800 buys / 3061 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not Upgradeable | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not Upgradeable | ✅ | Minimal proxy clone — the implementation is fixed in its bytecode and cannot be swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xf75cdee96765c6d230528c247fc21d11f9f3927a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mame-inu-bsc-f1e6)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
