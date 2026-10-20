---
token: Superior Intelligence
ticker: SI
network: ethereum
risk_score: 43
status: medium
date: 2026-09-30
---

# Superior Intelligence (SI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/superior-intelligence-eth)

---

## Audit Summary

This audit covers an ERC-20 token contract. The contract implements standard token functionalities and includes several privileged functions. Ownership of the contract has been renounced, making some administrative functions dormant. However, a designated `taxwallet` address retains significant control over transfer mechanisms, including the ability to halt transfers, modify transaction fees, and rescue ERC-20 tokens.

> **Final Recommendation:** Token holders should be fully aware of the significant control vested in the `taxwallet` address. It is strongly recommended that the `taxwallet` be secured by a multi-signature wallet or a robust governance mechanism to prevent single-point-of-failure risks and ensure transparency. Consider implementing a timelock for critical `taxwallet` functions to provide users with advance notice of changes. Regular communication from the project team regarding the `taxwallet`'s operations and any planned changes to fees or transfer rules is advisable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract is an ERC-20 token with standard functionalities (7.2 Code Security). It includes several administrative functions, some of which were restricted to the `owner` and are now dormant due… |
| **Governance / Economics** | 8/10 | Low | The economic parameters of the token, such as transfer taxes (`_transferTax`, `_finalBuyTax`, `_finalSellTax`) and transfer limits (`_maxTxAmount`, `_maxWalletSize`), are present (7.4 Economic).… |
| **Upgrades** | 8/10 | Low | The contract is a standard, non-proxy implementation of an ERC-20 token (7.1 Architecture). It does not incorporate any upgradeability patterns (7.7 Upgrades), meaning its logic is immutable once… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 99.2% (≈ permanent lock) |
| **LP Locked** | 99.2% — Null Address |

## Security Findings

_🟡 2 Medium · ⚪ 6 Informational_

### `CP-05` — A privileged address controls a switch that decides whether transfers go through  *(Severity: Medium · Status: Unresolved)*

An on/off setting checked in the transfer path can be changed by a privileged function; depending on its value, transfers or sales are allowed or refused. Functions: manualSwap. Restricted to: taxwallet.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `CP-07` — A privileged address can change the transfer fee  *(Severity: Medium · Status: Unresolved)*

The fee taken from transfers is a setting a privileged function can change. Functions: removeTransferTax, reduceFee. Restricted to: owner, taxwallet.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `CP-08` — A privileged address can change transfer or wallet limits  *(Severity: Informational · Status: Unresolved)*

Numeric limits checked in the transfer path (maximum transaction or wallet size, thresholds) can be changed by a privileged function. Ownership is renounced, so no one can call these functions now. Functions: removeLimits. Restricted to: owner.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 52.2% of supply. Of that, 29.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 11.1% in wallets, 11.5% in other contracts. 774 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Superior Intelligence (SI), rank #7609. 774 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

99.2% of the pool's LP is burned or time-locked. 99.2% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. 0.8% is held, unlocked, by 1 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $20K (DexScreener, all pools). 24h trading volume $43K (CoinGecko, all markets, daily snapshot). 24h trading volume $54K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: AI Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $20K of DEX liquidity across 2 pools. Launch: 157 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x9113...d07b`](https://etherscan.io/address/0x91139d452c144486d49b388509e459ab8748d07b) |
| **Network** | Ethereum |
| **Price** | $0.00000008 |
| **24h Volume** | $54.4K |
| **Liquidity** | $20.0K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 52.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 180 buys / 140 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0xb50726fac0bd357a0af9e4b8b1f3690327a69a48)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/superior-intelligence-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-30*
