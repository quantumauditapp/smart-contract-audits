---
token: Fomopad
ticker: FOMOPAD
network: solana
risk_score: 18
status: low
date: 2026-10-26
---

# Fomopad (FOMOPAD) — Smart Contract Security Analysis | Solana

> **Risk Score: 18/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fomopad-sol)

---

## Audit Summary

Fomopad is a Token-2022 asset with both mint and freeze authorities successfully revoked. Liquidity is fully locked, mitigating rug-pull risks, though metadata remains mutable. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should verify the current metadata on-chain to ensure it matches expected branding, as the metadata is mutable. Monitor the token's liquidity and volume on-chain to ensure market conditions remain stable given the high volume-to-liquidity ratio.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Security is robust due to the revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks or default frozen… |
| **Governance / Economics** | 9/10 | Low | Liquidity is fully secured with 100% of the pool locked in a third-party locker (7.4 Economic). Trading volume is active, though the volume/liquidity ratio of 16.45 warrants monitoring for potential… |
| **Upgrades** | 10/10 | Low | The mint is immutable regarding supply and freeze capabilities (7.7 Upgrades). Metadata remains mutable, allowing for potential changes to the token's name or branding (7.8 Operations). No other… |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is currently mutable, meaning the issuer can change these details at any time.

**Recommendation:** Verify the token metadata on-chain before interacting to ensure it aligns with the project's official branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $31K (DexScreener, all pools). 24h trading volume $414K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $31K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HEPG65...STNK`](https://solscan.io/account/HEPG65DZHGePLKrTqkkkJLUb7vt9A2436kdTxTJSSTNK) |
| **Network** | Solana |
| **Price** | $0.0001159 |
| **24h Volume** | $405.9K |
| **Liquidity** | $30.1K |
| **Volume / Liquidity** | 13.5× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5877 buys / 4098 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7fk5ejhyggzjhfqoevnvcaig366uohk9de8ejfkjxotk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fomopad-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
