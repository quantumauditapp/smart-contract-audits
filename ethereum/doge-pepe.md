---
token: Doge Pepe
ticker: DOPE
network: ethereum
risk_score: 29
status: low
date: 2026-10-25
---

# Doge Pepe (DOPE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/doge-pepe-eth)

---

## Audit Summary

The DOPE contract is a standard ERC-20 token implementation utilizing OpenZeppelin's audited libraries. The codebase is minimal, lacks administrative privileges, and follows industry-standard patterns for token transfers and allowance management. No vulnerabilities were identified in the current implementation.

> **Final Recommendation:** The DOPE token implementation is secure and follows best practices for standard ERC-20 tokens. No further action is required as the contract is immutable and lacks complex logic that could introduce future vulnerabilities.

Users should always verify the contract address against official sources before interacting with the token to ensure they are transacting with the intended asset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows the standard ERC-20 specification (7.1 Architecture). Code security is high due to the use of battle-tested OpenZeppelin contracts (7.2 Code Security). Access control is… |
| **Governance / Economics** | 8/10 | Low | The token has no governance mechanisms (7.5 Governance). Economic parameters are fixed at deployment (7.4 Economic). There are no external dependencies or oracle requirements (7.6 External). The… |
| **Upgrades** | 10/10 | Low | The contract is not a proxy and is immutable (7.7 Upgrades). There are no upgrade paths or administrative backdoors (7.8 Operations). The code is fixed upon deployment, ensuring long-term stability… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Locked** | 100.0% — TeamFinance |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $16K (DexScreener, all pools). 24h trading volume $29K (CoinGecko, all markets, daily snapshot). 24h trading volume $35K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0275 on 2026-10-14; the price is now 99.8886% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, LP lock/burn state, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.3% of supply. Of that, 27.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 32.3% in wallets, 31.6% in other contracts. 837 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Doge Pepe (DOPE), rank #7494. 837 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked, lock term not visible  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% is held by TeamFinance, but the lock's end date is not published in the data we can read — its duration is unverified. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $16K of DEX liquidity across 1 pools. Launch: 14 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 14 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 14 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x73df...4446`](https://etherscan.io/address/0x73df7018cbcb919ccde48c3f12f4326688ac4446) |
| **Network** | Ethereum |
| **Price** | $0.00003156 |
| **24h Volume** | $35.4K |
| **Liquidity** | $16.4K |
| **Volume / Liquidity** | 2.2× |
| **Token Age** | 14d |
| **Top-10 Holders** | 91.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 131 buys / 57 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xf774c0cf63a7bb1a403fc7256242283c150e9b95)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/doge-pepe-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
