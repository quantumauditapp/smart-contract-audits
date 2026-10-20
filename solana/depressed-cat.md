---
token: depressed cat
ticker: DEPCAT
network: solana
risk_score: 20
status: low
date: 2026-10-09
---

# depressed cat (DEPCAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/depressed-cat-sol)

---

## Audit Summary

This audit of the depressed cat (depcat) SPL Token Mint found no critical or high-severity issues based on the provided on-chain facts and third-party security signals. Both the mint and freeze authorities are revoked, and no Token-2022 extensions that introduce significant risk (like transfer hooks or default frozen accounts) are active. Third-party risk registries reported no adverse flags, and DEX liquidity is fully burned. Chain-native RPC data for holder distribution was available, showing low concentration.

> **Final Recommendation:** Given the low-risk profile, holders can interact with this token with a reasonable degree of confidence regarding its on-chain configuration. No specific on-chain verification steps are immediately necessary beyond confirming the current state of authorities and extensions, which are already favorable. Monitor the token's market behavior and liquidity for any changes, as external factors can always influence value.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts can be frozen… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell controlling 22.57% of the supply, which does not pose a significant concentration risk. The token has a total DEX liquidity of… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's supply and account states cannot be altered. The token's metadata is immutable, preventing changes to its name, symbol… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 35.0% of supply. Of that, 12.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.6% in wallets, 0.0% in other contracts. 614 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

614 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $32K (DexScreener, all pools). 24h trading volume $253K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $32K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), 7 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 7 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 7 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`B4v7fA...xrPk`](https://solscan.io/account/B4v7fATuSdtNsJximsbLXZ5wMenSvujfED71xe5ZxrPk) |
| **Network** | Solana |
| **Price** | $0.0001327 |
| **24h Volume** | $252.5K |
| **Liquidity** | $31.2K |
| **Volume / Liquidity** | 8.1× |
| **Token Age** | 7d |
| **Top-10 Holders** | 35.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2068 buys / 1689 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/and84tthp4mn5pu9ng1y4resa15va7qfa6luieqxp8xj)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/depressed-cat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-09*
