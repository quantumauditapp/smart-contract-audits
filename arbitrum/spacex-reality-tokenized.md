---
token: SpaceX (Reality Tokenized)
ticker: RSPCX
network: arbitrum
risk_score: 48
status: medium
date: 2026-10-20
---

# SpaceX (Reality Tokenized) (RSPCX) — Smart Contract Security Analysis | Arbitrum

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-reality-tokenized-arb)

---

## Audit Summary

The contract is a standard BeaconProxy implementation used to delegate calls to an implementation contract. The architecture follows established patterns for upgradeable proxies. No vulnerabilities were identified in the static analysis of the proxy logic itself, though the security of the system depends entirely on the implementation contract and the beacon address.

> **Final Recommendation:** Ensure that the beacon contract is governed by a secure, multi-signature wallet or a decentralized governance mechanism to prevent unauthorized implementation changes. Regularly audit the implementation contract, as the proxy's security is entirely dependent on the code it delegates to.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes a standard BeaconProxy pattern, ensuring clean separation between proxy storage and logic. 7.1 Architecture is robust, relying on a beacon to resolve implementation addresses.… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic and 7.5 Governance factors are not applicable to this proxy contract as it holds no assets and contains no governance logic. The contract serves only as a transparent interface for the… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are handled via the Beacon pattern, which allows for atomic updates across multiple proxy instances. This is a secure and efficient way to manage contract evolution. 7.8 Operations are… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Beacon |
| **Implementation** | ⚠️ Unverified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 5 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.9% of supply. Of that, 0.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 99.2% in wallets, 0.0% in other contracts. 136 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as SpaceX Tokenized Stock (Reality) (RSPCX), market cap $15M, rank #954. Its admin (0xe656…bcbb) controls 674 issuer-backed coins CoinGecko lists on arbitrum, $155M together, among them Circle Internet Group Tokenized Stock (Reality), SanDisk Tokenized Stock (Reality), Strategy Tokenized Stock (Reality): one issuer's programme, read on-chain. 136 holders. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $203K (DexScreener, all pools). 24h trading volume $146K (CoinGecko, all markets, daily snapshot). 24h trading volume $34K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $203K of DEX liquidity across 1 pools. Launch: 35 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5181...2f44`](https://arbiscan.io/address/0x5181b7dd097b42d7787ee78efab86f43d4e12f44) |
| **Network** | Arbitrum |
| **Price** | $152.6300 |
| **24h Volume** | $33.8K |
| **Liquidity** | $203.1K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 99.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 359 buys / 362 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/arbitrum/0xe072110fbaec692284b4038e196b7fdb2c96ff58)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-reality-tokenized-arb)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
