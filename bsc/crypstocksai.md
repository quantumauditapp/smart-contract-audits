---
token: CrypstocksAI
ticker: MVP
network: bsc
risk_score: 0
status: low
date: 2026-09-30
---

# CrypstocksAI (MVP) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/crypstocksai-bsc)

---

## Audit Summary

This audit covers an ERC-20 token contract. The contract implements standard token functionalities. Ownership has been renounced, rendering several privileged functions, including `setMode`, inoperable. The primary finding is an informational note regarding a dormant transfer control mechanism.

> **Final Recommendation:** Given that ownership has been renounced, the contract operates in a fully decentralized and immutable state. Token holders should be aware that no administrative functions can be executed, including any potential emergency controls. It is recommended to ensure all external integrations and users are aware of this immutable nature and the implications for any future changes or emergency actions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract architecture (7.1 Architecture) is a standard ERC-20 implementation, providing core token functionalities (7.2 Code Security) such as `transfer`, `transferFrom`, `balanceOf`, and… |
| **Governance / Economics** | 10/10 | Low | The contract's ownership has been renounced on-chain (7.5 Governance), setting the `_owner` address to zero. This decentralizes control by preventing any single entity from calling `onlyOwner`… |
| **Upgrades** | 10/10 | Low | This contract is not implemented as an upgradeable proxy (7.7 Upgrades). Therefore, there are no upgrade-related risks such as proxy misconfigurations or implementation logic flaws during upgrades.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_⚪ 6 Informational_

### `CP-05` — Dormant Transfer Control Switch  *(Severity: Informational · Status: Unresolved)*

The contract includes a function `setMode` that, if active, would allow a privileged address to change a switch (`_mode`) that dictates whether token transfers are allowed or restricted. However, the contract's ownership has been renounced, meaning the `onlyOwner` restriction on `setMode` makes this function permanently inactive. No one can currently call `setMode` to alter transfer rules.

**Recommendation:** No action is required as the ownership renunciation has effectively mitigated any potential centralized control over transfers. This finding serves as an informational note about a feature that is present in the code but no longer functional.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 26.0% of supply. Of that, 7.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 14.8% in wallets, 4.2% in other contracts. 4,925 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as CrypstocksAI (MVP), market cap $1M, rank #2936. 4,925 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.5% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $165K (DexScreener, all pools). 24h trading volume $703K (CoinGecko, all markets, daily snapshot). 24h trading volume $1.0M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0227 on 2025-06-30; the price is now 95.1082% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on four.meme, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $165K of DEX liquidity across 2 pools. Launch: launched on four.meme, 508 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2d2d...4444`](https://bscscan.com/address/0x2d2d8449ec0bb78c497c36ffaac583dff4bd4444) |
| **Network** | BNB Chain |
| **Price** | $0.001173 |
| **24h Volume** | $1.01M |
| **Liquidity** | $164.8K |
| **Volume / Liquidity** | 6.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 26.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1643 buys / 1122 sells |

## Security Flags (5/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0xdbe36fc6ef1b51dd71fdbd136a03f413b83327aa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/crypstocksai-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-30*
