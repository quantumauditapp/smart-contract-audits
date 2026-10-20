---
token: Flying Tesla Roadster
ticker: FTR
network: solana
risk_score: 9
status: low
date: 2026-10-18
---

# Flying Tesla Roadster (FTR) — Smart Contract Security Analysis | Solana

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/flying-tesla-roadster-sol-ba92)

---

## Audit Summary

The Flying Tesla Roadster (FTR) token mint is an SPL Token-2022. Both mint and freeze authorities are revoked, indicating a fixed supply and unfreezable accounts. Information regarding the locking status of the liquidity pool was not available for assessment.

> **Final Recommendation:** Holders should monitor the liquidity pool for any changes in its locking status, as this information was unavailable during the audit. Verify on-chain that the mint and freeze authorities remain revoked to confirm the fixed supply and unfreezable nature of the token.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The FTR token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no holder accounts can be… |
| **Governance / Economics** | 7/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding 12.23% of the supply. The token has $226,803 in DEX liquidity with a 24-hour volume of $1,961,825, resulting in a… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, preventing further changes to the token's supply or account freeze status. The token does not utilize a transfer hook, and its metadata is… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 18.2% of supply. Of that, 6.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 12.2% in wallets, 0.0% in other contracts. 18,363 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

18,363 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $653K (DexScreener, all pools). 24h trading volume $4.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $653K of DEX liquidity across 30 pools. Launch: launched on pump.fun, 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DFMt2F...pump`](https://solscan.io/account/DFMt2FyLpB6ekPNAzVErLXgpSnJ9CRf1VnxBAkTLpump) |
| **Network** | Solana |
| **Price** | $0.002424 |
| **24h Volume** | $1.96M |
| **Liquidity** | $228.9K |
| **Volume / Liquidity** | 8.6× |
| **Token Age** | 3d |
| **Top-10 Holders** | 18.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8254 buys / 6865 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2jaq7kmy4eqxex1dqho1nsybev2yty94dudkmvz2yub3)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/flying-tesla-roadster-sol-ba92)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-18*
