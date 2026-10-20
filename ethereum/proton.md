---
token: Proton
ticker: XPR
network: ethereum
risk_score: 46
status: medium
date: 2026-10-17
---

# Proton (XPR) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/proton-eth)

---

## Audit Summary

The XPRToken contract is a standard ERC20Burnable token with no special privileged functions or complex logic. The audit found no critical, high, medium, or low severity issues, indicating a robust and straightforward implementation.

> **Final Recommendation:** The XPRToken contract is a well-implemented, standard ERC20Burnable token. Given its simplicity and lack of complex features or privileged roles, the primary security recommendation is to ensure that any external protocols interacting with this token correctly handle standard ERC20 behaviors, especially regarding approvals and transfers. Users should always verify the recipient address before initiating transfers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The XPRToken contract implements the ERC20Burnable standard, providing basic token functionalities like transfer, transferFrom, approve, and burn. The code is straightforward, with no custom… |
| **Governance / Economics** | 3/10 | High | The XPRToken contract exhibits a low governance and economic risk profile due to its simplicity. There are no privileged roles or functions that can alter core token mechanics or introduce economic… |
| **Upgrades** | 8/10 | Low | The XPRToken contract is not designed as an upgradeable proxy (7.7 Upgrades). It is a standard implementation contract, meaning its logic cannot be changed post-deployment. This eliminates risks… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 63.5% |
| **Top-3 Unlocked** | ⚠️ 85.3% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 98.0% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a wallet, 0xe853…f250 — holds 63.5% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 70.9% of supply. Of that, 0.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 70.6% in wallets, 0.0% in other contracts. 28,608 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as XPR Network (XPR), market cap $55M, rank #423. 28,608 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $91K (DexScreener, all pools). 24h trading volume $2.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $103K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.1 on 2020-04-27; the price is now 98.0929% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $91K of DEX liquidity across 3 pools. Launch: 2230 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd7ef...a2af`](https://etherscan.io/address/0xd7efb00d12c2c13131fd319336fdf952525da2af) |
| **Network** | Ethereum |
| **Price** | $0.00198 |
| **24h Volume** | $102.5K |
| **Liquidity** | $90.5K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 6y |
| **Top-10 Holders** | 70.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 114 buys / 119 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x464bd7e6718a815c20a5ad529003d7a93a9676b3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/proton-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*
