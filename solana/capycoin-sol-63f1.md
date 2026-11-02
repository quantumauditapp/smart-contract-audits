---
token: Capycoin
ticker: CAPY
network: solana
risk_score: 72
status: high
date: 2026-11-02
---

# Capycoin (CAPY) — Smart Contract Security Analysis | Solana

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/capycoin-sol-63f1)

---

## Audit Summary

Capycoin utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. However, the project exhibits extreme economic risk due to 100% of liquidity being held by the creator and a volume-to-liquidity ratio indicative of wash trading. Holder concentration data was unavailable from the RPC source.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity. Monitor the creator's wallet (2JhRCe…urCV) for any movement of the pool's liquidity, as the entire position can be withdrawn at any time.

Verify the current liquidity status on-chain before any trade. Avoid interacting with the token if the volume-to-liquidity ratio remains at these levels, as it suggests artificial market activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token is deployed via the Token-2022 program, ensuring standard SPL compliance. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic stability is severely compromised by the fact that 100% of pool liquidity is withdrawable by the creator (wallet 2JhRCe…urCV). 7.6 External signals indicate a volume-to-liquidity ratio… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable to SPL mints. Metadata is immutable, and no balance-mutating authorities are present. The token configuration is static and cannot be altered by the creator. |

## Security Findings

_🟠 3 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Pool Creator Can Withdraw Liquidity  *(Severity: High · Status: Unresolved)*

100% of the pool's liquidity is held, unlocked, by the wallet that created the pool (2JhRCe…urCV). It can remove that liquidity at any moment and leave holders unable to sell.

**Recommendation:** Watch that wallet's liquidity position; treat the pool as removable until the liquidity is burned or locked.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 191.14x liquidity, a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for the potential lack of genuine market depth in any swap calculation.


### `QA-LIQUIDITY` — Liquidity withdrawable by the owner/deployer  *(Severity: High · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by the wallet that created this pool (2JhRCe…urCV) — it can pull that liquidity at any moment. This is the rug-pull path.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `M-01` — Low Liquidity  *(Severity: Medium · Status: Unresolved)*

Total DEX liquidity is $45,051. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Ensure trade sizes are small relative to the total liquidity pool.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $43K (DexScreener, all pools). 24h trading volume $7.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $43K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GcuMGT...e5AJ`](https://solscan.io/account/GcuMGTKW4kw6mER4Y5vecNVYVWuN6mZvYVPLw7bXe5AJ) |
| **Network** | Solana |
| **Price** | $0.00005624 |
| **24h Volume** | $7.08M |
| **Liquidity** | $43.0K |
| **Volume / Liquidity** | 164.7× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13760 buys / 11823 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/ggefxuwy2saobsqqbnnlzvuceusnl5ck8qui1jd9ewe4)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/capycoin-sol-63f1)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
