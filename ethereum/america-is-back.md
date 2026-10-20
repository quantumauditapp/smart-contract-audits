---
token: America is Back
ticker: AIB
network: ethereum
risk_score: 38
status: medium
date: 2026-10-12
---

# America is Back (AIB) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/america-is-back-eth)

---

## Audit Summary

The AIB token is an ERC-20 standard compliant token. Ownership of the contract has been renounced, meaning many privileged functions previously controlled by the owner are now dormant. However, a designated `_taxWallet` address retains significant control over transfer fees and liquidity management, posing a medium economic risk. A technical vulnerability related to the use of `tx.origin` in transfer logic was also identified.

> **Final Recommendation:** Token holders should be aware of the significant control retained by the `_taxWallet` address over transfer fees and liquidity operations. It is recommended to monitor actions taken by this address. Additionally, the use of `tx.origin` in the transfer logic is a known anti-pattern that could potentially be exploited in specific scenarios, and users should exercise caution when interacting with the token via untrusted third-party contracts.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract implements standard ERC-20 functionality, ensuring basic token operations. A significant technical concern is the use of `tx.origin` in the `_transfer` function, which can be vulnerable… |
| **Governance / Economics** | 8/10 | Low | The economic model is influenced by the `_taxWallet` address, which can actively change buy and sell transfer fees using `reduceFee()` (CP-07) and manage liquidity through `manualSwap()` and… |
| **Upgrades** | 8/10 | Low | The contract is not designed as an upgradeable proxy, meaning its logic is immutable once deployed. Furthermore, ownership of the contract has been renounced, preventing any future administrative… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 3 Medium · ⚪ 7 Informational_

### `CD-01` — Reliance on tx.origin for Authorization or Rules  *(Severity: Medium · Status: Unresolved)*

The contract's internal `_transfer` function uses `tx.origin` to determine certain rules or authorizations. `tx.origin` refers to the original external account that initiated a transaction, not necessarily the immediate caller. This can be problematic if a malicious contract tricks a user into interacting with it, and that contract then calls the token contract, potentially bypassing intended access controls or rules.

**Recommendation:** Token holders should be aware that the contract's internal transfer logic relies on `tx.origin`. While not always directly exploitable, this pattern is generally discouraged in smart contract development as it can be vulnerable to phishing or relay attacks where an attacker's contract acts as an intermediary.


### `CP-05` — Privileged Address Can Influence Transfer Processing  *(Severity: Medium · Status: Unresolved)*

The `_taxWallet` address has the ability to call the `manualSwap()` function. This function can change an internal state (`inSwap`) that might affect how token transfers are processed, potentially influencing whether transfers or sales are allowed or refused under certain conditions. While the original owner could also disable transfer delays via `removeLimits()`, this is no longer possible due to renounced ownership.

**Recommendation:** Token holders should be aware that the `_taxWallet` has the power to influence transfer processing through the `manualSwap()` function. This introduces a centralized point of control over a critical aspect of token functionality.


### `CP-07` — Privileged Address Can Change Transfer Fees  *(Severity: Medium · Status: Unresolved)*

The `_taxWallet` address can call the `reduceFee()` function to change the `_finalBuyTax` and `_finalSellTax` percentages applied to token transactions. This means the fees taken from buying and selling tokens can be modified by this single address. The original owner also had the ability to remove the general `_transferTax` via `removeTransferTax()`, but this is now dormant.

**Recommendation:** Token holders should be aware that the `_taxWallet` has the ability to modify the buy and sell taxes applied to transactions. This introduces a centralized control point over the token's economic parameters.


### `CP-06` — Ability to Block Individual Holders is Dormant  *(Severity: Informational · Status: Unresolved)*

Previously, the contract owner could add or remove specific addresses from a 'bot' list using the `addBots()` and `delBots()` functions. If an address was on this list, it could be prevented from moving or selling its tokens. However, since ownership has been renounced, no one can call these functions anymore, making this control dormant.

**Recommendation:** This control mechanism is no longer active because the contract's ownership has been permanently renounced. Therefore, there is no active risk of individual holders being blocked by a privileged address.


### `CP-08` — Ability to Change Transfer or Wallet Limits is Dormant  *(Severity: Informational · Status: Unresolved)*

The contract owner previously had the ability to call `removeLimits()` to modify numeric limits such as the maximum transaction amount (`_maxTxAmount`) and the maximum wallet size (`_maxWalletSize`), and to disable `transferDelayEnabled`. However, since ownership has been renounced, no one can call this function anymore, making these controls dormant.

**Recommendation:** This control mechanism is no longer active because the contract's ownership has been permanently renounced. Therefore, there is no active risk of transfer or wallet limits being changed by a privileged address.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 36.3% of supply. Of that, 17.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 8.5% in wallets, 10.4% in other contracts. 2,474 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as America is Back (AIB), rank #4378. 2,474 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $94K (DexScreener, all pools). 24h trading volume $44K (CoinGecko, all markets, daily snapshot). 24h trading volume $48K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.00424 on 2026-05-11; the price is now 93.4392% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $94K of DEX liquidity across 2 pools. Launch: 629 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb3a0...30b6`](https://etherscan.io/address/0xb3a0f70c913aa04404bd177be9e20b47613830b6) |
| **Network** | Ethereum |
| **Price** | $0.0002697 |
| **24h Volume** | $47.6K |
| **Liquidity** | $93.5K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 36.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 78 buys / 39 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x62eae8645b51146d262dca962e3ec00e84946475)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/america-is-back-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
