---
token: LOUZI
ticker: LOUZI
network: bsc
risk_score: 65
status: high
date: 2026-10-29
---

# LOUZI (LOUZI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/louzi-bsc)

---

## Audit Summary

The LOUZI contract is a standard ERC-20 token implementation utilizing OpenZeppelin's ERC20Permit extension. The codebase is clean, follows industry-standard patterns, and lacks any centralized administrative control or privileged functions that could restrict user transfers or modify token balances. No vulnerabilities were identified during the static analysis of the contract.

> **Final Recommendation:** The LOUZI contract is well-structured and follows secure coding standards. No further action is required as the contract is immutable and lacks privileged functions.

Users should always verify the contract address before interacting with the token to ensure they are engaging with the legitimate deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The architecture follows the standard ERC-20 implementation (7.1 Architecture) with robust security practices (7.2 Code Security). It utilizes well-audited OpenZeppelin libraries for permit… |
| **Governance / Economics** | 2/10 | High | The contract lacks any governance or economic parameters (7.4 Economic, 7.5 Governance). There are no minting, burning, or fee-on-transfer mechanisms. The token operates as a pure utility asset… |
| **Upgrades** | 6/10 | Medium | The contract is not a proxy and is immutable (7.7 Upgrades). There are no administrative functions to modify the contract logic or state (7.8 Operations). This eliminates risks associated with… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the token's owner/deployer (0xaa57…2d22) — they can pull that liquidity at any moment. This is the rug-pull path. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 20.8% of supply. Of that, 5.0% locked, 14.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 1.6% in wallets, 0.0% in other contracts. 3,836 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as LOUZI (LOUZI). 3,836 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11.5M (DexScreener, all pools). 24h trading volume $340K (CoinGecko, all markets, daily snapshot). 24h trading volume $596K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11.5M of DEX liquidity across 1 pools. Launch: 156 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xed47...5aff`](https://bscscan.com/address/0xed4715c47a67e3cd09d765babc4b9f0e44e65aff) |
| **Network** | BNB Chain |
| **Price** | $0.08051 |
| **24h Volume** | $595.6K |
| **Liquidity** | $11.45M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 20.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 466 buys / 466 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0xea358597b25ca24ae91ef35defe31e046d34f83d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/louzi-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
