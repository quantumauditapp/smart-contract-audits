---
token: Ginnan Doge's Brother
ticker: GINNAN
network: ethereum
risk_score: 51
status: medium
date: 2026-10-26
---

# Ginnan Doge's Brother (GINNAN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 51/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ginnan-doges-brother-eth)

---

## Audit Summary

The GINNAN token is a standard ERC-20 implementation with added tax and transfer restriction features. Ownership has been renounced, effectively disabling administrative functions that were previously restricted to the owner. However, a tax wallet remains capable of modifying fees and executing token swaps, which introduces centralized control over the token's economic parameters.

> **Final Recommendation:** Investors should be aware that the tax wallet retains the ability to adjust fees and perform manual swaps, which directly impacts the token's economic utility. While ownership is renounced, the centralized control over the tax wallet should be monitored for potential changes in fee structures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract follows standard ERC-20 patterns with additional logic for tax collection and transaction limits. 7.1 Architecture is straightforward, though 7.2 Code Security is impacted by the use of… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance aspects are centralized under the tax wallet. The tax wallet can unilaterally adjust fees via reduceFee and trigger liquidity swaps via manualSwap. While ownership is… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the contract is not a proxy. The logic is immutable, providing certainty to holders regarding the contract's operational rules. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 4 Medium · ⚪ 6 Informational_

### `CD-01` — Use of tx.origin for Authorization  *(Severity: Medium · Status: Unresolved)*

The _transfer function uses tx.origin, which can be exploited if users interact with malicious smart contracts that initiate transfers on their behalf.

**Recommendation:** Replace tx.origin with _msgSender() to ensure that the immediate caller is correctly identified and to prevent potential authorization bypasses.


### `CP-05` — Centralized Control over Transfer Logic  *(Severity: Medium · Status: Unresolved)*

The tax wallet can trigger manualSwap and the owner (now renounced) could call removeLimits, which alters the fundamental transfer rules of the token. This allows the controller to potentially halt or modify the conditions under which tokens can be transferred.

**Recommendation:** Ensure that any future economic adjustments are transparent and communicated to the community, as these functions directly impact token liquidity.


### `CP-07` — Variable Tax Fees  *(Severity: Medium · Status: Unresolved)*

The tax wallet can call reduceFee to change the buy and sell taxes. This allows the controller to influence the cost of trading the token at any time.

**Recommendation:** Implement a timelock or a multi-sig wallet for the tax wallet to prevent unilateral fee changes.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $43K (DexScreener, all pools). 24h trading volume $319 (CoinGecko, all markets, daily snapshot). 24h trading volume $150K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $5.27e-05 on 2024-09-21; the price is now 99.2426% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `CP-06` — Blacklist Functionality  *(Severity: Informational · Status: Unresolved)*

The contract contains addBots and delBots functions that allow the owner to block specific addresses from transferring tokens. Since ownership is renounced, these functions are currently dormant.

**Recommendation:** No action required as ownership is renounced, but users should be aware that this logic exists in the bytecode.


### `CP-08` — Configurable Transaction Limits  *(Severity: Informational · Status: Unresolved)*

The contract includes logic for transaction and wallet size limits that could be modified by the owner. These functions are now inaccessible due to ownership renouncement.

**Recommendation:** None, as the functions are effectively disabled.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 69.3% of supply. Of that, 49.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.1% in wallets, 10.8% in other contracts. 2,124 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Ginnan Doge's Brother (GINNAN), rank #6950. 2,124 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $43K of DEX liquidity across 2 pools. Launch: 819 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x375e...757c`](https://etherscan.io/address/0x375e104af98872e5b4fe951919e504a47db1757c) |
| **Network** | Ethereum |
| **Price** | $0.00000045 |
| **24h Volume** | $150.1K |
| **Liquidity** | $42.7K |
| **Volume / Liquidity** | 3.5× |
| **Token Age** | 2y |
| **Top-10 Holders** | 69.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 222 buys / 179 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xa5d739430718451756a7c97254939cbdd25a83ec)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ginnan-doges-brother-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
