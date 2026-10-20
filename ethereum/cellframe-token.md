---
token: Cellframe Token
ticker: CELL
network: ethereum
risk_score: 6
status: low
date: 2026-10-03
---

# Cellframe Token (CELL) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 6/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cellframe-token-eth)

---

## Audit Summary

The CellToken contract is a standard ERC-20 token implementation. The audit found no critical, high, or medium severity issues, indicating a robust and straightforward design. The contract lacks custom privileged functions or complex transfer logic, adhering closely to established ERC-20 standards.

> **Final Recommendation:** The CellToken contract appears to be a straightforward ERC-20 implementation. It is recommended to ensure that the token's initial supply and distribution align with the project's economic model and whitepaper. For any future integrations with other protocols, thoroughly review the interaction logic to prevent common integration pitfalls like reentrancy in external protocols or incorrect token handling.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The CellToken contract implements the ERC-20 standard without additional complex logic or privileged functions affecting transfers (7.1 Architecture). The `transfer` and `transferFrom` functions… |
| **Governance / Economics** | 9/10 | Low | The CellToken contract is a basic ERC-20 token with no specific governance or economic mechanisms beyond its fungible token nature (7.4 Economic). There are no privileged roles or functions that can… |
| **Upgrades** | 9/10 | Low | The CellToken contract is not implemented as a proxy and therefore does not support upgradeability (7.7 Upgrades). This design choice eliminates risks associated with upgrade mechanisms, such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 31.4% |
| **Top-3 Unlocked** | 75.8% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 93.9% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $112K (DexScreener, all pools). 24h trading volume $238K (CoinGecko, all markets, daily snapshot). 24h trading volume $31K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $7.21 on 2021-03-24; the price is now 99.3696% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 17.3% of supply. Of that, 1.9% burned, 2.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 10.6% in wallets, 2.1% in other contracts. 10,931 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Cellframe (CELL), market cap $2M, rank #2553. 10,931 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $112K of DEX liquidity across 6 pools. Launch: 2025 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x26c8...e099`](https://etherscan.io/address/0x26c8afbbfe1ebaca03c2bb082e69d0476bffe099) |
| **Network** | Ethereum |
| **Price** | $0.06507 |
| **24h Volume** | $30.2K |
| **Liquidity** | $109.7K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 5y |
| **Top-10 Holders** | 17.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 64 buys / 54 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x9c4cc862f51b1ba90485de3502aa058ca4331f32)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cellframe-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
