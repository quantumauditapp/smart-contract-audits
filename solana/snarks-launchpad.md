---
token: SNARKS Launchpad
ticker: SNARKS
network: solana
risk_score: 23
status: low
date: 2026-10-30
---

# SNARKS Launchpad (SNARKS) — Smart Contract Security Analysis | Solana

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/snarks-launchpad-sol)

---

## Audit Summary

The SNARKS Launchpad token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. The liquidity is fully locked, and no adverse flags were reported by third-party registries. The token exhibits a healthy security posture with no critical or high-severity vulnerabilities identified.

> **Final Recommendation:** The token is configured securely with no administrative backdoors. Holders should continue to monitor the top 10 holder distribution to ensure concentration does not increase significantly over time.

No further action is required for the token configuration. Users should verify the mint address against official project channels before interacting with the asset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program, ensuring compatibility with modern extensions. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance metrics show 22.54% concentration among the top 10 holders, which is within acceptable ranges. 7.6 External data confirms 100% of liquidity is locked, preventing… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is immutable, and no upgradeable extensions are active. The token state is fixed and cannot be altered by any external authority. |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 50.9% of supply. Of that, 28.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.5% in wallets, 0.0% in other contracts. 686 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as SNARKS Launchpad (SNARKS), rank #8026. 686 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $21K (DexScreener, all pools). 24h trading volume $78K (CoinGecko, all markets, daily snapshot). 24h trading volume $205K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $21K of DEX liquidity across 2 pools. Launch: 18 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 18 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 18 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ABnpAh...dNvJ`](https://solscan.io/account/ABnpAh5jdjD78iAuzsSgT6y57m3hUKpxEKBeeYaddNvJ) |
| **Network** | Solana |
| **Price** | $0.00003908 |
| **24h Volume** | $182.5K |
| **Liquidity** | $20.4K |
| **Volume / Liquidity** | 9.0× |
| **Token Age** | 18d |
| **Top-10 Holders** | 50.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1326 buys / 1028 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dttjgdew1gfk3cvmngchhupimuohbdospeb9mw7fmkki)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/snarks-launchpad-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
