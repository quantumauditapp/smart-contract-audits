---
token: Nullmask
ticker: MASK
network: solana
risk_score: 38
status: medium
date: 2026-10-02
---

# Nullmask (MASK) — Smart Contract Security Analysis | Solana

> **Risk Score: 38/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nullmask-sol)

---

## Audit Summary

The Nullmask (MASK) SPL Token Mint is built on the spl-token-2022 program. Key authorities such as Mint Authority and Freeze Authority have been revoked, indicating a fixed supply and unfreezable accounts. However, the token's metadata remains mutable, allowing changes to its name, symbol, or image post-launch. Holder distribution data was unavailable from chain-native RPC, preventing a full assessment of concentration risk, though a third-party registry signals high concentration.

> **Final Recommendation:** Holders should verify the token's metadata against official sources periodically to ensure branding consistency, as it can be changed. Monitor the remaining 15.0% of unlocked liquidity held by other addresses for any significant movements. Due to unavailable holder distribution data, closely observe on-chain holder activity for signs of concentration or large transfers that could impact market stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Nullmask (MASK) token operates on the spl-token-2022 program. Both the Mint Authority and Freeze Authority have been revoked, ensuring no new tokens can be minted and no holder accounts can be… |
| **Governance / Economics** | 8/10 | Low | The token exhibits a healthy liquidity profile with $615,521 in total DEX liquidity. The 24-hour volume of $1,405,412 results in a normal Volume/Liquidity Ratio of 2.28, not indicating wash trading.… |
| **Upgrades** | 7/10 | Low | The Mint Authority and Freeze Authority are both revoked, preventing further changes to supply or account freezing capabilities. While the token leverages the Token-2022 program, its Transfer Hook is… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 3.0% · upgradeable |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity only partly locked or burned  *(Severity: Medium · Status: Acknowledged)*

85.0% of the pool's LP is burned or time-locked. 85.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. 15.0% is held, unlocked, by 1 address(es) other than the pool's creator. This assessment covers the main pool, which holds 69% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by `metadata_mutable: True`.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Nullmask (MASK).

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $878K (DexScreener, all pools). 24h trading volume $4.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $878K of DEX liquidity across 16 pools. Launch: 8 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 8 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 8 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HuAXPy...CUa7`](https://solscan.io/account/HuAXPyDWDaMYFKuwQHpqL1oPnj93zdzWmtvFGzCeCUa7) |
| **Network** | Solana |
| **Price** | $0.02938 |
| **24h Volume** | $1.39M |
| **Liquidity** | $605.7K |
| **Volume / Liquidity** | 2.3× |
| **Token Age** | 8d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2959 buys / 2078 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4gwh5sakgzoukhhj4rh3p5fmpu6ypuaexv6fah5jqyfm)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nullmask-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-02*
