---
token: Bnb Tiger Inu
ticker: BNBTIGER
network: bsc
risk_score: 20
status: low
date: 2026-10-24
---

# Bnb Tiger Inu (BNBTIGER) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bnb-tiger-inu-bsc-c400)

---

## Audit Summary

BNBTiger is a standard ERC-20 token with integrated tax, liquidity, and wallet limit mechanisms. The contract ownership has been renounced, effectively locking all administrative functions and preventing any further modifications to the token's economic parameters or operational logic. The code follows standard patterns for deflationary tokens, and the renouncement significantly reduces the risk of malicious administrative intervention.

> **Final Recommendation:** The contract is in a secure, immutable state due to the renouncement of ownership. No further action is required for the current deployment as the administrative functions are permanently disabled.

Users should verify the current state of the contract on-chain to confirm that the owner address remains set to the zero address before interacting with the protocol.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract implements standard ERC-20 functionality with additional logic for automated liquidity and tax distribution. 7.1 Architecture is straightforward, utilizing a standard router-based swap… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic parameters such as taxes and limits are currently fixed due to the renounced ownership. 7.5 Governance is non-existent as the contract is immutable. 7.6 External dependencies, such as… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not supported by this contract architecture. 7.8 Operations are stable and cannot be altered by any party. The contract is effectively immutable. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | 8.2% |
| **LP Locked** | 98.3% — Null Address, PinkLock02 |
| **Top-1 Unlocked Holder** | 1.7% |

## Security Findings

_⚪ 9 Informational_

### `CP-03` — Dormant Router Redirection Capability  *(Severity: Informational · Status: Unresolved)*

The contract contains a function 'changeRouterVersion' that allows the owner to change the DEX router address. Since ownership is renounced, this function is now permanently inaccessible.

**Recommendation:** No action required as the function is effectively disabled.


### `CP-05` — Dormant Operational Switches  *(Severity: Informational · Status: Unresolved)*

Functions like 'enableDisableWalletLimit' and 'setSwapAndLiquifyEnabled' control critical operational switches. These are now permanently locked in their current state due to ownership renouncement.

**Recommendation:** No action required as the functions are effectively disabled.


### `CP-07` — Dormant Tax Configuration  *(Severity: Informational · Status: Unresolved)*

Functions for adjusting buy/sell taxes and distribution shares are present but cannot be called because ownership has been renounced.

**Recommendation:** No action required as the functions are effectively disabled.


### `CP-08` — Dormant Limit Adjustments  *(Severity: Informational · Status: Unresolved)*

Functions 'setWalletLimit' and 'setMaxTxAmount' allow for modifying transaction and wallet limits. These are now permanently inaccessible due to ownership renouncement.

**Recommendation:** No action required as the functions are effectively disabled.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 73.3% of supply. Of that, 43.2% burned, 5.0% locked, 15.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.0% in wallets, 1.0% in other contracts. 32,213 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as BNB Tiger Inu (BNBTIGER), market cap $1M, rank #2623. 32,213 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity time-locked  *(Severity: Informational · Status: Acknowledged)*

98.3% of the pool's LP is burned or time-locked. 8.2% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 90.1% is locked in PinkLock02 until 01 Sep 2029 (1042 days). Until then nobody — the project included — can withdraw it unless the locker contract itself is flawed; after that date the lock's owner can. 1.7% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $946K (DexScreener, all pools). 24h trading volume $372 (CoinGecko, all markets, daily snapshot). 24h trading volume $174K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 7% on buy, 7% on sell. Market: $946K of DEX liquidity across 5 pools. Launch: 418 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf858...4cb5`](https://bscscan.com/address/0xf8584516b7d2c156c763c874d6813e06b57e4cb5) |
| **Network** | BNB Chain |
| **Price** | $0. |
| **24h Volume** | $171.8K |
| **Liquidity** | $939.6K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 73.3% of supply |
| **Buy / Sell Tax** | 7.0% / 7.0% |
| **24h Transactions** | 173 buys / 83 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x95073d7b958f6a4ccc46fab5154997fe819695d9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bnb-tiger-inu-bsc-c400)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
