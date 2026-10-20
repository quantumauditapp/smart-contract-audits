---
token: LayerEdge
ticker: EDGEN
network: ethereum
risk_score: 14
status: low
date: 2026-10-15
---

# LayerEdge (EDGEN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/layeredge-eth)

---

## Audit Summary

The audit of the LayerEdgeToken contract found it to be a standard ERC-20 implementation with no custom privileged functions or complex transfer logic. No critical or high-severity vulnerabilities were identified, indicating a robust and secure design for its intended purpose.

> **Final Recommendation:** For token holders, it is important to understand that the LayerEdgeToken operates as a standard, immutable ERC-20 token. Its functionality is limited to basic token transfers and approvals, without any special administrative controls. Users should always verify the contract address and ensure they are interacting with the legitimate token. Given its immutable nature, the contract's behavior will remain consistent over time.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The LayerEdgeToken contract is a standard ERC-20 implementation, inheriting from OpenZeppelin's ERC20Permit and ERC20. It includes all expected ERC-20 functions like `transfer` and `approve`. The… |
| **Governance / Economics** | 7/10 | Low | The LayerEdgeToken contract does not implement any custom governance mechanisms or complex economic models beyond the standard ERC-20 token functionality (7.5 Governance, 7.4 Economic). There are no… |
| **Upgrades** | 9/10 | Low | The LayerEdgeToken contract is not implemented as a proxy and therefore is not upgradeable (7.7 Upgrades). This design choice eliminates risks associated with upgradeability, such as proxy… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a wallet, 0xcc5d…4899 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.6% of supply. Of that, 26.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 2.2% in wallets, 68.4% in other contracts. 4,156 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as LayerEdge (EDGEN), rank #6958. 4,156 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $90K (DexScreener, all pools). 24h trading volume $49K (CoinGecko, all markets, daily snapshot). 24h trading volume $64K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0239 on 2025-06-02; the price is now 98.8855% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $90K of DEX liquidity across 2 pools. Launch: 499 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xaa98...02ca`](https://etherscan.io/address/0xaa9806c938836627ed1a41ae871c7e1889ae02ca) |
| **Network** | Ethereum |
| **Price** | $0.0002596 |
| **24h Volume** | $64.3K |
| **Liquidity** | $89.7K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 97.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 121 buys / 72 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x4b2c930f88a87d1bffac291b6a7e01c9f13dd03e)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/layeredge-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
