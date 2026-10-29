---
token: PARTI Token
ticker: PARTI
network: base
risk_score: 8
status: low
date: 2026-10-29
---

# PARTI Token (PARTI) — Smart Contract Security Analysis | Base

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/parti-token-base)

---

## Audit Summary

ParticleToken is an omnichain token implementation utilizing LayerZero's OFT standard. The contract architecture is robust, leveraging standard libraries for cross-chain messaging and ERC-20 compliance. The primary risk involves the minting capabilities inherent to the OFT standard, which are necessary for cross-chain functionality but represent a centralized control point.

> **Final Recommendation:** The protocol should maintain the current multisig threshold and ensure that the LayerZero endpoint configuration is monitored for any unauthorized changes. Given the minting capability, periodic audits of the cross-chain messaging configuration are recommended to ensure no misconfigurations allow for unauthorized supply expansion.

Users should be aware that the token supply is dynamic due to the cross-chain nature of the OFT standard. Ensure that the multisig signers are geographically and organizationally distributed to mitigate single-point-of-failure risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract follows industry-standard patterns for cross-chain token transfers (7.1 Architecture). Code security is high due to the use of audited LayerZero OFT libraries (7.2 Code Security). Access… |
| **Governance / Economics** | 9/10 | Low | Economic stability is maintained through standard ERC-20 mechanisms (7.4 Economic). Governance is currently centralized under a 3-of-4 multisig, providing a balance between security and agility (7.5… |
| **Upgrades** | 10/10 | Low | The contract is not currently deployed as a proxy, meaning logic is immutable (7.7 Upgrades). This eliminates risks associated with malicious implementation swaps. Future upgrades would require a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 55.6% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 5 Informational_

### `CP-01` — Privileged Minting via Cross-Chain Messaging  *(Severity: Informational · Status: Unresolved)*

The functions send, lzReceiveSimulate, and lzReceive allow for the minting of new tokens as part of the cross-chain transfer process. While this is required for the OFT standard to function, it allows the LayerZero endpoint to increase the total supply, which could dilute existing holders if the cross-chain bridge is compromised.

**Recommendation:** Monitor the LayerZero endpoint and peer configurations closely. Ensure that only authorized chains are set as peers to prevent unauthorized minting from malicious or compromised chains.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.2% of supply. Of that, 1.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.5% in wallets, 80.5% in other contracts. 12,917 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Particle Network (PARTI), market cap $9M, rank #1339. Traded on Binance. 12,917 holders. Verified by: exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $336K (DexScreener, all pools). 24h trading volume $8.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $324K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.419 on 2025-05-13; the price is now 90.7115% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: a copy of the coin from its home chain (binance-smart-chain), minted here by LayerZero (lzReceive). Tokenomics — Supply: minted here by LayerZero (lzReceive) against tokens locked or burned on other chains. Control: a 3-of-4 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $336K of DEX liquidity across 19 pools. Launch: 584 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5926...0f00`](https://basescan.org/address/0x59264f02d301281f3393e1385c0aefd446eb0f00) |
| **Network** | Base |
| **Price** | $0.05712 |
| **24h Volume** | $323.7K |
| **Liquidity** | $335.8K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 1y |
| **Top-10 Holders** | 97.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2024 buys / 1478 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x9c42751954513c0461481a9600c9d11a059ddd12)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/parti-token-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*
