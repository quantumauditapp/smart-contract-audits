---
token: mint
ticker: MINT
network: solana
risk_score: 70
status: high
date: 2026-10-23
---

# mint (MINT) — Smart Contract Security Analysis | Solana

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mint-sol)

---

## Audit Summary

The token mint is currently at high risk due to an active mint authority and suspicious trading patterns. While the freeze authority is revoked and liquidity is largely locked, the ability to mint unlimited tokens and the high volume-to-liquidity ratio suggest significant potential for manipulation. Third-party registry data confirms the mint authority and mutable metadata as primary security concerns.

> **Final Recommendation:** Investors should monitor the mint authority address for a revocation transaction. Until the mint authority is set to null, the token supply is subject to arbitrary inflation. 

Verify the current supply on-chain before executing large trades. Given the high volume-to-liquidity ratio, exercise caution regarding potential price manipulation and ensure slippage settings are configured appropriately for low-liquidity environments.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token utilizes the Token-2022 program, ensuring compatibility with advanced extensions. 7.1 Architecture is standard for SPL tokens, while 7.2 Code Security relies on the audited SPL program… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic stability is compromised by a volume/liquidity ratio of 43.55, indicating potential wash trading. 7.5 Governance is centralized with the top 10 holders controlling 45.60% of the supply.… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable in the traditional sense for SPL mints, but metadata mutability allows for branding changes. The mint authority remains active, allowing for future supply expansion.… |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 5Yix3R5nj7iUVVDfrAPvbPKM9j18oAto8eiJ5BjXUn7g. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 43.55x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for the high volatility and potential artificial volume in any swap calculation.


### `H-02` — Flagged High-Risk by Third-Party Registry  *(Severity: High · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset.

**Recommendation:** Do not interact with this token.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `L-01` — Pool Liquidity Not Locked  *(Severity: Low · Status: Unresolved)*

3.2% of pool liquidity is held, unlocked, by 2 address(es) other than the pool's creator.

**Recommendation:** Monitor these addresses for potential liquidity removal.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.1% of supply. Of that, 2.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.5% in wallets, 26.1% in other contracts. 739 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

739 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

96.6% of the pool's LP is burned or time-locked. 96.6% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 3.1% is held, unlocked, by 1 address(es) other than the pool's creator. This assessment covers the main pool, which holds 62% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $53K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $53K of DEX liquidity across 6 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`tybY2L...mint`](https://solscan.io/account/tybY2LFHH91VdoPJJkkFAsYaD7wnQQAm3BYg1x3mint) |
| **Network** | Solana |
| **Price** | $1.9100 |
| **24h Volume** | $960.3K |
| **Liquidity** | $32.7K |
| **Volume / Liquidity** | 29.4× |
| **Token Age** | 11h |
| **Top-10 Holders** | 48.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7596 buys / 5946 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/hsxna3rc2np5qu17bcmm3a69567kyqficjjrf569a8h3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mint-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
