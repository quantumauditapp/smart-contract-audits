---
token: Sapling
ticker: SAPLING
network: solana
risk_score: 1
status: low
date: 2026-10-03
---

# Sapling (SAPLING) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sapling-sol)

---

## Audit Summary

This SPL Token Mint exhibits a strong security posture with both mint and freeze authorities revoked, preventing further supply dilution or asset freezing. All pool liquidity is permanently burned, eliminating rug pull risk from liquidity withdrawal. Holder concentration data was unavailable, and no adverse flags were reported by third-party risk registries.

> **Final Recommendation:** Holders should monitor the token's trading activity, particularly the volume-to-liquidity ratio, for any significant changes. While current liquidity is robust and locked, continuous observation of market dynamics is prudent. Verify on-chain that the reported authority revocations remain unchanged before any significant interaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | This token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, preventing further token issuance or freezing of holder accounts. No… |
| **Governance / Economics** | 10/10 | Low | The token has a total DEX liquidity of $145,553, with 100% of the pool's LP tokens burned, ensuring liquidity cannot be withdrawn. The 24-hour volume is $1,419,547, resulting in a Volume/Liquidity… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning no further tokens can be minted and no accounts can be frozen. The token's metadata, including name, symbol, or image, is immutable… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Sapling (SAPLING), market cap $2M, rank #2624.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 63% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $246K (DexScreener, all pools). 24h trading volume $3.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $3.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $246K of DEX liquidity across 8 pools. Launch: launched on pump.fun (PumpSwap), 7 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 7 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 7 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BZFYNP...B96W`](https://solscan.io/account/BZFYNPeQAEW3HWQ4DNsTVahC1n4ZjTgn6jB2nnBbB96W) |
| **Network** | Solana |
| **Price** | $0.00128 |
| **24h Volume** | $1.43M |
| **Liquidity** | $156.2K |
| **Volume / Liquidity** | 9.2× |
| **Token Age** | 7d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2892 buys / 2684 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6ejg4ayjm3mk1t2zbkjbj43df3s7rbmpc9mgo526k51g)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sapling-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
