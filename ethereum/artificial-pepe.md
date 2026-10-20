---
token: Artificial Pepe
ticker: AP
network: ethereum
risk_score: 6
status: low
date: 2026-09-29
---

# Artificial Pepe (AP) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 6/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/artificial-pepe-eth)

---

## Audit Summary

The LaunchToken contract is a standard ERC-20 token implementation. Static analysis revealed no critical, high, or medium severity vulnerabilities. The contract lacks privileged functions, ensuring a decentralized and immutable operational model for token transfers.

> **Final Recommendation:** Given the contract's immutable nature and lack of special administrative controls, the primary recommendation is to ensure adequate liquidity and distribution mechanisms are in place for the token's intended use. For projects utilizing this token, it is crucial to audit any external contracts interacting with LaunchToken to ensure they handle standard ERC-20 operations correctly and securely. No further security-specific recommendations are needed for the LaunchToken contract itself.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The LaunchToken contract implements the ERC-20 standard without additional complex logic or privileged functions (7.1 Architecture). All standard ERC-20 functions are present and appear correctly… |
| **Governance / Economics** | 9/10 | Low | The contract exhibits a strong decentralized economic and governance model (7.4 Economic, 7.5 Governance). There are no privileged functions that could alter transfer mechanisms, freeze funds, or… |
| **Upgrades** | 9/10 | Low | The LaunchToken contract is not designed as an upgradeable proxy (7.7 Upgrades). This means its logic is immutable once deployed, eliminating risks associated with upgradeability, such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 32.6% |
| **Top-3 Unlocked** | 62.4% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 98.0% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 69% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 26.3% of supply. What remains: 9.8% in wallets, 16.6% in other contracts. 826 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Artificial Pepe (), rank #3855. 826 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $162K (DexScreener, all pools). 24h trading volume $314K (CoinGecko, all markets, daily snapshot). 24h trading volume $1.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $162K of DEX liquidity across 13 pools. Launch: 25 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 25 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 25 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8602...2148`](https://etherscan.io/address/0x8602b2fd8d105a56d3152e936e66b1d414142148) |
| **Network** | Ethereum |
| **Price** | $0.0008219 |
| **24h Volume** | $899.6K |
| **Liquidity** | $111.3K |
| **Volume / Liquidity** | 8.1× |
| **Token Age** | 25d |
| **Top-10 Holders** | 26.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 879 buys / 710 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xdbebd228442a4a8e46c0e768a7f89a167e7c8bb3880bfca2c75ca67c1c5c8cb3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/artificial-pepe-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*
