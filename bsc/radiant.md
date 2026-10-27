---
token: Radiant
ticker: RDNT
network: bsc
risk_score: 11
status: low
date: 2026-10-08
---

# Radiant (RDNT) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 11/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/radiant-bsc)

---

## Audit Summary

The RadiantOFT contract is an ERC-20 token with LayerZero cross-chain functionality. It is owned by a multisig wallet. The audit identified a medium-severity issue related to token minting by the owner and a low-severity issue concerning potential rounding loss in fee calculation. The contract is not upgradeable.

> **Final Recommendation:** It is recommended to carefully review and restrict the capabilities of the `sendAndCall` function to prevent unauthorized token minting, or ensure robust governance procedures are in place for its execution. Additionally, consider reordering operations in `getBridgeFee` to perform multiplication before division to avoid potential rounding losses. Maintain strong security practices for the multisig wallet controlling the contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The RadiantOFT contract implements the ERC-20 standard and integrates LayerZero for cross-chain functionality, enabling token transfers across different chains (7.1 Architecture). The contract… |
| **Governance / Economics** | 9/10 | Low | The contract's ownership is retained by a multisig wallet, which enhances security by requiring multiple approvals for critical operations (7.5 Governance). The owner has significant control over… |
| **Upgrades** | 10/10 | Low | The RadiantOFT contract is not designed with an explicit upgrade mechanism (7.7 Upgrades). This means its logic cannot be changed post-deployment, providing immutability but requiring a new… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 67.6% |
| **Top-3 Unlocked** | ⚠️ 92.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $136K (DexScreener, all pools). 24h trading volume $4.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $976K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.585 on 2022-09-16; the price is now 99.8371% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `CD-01` — Potential rounding loss in bridge fee calculation  *(Severity: Low · Status: Unresolved)*

The `getBridgeFee` function calculates fees by performing division before multiplication. In Solidity, integer division truncates decimals, which can lead to a small loss of precision or rounding down of the fee amount. While typically minor, this can accumulate over many transactions.

**Recommendation:** Token holders should note that small rounding losses might occur during bridge fee calculations. The project team should consider reordering the operations in the `getBridgeFee` function to perform multiplication before division (e.g., `(amount * numerator) / denominator`) to minimize or eliminate these rounding losses and ensure more accurate fee collection.


### `CP-01` — Owner can mint new tokens  *(Severity: Informational · Status: Unresolved)*

The `sendAndCall` function, which is controlled by the contract owner (a multisig wallet), has the capability to increase the total supply of tokens. This means the owner can create new tokens at will, potentially diluting the value for existing token holders.

**Recommendation:** Token holders should be aware that the multisig wallet controlling the contract can mint new tokens using the `sendAndCall` function. It is recommended that the project team implements strict governance policies and transparency around the use of this function, or explores technical solutions to remove or restrict this minting capability if it's not intended for ongoing use.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 82.5% of supply. Of that, 19.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 59.9% in wallets, 2.7% in other contracts. 150,870 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Radiant Capital (RDNT), rank #3237. Traded on Binance. 150,870 holders. Verified by: exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: a copy of the coin from its home chain (arbitrum-one), minted here by LayerZero (lzReceive). Tokenomics — Supply: minted here by LayerZero (lzReceive) against tokens locked or burned on other chains. Control: a 4-of-11 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $136K of DEX liquidity across 18 pools. Launch: 1290 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf7de...84df`](https://bscscan.com/address/0xf7de7e8a6bd59ed41a4b5fe50278b3b7f31384df) |
| **Network** | BNB Chain |
| **Price** | $0.00091 |
| **24h Volume** | $960.6K |
| **Liquidity** | $131.5K |
| **Volume / Liquidity** | 7.3× |
| **Token Age** | 3y |
| **Top-10 Holders** | 82.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10656 buys / 10409 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x346575fc7f07e6994d76199e41d13dc1575322e1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/radiant-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
