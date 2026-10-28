---
token: Unity USD
ticker: UUSD
network: bsc
risk_score: 10
status: low
date: 2026-10-28
---

# Unity USD (UUSD) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/unity-usd-bsc)

---

## Audit Summary

The UUSD contract is a standard ERC-20 implementation utilizing the Transparent Proxy pattern. It includes administrative controls for minting, pausing, and account freezing. The protocol relies on a 4-of-7 multisig for ownership, which provides a strong security baseline for administrative actions.

> **Final Recommendation:** The protocol should maintain the current multisig configuration and ensure that the keys are distributed across geographically and organizationally diverse signers. Transparency regarding the criteria for account freezing should be provided to users to mitigate concerns regarding centralized control.

Regular audits of the implementation contract should be conducted prior to any proxy upgrades. Ensure that the multisig signers follow strict operational security protocols to prevent key compromise.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The architecture follows industry-standard OpenZeppelin patterns for upgradeable tokens. 7.1 Architecture and 7.2 Code Security are robust, utilizing well-audited libraries for ERC-20 and EIP-712… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance rely on centralized multisig control. While the 4-of-7 multisig mitigates single-point-of-failure risks, the ability to freeze accounts and mint tokens creates… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are managed via a Transparent Proxy pattern with a dedicated ProxyAdmin. This ensures that logic updates are controlled by the multisig, preventing unauthorized implementation changes.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 5 Informational_

### `CP-06` — Centralized Control Over Account Transfers  *(Severity: Informational · Status: Unresolved)*

The contract includes 'freeze' and 'unfreeze' functions that allow the admin or owner to block specific addresses from transferring or selling their tokens. This grants the controller the power to censor individual users.

**Recommendation:** Implement a time-lock or a multi-step governance process for freezing accounts to prevent unilateral or malicious actions by a single compromised admin key.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 90.5% of supply. Of that, 6.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.0% in wallets, 84.5% in other contracts. 103,034 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Unity USD (UUSD), market cap $100M, rank #277. 103,034 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $31.7M (DexScreener, all pools). 24h trading volume $2.6M (CoinGecko, all markets, daily snapshot). 24h trading volume $909K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Stablecoin — synthetic  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Stablecoins. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: a 4-of-7 multisig. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $31.7M of DEX liquidity across 30 pools. Launch: 243 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x61a1...0000`](https://bscscan.com/address/0x61a10e8556bed032ea176330e7f17d6a12a10000) |
| **Network** | BNB Chain |
| **Price** | $1.0006 |
| **24h Volume** | $697.3K |
| **Liquidity** | $14.70M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 90.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16964 buys / 382 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x1c3865814acbba11e7196df0b46c024472503196)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/unity-usd-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*
