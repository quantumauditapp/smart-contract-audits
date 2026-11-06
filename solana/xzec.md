---
token: xZEC
ticker: XZEC
network: solana
risk_score: 68
status: high
date: 2026-11-06
---

# xZEC (XZEC) — Smart Contract Security Analysis | Solana

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xzec-sol)

---

## Audit Summary

The xZEC token mint maintains an active mint authority, allowing for unlimited supply expansion. Third-party registry data indicates high-risk flags including potential name mismatches and concentrated ownership. While the freeze authority is revoked, the combination of active minting capabilities and suspicious trading volume patterns necessitates extreme caution.

> **Final Recommendation:** Investors should verify the mint authority status on-chain before interacting with this asset. Given the active mint authority and high wash-trading signals, users should avoid holding large positions that cannot be exited within current liquidity constraints.

Monitor the mint address for a potential revocation transaction. Verify the token metadata against official project channels to ensure the current name and symbol are legitimate.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token utilizes the standard spl-token program (7.1 Architecture). Access control is currently insecure due to an active mint authority (7.3 Access Control). The freeze authority is successfully… |
| **Governance / Economics** | 6/10 | Medium | The token exhibits a volume-to-liquidity ratio of 26.78, which is highly indicative of wash trading (7.4 Economic). Liquidity is relatively low at $58,479, increasing slippage risks for larger trades… |
| **Upgrades** | 6/10 | Medium | SPL token mints do not support upgrade patterns (7.7 Upgrades). The mint authority is the primary administrative control and remains active. Metadata mutability is the only configurable parameter… |

## Security Findings

_🔴 1 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is GEwgNdd1wzAGNSePyM1Duaq3tPJTKuNiZLmxN6CBh94a. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 26.78x liquidity, a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for the fee in any swap calculation.


### `H-02` — Flagged High-Risk by Third-Party Registry  *(Severity: High · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset.

**Recommendation:** Do not interact with this token.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `L-01` — Metadata Mismatch  *(Severity: Low · Status: Unresolved)*

Third-party registry signals indicate a name mismatch for the token.

**Recommendation:** Cross-reference the token mint address with official project documentation.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $189K (DexScreener, all pools). 24h trading volume $4.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $189K of DEX liquidity across 14 pools. Launch: 3 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FgLfLh...Xci6`](https://solscan.io/account/FgLfLhT3QoPWynZ53L3KUUsPhspWbdPUfMtmPfezXci6) |
| **Network** | Solana |
| **Price** | $0.9437 |
| **24h Volume** | $1.55M |
| **Liquidity** | $58.1K |
| **Volume / Liquidity** | 26.6× |
| **Token Age** | 3d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13859 buys / 14129 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/htt2r4ry4rejcvhtw6an5qcjrhcwnj9qbpzyjm3h1acs)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xzec-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
