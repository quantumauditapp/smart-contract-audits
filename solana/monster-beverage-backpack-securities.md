---
token: Monster Beverage - Backpack Securities
ticker: MNST
network: solana
risk_score: 74
status: high
date: 2026-11-06
---

# Monster Beverage - Backpack Securities (MNST) — Smart Contract Security Analysis | Solana

> **Risk Score: 74/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/monster-beverage-backpack-securities-sol)

---

## Audit Summary

The token is highly centralized, with the mint authority, freeze authority, and a permanent delegate all remaining active. These authorities allow the issuer to mint unlimited supply, freeze any user's assets, and transfer tokens from any wallet without consent. Holder distribution data is unavailable, and metadata remains mutable.

> **Final Recommendation:** Investors should exercise extreme caution due to the presence of a permanent delegate and active freeze authority. Verify the revocation of these authorities via a block explorer before considering any long-term position.

Monitor the mint address for authority revocation transactions. If the authorities remain active, the token should be treated as a fully custodial asset controlled by the issuer.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token utilizes the Token-2022 program, which enables advanced extensions. 7.1 Architecture relies on the SPL-2022 standard. 7.3 Access Control is currently compromised by active mint and freeze… |
| **Governance / Economics** | 2/10 | High | 7.4 Economic stability is supported by $117,414 in liquidity and a healthy 4.28 volume/liquidity ratio. 7.5 Governance is non-existent as all control rests with the identified authorities. Holder… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are not applicable to the mint itself, but 7.3 Access Control allows for ongoing modifications to metadata. The metadata is currently mutable, allowing for potential branding changes. No… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is GRgn7aD3tqdL7aua5o1Evj8ri8SUoKvQw653h2UytP4y. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is 2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply; change any holder's balance (seize or credit tokens); freeze or blacklist individual addresses; change the token's name, symbol and image. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

The balance_mutable flag is set to True, indicating an authority can adjust user balances.

**Recommendation:** Monitor the token program account for balance adjustment events.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $361K (DexScreener, all pools). 24h trading volume $5.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $361K of DEX liquidity across 29 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`MNSTy4...zxr2`](https://solscan.io/account/MNSTy46haEN7sEaeXAWBXG6zHaRikCvqf3krAEDzxr2) |
| **Network** | Solana |
| **Price** | $45.7200 |
| **24h Volume** | $433.6K |
| **Liquidity** | $118.5K |
| **Volume / Liquidity** | 3.7× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3384 buys / 2232 sells |

## Security Flags (2/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/2uqzs7vqsqacpy4fyuqgpgsbo94ulnxkdpkn9x1vvfhz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/monster-beverage-backpack-securities-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
