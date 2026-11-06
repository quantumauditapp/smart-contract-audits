---
token: Hims & Hers Health, Inc.
ticker: HIMSC
network: base
risk_score: 55
status: medium
date: 2026-11-06
---

# Hims & Hers Health, Inc. (HIMSC) — Smart Contract Security Analysis | Base

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hims-hers-health-inc-base)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is inaccessible for security analysis. Investors should exercise extreme caution as unverified contracts lack transparency regarding ownership, tax mechanisms, and potential backdoors.

> **Final Recommendation:** Do not interact with this contract. Without verified source code, there is no way to ensure the safety of funds or the integrity of the contract logic. Users should prioritize projects that provide fully verified source code on block explorers.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | 7.1 Architecture: Unknown. 7.2 Code Security: Cannot be verified. 7.3 Access Control: Cannot be verified. 7.6 External: Cannot be verified. The absence of source code prevents any assessment of… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic: Cannot be verified. 7.5 Governance: Cannot be verified. 7.8 Operations: Cannot be verified. Without source code, it is impossible to determine if there are hidden minting functions… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades: Cannot be verified. It is impossible to determine if the contract is immutable or if it contains proxy patterns that allow for arbitrary logic updates by the deployer. |

## Security Findings

_🔴 1 Critical · ⚪ 3 Informational_

### `C-01` — Unverified Contract Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not verified on the Base block explorer, rendering it a 'black box'. This prevents any security audit or verification of contract behavior.

**Recommendation:** Verify the contract source code on the block explorer to allow for transparency and community due diligence.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Hims & Hers Health, Inc. (Coinbase Tokenized Stock) (HIMSC), rank #7262.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $237K (DexScreener, all pools). 24h trading volume $200K (CoinGecko, all markets, daily snapshot). 24h trading volume $519K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $237K of DEX liquidity across 7 pools. Launch: 37 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xb200...f336`](https://basescan.org/address/0xb20000000000000000000043a599976181bcf336) |
| **Network** | Base |
| **Price** | $26.0920 |
| **24h Volume** | $518.3K |
| **Liquidity** | $236.0K |
| **Volume / Liquidity** | 2.2× |
| **Token Age** | 1mo |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1775 buys / 1939 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x41d7793faa4ca181b6f021423ff3f9015c00b2ff)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hims-hers-health-inc-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
