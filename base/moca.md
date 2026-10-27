---
token: Moca
ticker: MOCA
network: base
risk_score: 9
status: low
date: 2026-10-09
---

# Moca (MOCA) — Smart Contract Security Analysis | Base

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/moca-base)

---

## Audit Summary

The MocaOFT contract is an Omnichain Fungible Token (OFT) designed for cross-chain transfers using LayerZero. It implements standard ERC-20 functionalities alongside specific administrative controls for managing its cross-chain operations. The audit identified one medium-severity issue related to privileged token minting, which could dilute existing token holders if misused. All other aspects appear to be well-structured and follow established patterns.

> **Final Recommendation:** Token holders should be aware of the administrative controls, particularly the multisig ownership and its ability to manage cross-chain operations. It is crucial for the multisig signers to maintain strong operational security practices to prevent unauthorized access to privileged functions. The team should ensure that the privileged addresses capable of minting tokens are highly secured and that their operations are transparently communicated to the community, including any policies or limits on token minting.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The MocaOFT contract implements an Omnichain Fungible Token (OFT) using LayerZero, enabling cross-chain token transfers (7.1 Architecture). It includes standard ERC-20 functions and a robust set of… |
| **Governance / Economics** | 9/10 | Low | Ownership of the MocaOFT contract is retained by a 2/3 multisig, which provides a good level of decentralization for administrative actions (7.5 Governance). The owner has extensive control over… |
| **Upgrades** | 10/10 | Low | The MocaOFT contract is not implemented as an upgradeable proxy (7.7 Upgrades). This means its logic cannot be changed after deployment, eliminating risks associated with upgrade mechanisms such as… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 49.9% |
| **Top-3 Unlocked** | ⚠️ 99.5% |

## Security Findings

_⚪ 5 Informational_

### `CP-01` — Privileged Addresses Can Mint New Tokens  *(Severity: Informational · Status: Unresolved)*

The MocaOFT contract allows certain privileged addresses to create new tokens. Specifically, the `lzReceiveSimulate`, `lzReceive`, and `send` functions can increase the total supply of MocaOFT tokens. The `lzReceive` function is restricted to the LayerZero endpoint, and the `send` function is restricted to whitelisted addresses. The `lzReceiveSimulate` function, also capable of minting, is similarly controlled by privileged entities involved in cross-chain operations. If these privileged addresses are compromised or misused, they could mint an arbitrary amount of new tokens, diluting the value of existing token holders' assets.

**Recommendation:** Token holders should understand that the contract design includes a mechanism for token minting by specific privileged entities for cross-chain operations. While this is often necessary for OFT functionality, it introduces a centralization risk. Ensure that the addresses designated as the LayerZero endpoint and whitelisted senders, as well as any controllers of `lzReceiveSimulate`, are highly secured, ideally controlled by a robust multi-signature wallet or a well-audited governance process. Th…


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 74.7% of supply. What remains: 34.7% in wallets, 40.0% in other contracts. 657,148 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Moca Network (MOCA), market cap $37M, rank #562. 657,148 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $331K (DexScreener, all pools). 24h trading volume $2.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $111K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.477 on 2024-12-24; the price is now 98.0257% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: a copy of the coin from its home chain (ethereum), minted here by LayerZero (lzReceive). Tokenomics — Supply: mintable with no on-chain cap found. Control: a 2-of-3 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $331K of DEX liquidity across 4 pools. Launch: 365 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2b11...884d`](https://basescan.org/address/0x2b11834ed1feaed4b4b3a86a6f571315e25a884d) |
| **Network** | Base |
| **Price** | $0.009449 |
| **24h Volume** | $59.1K |
| **Liquidity** | $187.2K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 74.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 217 buys / 345 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xdc55a0291029665fecff5ca5add0e51dd2964877)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/moca-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*
