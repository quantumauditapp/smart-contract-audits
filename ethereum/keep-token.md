---
token: KEEP Token
ticker: KEEP
network: ethereum
risk_score: 31
status: low
date: 2026-10-25
---

# KEEP Token (KEEP) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 31/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/keep-token-eth)

---

## Audit Summary

The KeepToken contract is a standard ERC-20 implementation utilizing OpenZeppelin's legacy library. The contract functions as a basic utility token without administrative backdoors, complex logic, or upgradeability features. No vulnerabilities were identified in the transfer path or state management.

> **Final Recommendation:** The contract is secure and functions as intended for a standard ERC-20 token. No further action is required as the code is immutable and free of identified vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows the standard ERC-20 pattern, ensuring 7.1 Architecture and 7.2 Code Security compliance. 7.3 Access Control is inherently secure as there are no privileged functions. 7.6… |
| **Governance / Economics** | 1/10 | High | The token lacks 7.5 Governance mechanisms, which eliminates risks associated with centralized control. 7.4 Economic parameters are fixed by the initial supply and standard transfer logic. The absence… |
| **Upgrades** | 8/10 | Low | The contract is immutable, satisfying 7.7 Upgrades requirements by design. There is no proxy pattern or administrative logic that could alter the contract's bytecode or state after deployment. 7.8… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 81.6% |
| **Top-3 Unlocked** | ⚠️ 89.3% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 97.0% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a contract, 0x47a5…6f44 — holds 81.6% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $33K (DexScreener, all pools). 24h trading volume $27K (CoinGecko, all markets, daily snapshot). 24h trading volume $53K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $6.10 on 2020-05-14; the price is now 99.4913% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.7% of supply. What remains: 2.4% in wallets, 95.3% in other contracts. 11,963 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Keep Network (KEEP), market cap $30M, rank #652. On GoPlus's list of trusted tokens. Traded on Binance, Coinbase. 11,963 holders. Verified by: CoinGecko, GoPlus, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $33K of DEX liquidity across 5 pools. Launch: 2349 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x85ee...afec`](https://etherscan.io/address/0x85eee30c52b0b379b046fb0f85f4f3dc3009afec) |
| **Network** | Ethereum |
| **Price** | $0.02615 |
| **24h Volume** | $52.6K |
| **Liquidity** | $32.2K |
| **Volume / Liquidity** | 1.6× |
| **Token Age** | 6y |
| **Top-10 Holders** | 97.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 338 buys / 563 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xe6f19dab7d43317344282f803f8e8d240708174a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/keep-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*
