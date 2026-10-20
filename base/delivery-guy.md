---
token: Delivery Guy
ticker: DGUY
network: base
risk_score: 10
status: low
date: 2026-10-01
---

# Delivery Guy (DGUY) — Smart Contract Security Analysis | Base

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/delivery-guy-base)

---

## Audit Summary

The StonkToken contract is a standard ERC-20 implementation. The audit found no critical, high, medium, or low severity vulnerabilities. The contract exhibits no privileged functions or complex logic beyond basic token transfers, contributing to its low overall risk profile.

> **Final Recommendation:** Given the contract's simplicity and the absence of identified vulnerabilities, the primary recommendation is to ensure users understand its immutable nature. For any future development involving this token, consider integrating it with well-audited protocols. Always verify contract addresses before interacting to prevent phishing or malicious contract interactions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The StonkToken contract is a straightforward ERC-20 implementation (7.1 Architecture). It includes standard token functionalities like `transfer`, `transferFrom`, and `approve`. Static analysis… |
| **Governance / Economics** | 2/10 | High | The StonkToken contract functions as a basic ERC-20 token without any complex economic models, staking mechanisms, or governance features (7.4 Economic, 7.5 Governance). Its design is simple… |
| **Upgrades** | 8/10 | Low | The StonkToken contract is not implemented as an upgradeable proxy (7.7 Upgrades). It is a standard, non-upgradeable contract, meaning its logic cannot be altered after deployment. This eliminates… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 62.0% |
| **Top-3 Unlocked** | ⚠️ 93.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 5 address(es) other than the owner/deployer. One of them — a contract, 0x02f4…30b5 — holds 62.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 62% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 43.3% of supply. Of that, 3.9% burned — not holders that can sell, so excluded from the concentration score. What remains: 5.1% in wallets, 34.3% in other contracts. 543 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Delivery Guy (DGUY), rank #4661. 543 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $93K (DexScreener, all pools). 24h trading volume $109K (CoinGecko, all markets, daily snapshot). 24h trading volume $215K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Base Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $93K of DEX liquidity across 16 pools. Launch: 16 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 16 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 16 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xe343...c54e`](https://basescan.org/address/0xe34356dcd3d7bb991248f322e4ec31b5d60bc54e) |
| **Network** | Base |
| **Price** | $0.0002482 |
| **24h Volume** | $119.0K |
| **Liquidity** | $57.9K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 16d |
| **Top-10 Holders** | 43.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 675 buys / 554 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x4be684f77419999aa3e1162d25d9ae6ff64c05a0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/delivery-guy-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
