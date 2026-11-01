---
token: 1win Token
ticker: 1WIN
network: solana
risk_score: 53
status: medium
date: 2026-11-01
---

# 1win Token (1WIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 53/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/1win-token-sol)

---

## Audit Summary

The 1win Token (1WIN) presents significant security risks primarily due to an active freeze authority and high holder concentration. While the mint authority is revoked, the freeze authority remains active, allowing for potential account-level restrictions. Third-party registry data indicates high-risk flags regarding developer history and ownership distribution.

> **Final Recommendation:** Investors should exercise extreme caution due to the active freeze authority. Verify the intent of the freeze authority holder before interacting with the token. Monitor the top 10 holder wallets for signs of coordinated liquidation, as the high concentration poses a significant risk of price manipulation.

Perform on-chain verification of the freeze authority status periodically. Avoid holding large positions in this asset given the lack of locked liquidity and the potential for the freeze authority to restrict access to funds.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture is standard for SPL mints, while 7.3 Access Control is compromised by the active freeze authority… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic risk is high due to 88.92% concentration among the top 10 holders. 7.6 External signals indicate high-risk flags from third-party registries. Liquidity is $118,185, and the pair is 0… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable to SPL mints in the EVM sense. Metadata is mutable, allowing for potential branding changes post-launch. The mint authority is successfully revoked, preventing further… |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 2 Medium · ⚪ 5 Informational_

### `C-01` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is G68zSDguycN8BfZLtpQRBDbkBaw62aaMV5EpdoaqsEVm. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 88.92% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor top holder activity and consider the impact of large sell orders on market stability.


### `H-02` — Flagged High-Risk by Third-Party Registry  *(Severity: High · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset (developer history, LP movements).

**Recommendation:** Do not interact with this token.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — the freeze authority — freeze or blacklist individual addresses; change the token's name, symbol and image. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 88.9% of supply. What remains: 14.4% in wallets, 74.5% in other contracts. 3,951 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,951 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $404K (DexScreener, all pools). 24h trading volume $3.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $404K of DEX liquidity across 29 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FjPKUG...1win`](https://solscan.io/account/FjPKUGnF5zBpdEv18gT8FJCtxh3MKrFkoeYekgYr1win) |
| **Network** | Solana |
| **Price** | $0.05734 |
| **24h Volume** | $1.79M |
| **Liquidity** | $141.8K |
| **Volume / Liquidity** | 12.6× |
| **Token Age** | 17h |
| **Top-10 Holders** | 88.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3158 buys / 2759 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/e8eq1j7r1eaknrfkfktrtuaefbrw5rzcjgl7kzj3wnf3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/1win-token-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
