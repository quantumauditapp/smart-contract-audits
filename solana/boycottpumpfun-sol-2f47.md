---
token: BOYCOTTPUMPFUN
ticker: BPF
network: solana
risk_score: 15
status: low
date: 2026-10-27
---

# BOYCOTTPUMPFUN (BPF) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/boycottpumpfun-sol-2f47)

---

## Audit Summary

The BOYCOTTPUMPFUN token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully locked, mitigating rug-pull risks, though the token metadata remains mutable and liquidity is currently low. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Monitor the token's liquidity levels, as the current depth may result in significant slippage for larger trades. Verify the token metadata on-chain before interacting to ensure the branding matches expectations, as the metadata is currently mutable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the SPL Token-2022 program. 7.1 Architecture is standard for SPL mints. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.2 Code Security is… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic factors show $9,360 in liquidity, which is below the $10,000 threshold. 7.6 External data indicates 100% of liquidity is locked, preventing creator withdrawal. 7.5 Governance and holder… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints in the EVM sense. 7.8 Operations are limited by the revocation of authorities. Metadata remains mutable, allowing for potential branding changes. |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $9,360. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Monitor liquidity depth before executing large trades.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `L-01` — Third-Party Registry Warning  *(Severity: Low · Status: Unresolved)*

A third-party risk registry flagged the token for low liquidity and a low number of LP providers.

**Recommendation:** Exercise caution due to the limited market participation.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $14K (DexScreener, all pools). 24h trading volume $79K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $14K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3PKWCX...mc58`](https://solscan.io/account/3PKWCXr94x14tsUZKzmmGqexCEtmhFedNVPVMhRJmc58) |
| **Network** | Solana |
| **Price** | $0.00004953 |
| **24h Volume** | $78.4K |
| **Liquidity** | $14.0K |
| **Volume / Liquidity** | 5.6× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1226 buys / 636 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2t2ufphxrbq2jreseelhq4w6woujwmxeqnz3rnupc3tg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/boycottpumpfun-sol-2f47)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
