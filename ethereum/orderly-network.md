---
token: Orderly Network
ticker: ORDER
network: ethereum
risk_score: 51
status: medium
date: 2026-10-24
---

# Orderly Network (ORDER) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/orderly-network-eth)

---

## Audit Summary

The OrderToken contract is a standard ERC-20 implementation with no additional privileged functions or complex logic. The code adheres to OpenZeppelin standards, ensuring predictable behavior for token transfers and approvals. No vulnerabilities were identified during the static analysis of the contract's transfer path or state management.

> **Final Recommendation:** The contract is secure and follows industry best practices for a standard ERC-20 token. No further action is required for the current implementation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows a standard, battle-tested ERC-20 pattern (7.1 Architecture). Code security is high due to the use of standard libraries (7.2 Code Security). There are no custom access… |
| **Governance / Economics** | 6/10 | Medium | There are no economic parameters or governance mechanisms present in this contract (7.4 Economic, 7.5 Governance). The token functions as a simple utility asset without external dependencies (7.6… |
| **Upgrades** | 8/10 | Low | The contract is not upgradeable (7.7 Upgrades). It is a static implementation, meaning the logic cannot be altered post-deployment. This eliminates risks associated with proxy patterns or logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0x9b81…7db9 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 89.2% of supply. What remains: 18.0% in wallets, 71.1% in other contracts. 28,054 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Orderly (ORDER), market cap $14M, rank #1004. 28,054 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $638K (DexScreener, all pools). 24h trading volume $3.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.9M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.492 on 2025-10-06; the price is now 92.9981% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $638K of DEX liquidity across 4 pools. Launch: 790 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xabd4...4337`](https://etherscan.io/address/0xabd4c63d2616a5201454168269031355f4764337) |
| **Network** | Ethereum |
| **Price** | $0.07074 |
| **24h Volume** | $2.92M |
| **Liquidity** | $624.4K |
| **Volume / Liquidity** | 4.7× |
| **Token Age** | 2y |
| **Top-10 Holders** | 89.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1398 buys / 1207 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xb2dc4d7627501338b578985c214208eb32283086)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/orderly-network-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
