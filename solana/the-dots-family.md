---
token: The Dots Family
ticker: DOTS
network: solana
risk_score: 17
status: low
date: 2026-10-01
---

# The Dots Family (DOTS) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-dots-family-sol)

---

## Audit Summary

The audit of The Dots Family (DOTS) SPL Token Mint identified a low-severity risk related to mutable metadata. Key authorities such as Mint Authority and Freeze Authority are revoked, indicating a fixed supply and unfreezable accounts. Liquidity is robustly locked, but holder concentration data was unavailable from chain-native RPC.

> **Final Recommendation:** Holders should verify the token's metadata against official sources periodically to ensure branding consistency, especially since the `metadata_mutable` flag is True. Monitor for any changes to the token's name, symbol, or image that could indicate a rebranding or malicious intent. No further on-chain verification steps are required regarding minting or freezing capabilities, as these authorities are permanently revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority are revoked, ensuring that no new tokens can be minted and no existing holder accounts can be… |
| **Governance / Economics** | 9/10 | Low | The token exhibits healthy liquidity with $12,441 USD, and 100.0% of the pool's liquidity is locked for good in Raydium's LP locker, preventing rug pulls. The 24-hour volume of $51,246 USD results in… |
| **Upgrades** | 10/10 | Low | The Mint Authority and Freeze Authority are both revoked, meaning the token's supply and transferability properties are fixed and cannot be altered by any single entity. No Token-2022 extensions like… |

## Security Findings

_🟢 1 Low · ⚪ 6 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by `metadata_mutable: True`.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $51K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $13K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6hatGW...jLoM`](https://solscan.io/account/6hatGWdZbBFuLuicNXGRDStqkGN9mAyfZBTkusUrjLoM) |
| **Network** | Solana |
| **Price** | $0.00001838 |
| **24h Volume** | $50.8K |
| **Liquidity** | $12.9K |
| **Volume / Liquidity** | 3.9× |
| **Token Age** | 19h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 424 buys / 361 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/tvqcrl7npcw5sk2qwgltsnacib3e7gdtzijfvnzmvxi)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-dots-family-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
