---
token: Señor Inteligente
ticker: SÍ
network: solana
risk_score: 38
status: medium
date: 2026-10-07
---

# Señor Inteligente (SÍ) — Smart Contract Security Analysis | Solana

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/senor-inteligente-sol)

---

## Audit Summary

The Señor Inteligente (Sí) token mint exhibits a robust security posture with both mint and freeze authorities revoked, and 100% of its liquidity locked. The primary concern identified is the mutability of token metadata. Holder concentration data was unavailable for analysis.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to ensure supply immutability and account control. Monitor the token's metadata for any unexpected changes, as it is mutable. While liquidity is fully locked, be aware of the 1.00% transfer fee when calculating trade costs.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Señor Inteligente (Sí) token is an SPL Token-2022 mint with a supply of 999,996,762,821,704 tokens and 6 decimals. Both the mint authority and freeze authority have been revoked, ensuring no new… |
| **Governance / Economics** | 8/10 | Low | The token has a total DEX liquidity of $68,275. A significant positive is that 100.0% of the pool's liquidity is locked for good in Raydium's LP locker, meaning it cannot be withdrawn by the pool's… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, preventing any further changes to the token's supply or account freeze status. While the transfer fee is upgradable, the transfer hook is… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token's metadata_mutable flag is set to True. This means that the token's name, symbol, or image can be changed post-launch by an authorized party.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding. Monitor for any unexpected changes to the token's identifying information.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $69K (DexScreener, all pools). 24h trading volume $601K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $69K of DEX liquidity across 3 pools. Launch: 2 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`1BYFCL...9emN`](https://solscan.io/account/1BYFCLiArGnZA6GHXro8WhGX4n1hWk2mwrxbnMY9emN) |
| **Network** | Solana |
| **Price** | $0.0004281 |
| **24h Volume** | $574.1K |
| **Liquidity** | $68.2K |
| **Volume / Liquidity** | 8.4× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4219 buys / 2775 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/7zcasghbcnr3xrgy1vab63qs1n4kruvgdqdpn7ihz4lb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/senor-inteligente-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-07*
