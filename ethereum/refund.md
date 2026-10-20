---
token: REFUND
ticker: RFD
network: ethereum
risk_score: 6
status: low
date: 2026-10-11
---

# REFUND (RFD) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 6/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/refund-eth)

---

## Audit Summary

The REFUND contract is a standard ERC-20 token implementation. Static analysis and review of key functions reveal no privileged roles or complex logic, and no critical or high-severity vulnerabilities were identified.

> **Final Recommendation:** Ensure that all interactions with the REFUND token adhere to standard ERC-20 practices. Users should verify the contract address to prevent interacting with malicious imposters. While the contract itself is robust, external factors such as wallet security and phishing remain critical considerations for token holders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The REFUND contract implements the ERC-20 standard correctly, as evidenced by the presence of all required functions like `transfer` and `transferFrom`. The code for these functions includes standard… |
| **Governance / Economics** | 7/10 | Low | The contract is a basic ERC-20 token with no governance mechanisms, special economic incentives, or fee structures beyond standard token transfers (7.5 Governance, 7.4 Economic). There are no… |
| **Upgrades** | 9/10 | Low | The REFUND contract is not implemented as a proxy and therefore is not upgradeable (7.7 Upgrades). This eliminates risks associated with upgradeability patterns such as proxy misconfigurations or… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.9% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 2 address(es) other than the owner/deployer. One of them — a wallet, 0x4c53…bea2 — holds 99.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 75.1% of supply. Of that, 12.2% burned, 51.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.8% in wallets, 2.8% in other contracts. 6,913 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Refund (RFD), market cap $2M, rank #2397. 6,913 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.6M (DexScreener, all pools). 24h trading volume $190K (CoinGecko, all markets, daily snapshot). 24h trading volume $175K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.000105 on 2023-05-22; the price is now 98.1148% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.6M of DEX liquidity across 5 pools. Launch: 1240 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x955d...5ba1`](https://etherscan.io/address/0x955d5c14c8d4944da1ea7836bd44d54a8ec35ba1) |
| **Network** | Ethereum |
| **Price** | $0.00000193 |
| **24h Volume** | $174.2K |
| **Liquidity** | $1.55M |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 75.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 92 buys / 34 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x6c4c7f46d9d4ef6bc5c9e155f011ad19fc4ef321)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/refund-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
