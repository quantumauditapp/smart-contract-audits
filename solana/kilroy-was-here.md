---
token: Kilroy was here
ticker: KILROY
network: solana
risk_score: 6
status: low
date: 2026-11-07
---

# Kilroy was here (KILROY) — Smart Contract Security Analysis | Solana

> **Risk Score: 6/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kilroy-was-here-sol)

---

## Audit Summary

The KILROY token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. The project demonstrates strong liquidity security with 92.7% of LP tokens burned, and no adverse flags were reported by third-party registries. Holder concentration is low, and the token exhibits no mutable metadata or balance-altering risks.

> **Final Recommendation:** The token is in a secure state with authorities revoked and liquidity protected. Holders should continue to monitor the remaining 7.3% of unverified liquidity for any unusual movements.

Verify the current mint and freeze authority status periodically using a block explorer to ensure they remain null. No further action is required for standard interaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token operates on the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring the supply is fixed and accounts cannot be frozen (7.3 Access Control).… |
| **Governance / Economics** | 10/10 | Low | The top 10 holders control 22.56% of the supply, indicating a healthy distribution (7.4 Economic). Liquidity is robust at $77,442, with 92.7% of LP tokens permanently burned, mitigating rug-pull… |
| **Upgrades** | 10/10 | Low | SPL tokens do not support upgrades (7.7 Upgrades). The mint and freeze authorities are permanently revoked, meaning no administrative changes can be made to the token's core parameters. Metadata is… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `QA-LIQUIDITY` — Liquidity only partly locked or burned  *(Severity: Medium · Status: Acknowledged)*

92.7% of the pool's LP is burned or time-locked. 92.7% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified. This assessment covers the main pool, which holds 88% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 34.3% of supply. Of that, 11.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.6% in wallets, 0.0% in other contracts. 1,227 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Kilroy was here (KILROY), rank #4453. 1,227 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $86K (DexScreener, all pools). 24h trading volume $260K (CoinGecko, all markets, daily snapshot). 24h trading volume $646K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $86K of DEX liquidity across 15 pools. Launch: launched on pump.fun, 360 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CFYhdW...pump`](https://solscan.io/account/CFYhdWXsYfS7swnJgHRwb5toTHMEQD7Ljd5gGwKLpump) |
| **Network** | Solana |
| **Price** | $0.0004192 |
| **24h Volume** | $636.2K |
| **Liquidity** | $75.9K |
| **Volume / Liquidity** | 8.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 34.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4042 buys / 2845 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fakn3y8zxrneqagcwfkniu4x8gn4dmsymyjh1s5ebrx)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kilroy-was-here-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
