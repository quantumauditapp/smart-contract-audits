---
token: Take-Two Interactive Software - Backpack Securities
ticker: TTWO
network: solana
risk_score: 76
status: high
date: 2026-10-20
---

# Take-Two Interactive Software - Backpack Securities (TTWO) — Smart Contract Security Analysis | Solana

> **Risk Score: 76/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/take-two-interactive-software-backpack-securities-sol)

---

## Audit Summary

The token exhibits critical centralization risks due to active Mint, Freeze, and Permanent Delegate authorities. Third-party risk registries have flagged the asset as high-risk due to these administrative controls and the lack of locked liquidity. All sources were successfully retrieved for this assessment.

> **Final Recommendation:** Investors should treat this token as fully custodial due to the Permanent Delegate and active Freeze Authority. Verify the current status of these authorities on-chain before any significant capital allocation.

Monitor the liquidity pool for sudden withdrawals, as the lack of confirmed locking mechanisms poses a risk of liquidity removal. Avoid holding large positions until the Mint and Freeze authorities are revoked to null addresses.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token utilizes the Token-2022 program with active administrative extensions. 7.3 Access Control is compromised by the presence of an active Mint Authority… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic analysis shows $594,002 in liquidity with a 41-day pair age. 7.5 Governance is centralized, as the top 10 holders that can sell control 14.28% of the supply, while the pool creator's… |
| **Upgrades** | 1/10 | High | 7.7 Upgrades are not applicable in the EVM sense, but 7.8 Operations are impacted by mutable metadata and authority flags. The metadata is currently mutable, allowing for potential branding changes.… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟠 2 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is CwWGWmE3MLyRmFiLkVsZU9oDyWhF3XtULciqTjj2bNkv. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is 2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `H-01` — Flagged High-Risk by Third-Party Registry  *(Severity: High · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset (developer history, LP movements).

**Recommendation:** Do not interact with this token.


### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply; change any holder's balance (seize or credit tokens); freeze or blacklist individual addresses; change the token's name, symbol and image. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

GoPlus balance_mutable == True (Token-2022). A balance-mutating authority can adjust user balances.

**Recommendation:** Monitor for changes in balance-mutating authority status.


### `M-02` — Pool Liquidity Not Locked  *(Severity: Medium · Status: Unresolved)*

The fact block indicates liquidity is not confirmed as locked, meaning it can be withdrawn by whoever holds the LP tokens.

**Recommendation:** Watch the pool creator's wallet liquidity position; treat the pool as removable until the liquidity is burned or locked.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 52.3% of supply. Of that, 38.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 6.6% in wallets, 7.6% in other contracts. 30,643 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Take-Two Interactive Software (Backpack Securities) (TTWO), market cap $1M, rank #2610. 30,643 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.4M (DexScreener, all pools). 24h trading volume $8.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $10.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.4M of DEX liquidity across 30 pools. Launch: launched on pump.fun (PumpSwap), 74 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`TTWofw...FbKo`](https://solscan.io/account/TTWofwAge91oFhZs7kpQdyrVRkmevgM88xijGvQFbKo) |
| **Network** | Solana |
| **Price** | $205.4000 |
| **24h Volume** | $3.48M |
| **Liquidity** | $594.7K |
| **Volume / Liquidity** | 5.9× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 52.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 17005 buys / 17588 sells |

## Security Flags (2/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/6ptm7mkumtslu7w6dwrmhjat8pnzocgczdkytkehuapl)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/take-two-interactive-software-backpack-securities-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
