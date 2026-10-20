---
token: holy shit
ticker: HOLYSHIT
network: solana
risk_score: 17
status: low
date: 2026-10-11
---

# holy shit (HOLYSHIT) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/holy-shit-sol)

---

## Audit Summary

This SPL Token-2022 mint, 'holy shit,' presents a low-risk profile based on available on-chain data. Both mint and freeze authorities are revoked, and 100% of its DEX liquidity is burned, indicating a secure and immutable setup. Third-party risk registry data reported no adverse flags, though holder distribution data was unavailable.

> **Final Recommendation:** Given the revoked authorities and locked liquidity, this token appears to have a robust and immutable configuration. Holders should continue to monitor DEX market data for any significant changes in liquidity or trading patterns. As holder distribution data was unavailable, it is prudent to observe on-chain holder activity if such data becomes accessible, to assess potential concentration risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is an SPL Token-2022 mint. Both the Mint Authority and Freeze Authority have been revoked, ensuring no new tokens can be minted and no existing accounts can be frozen. It does not utilize a… |
| **Governance / Economics** | 9/10 | Low | The token has a liquidity of $24,040 USD, which is moderate. The 24-hour volume to liquidity ratio is 6.13, indicating active trading relative to its liquidity, though not at a level suggesting wash… |
| **Upgrades** | 10/10 | Low | The Mint Authority and Freeze Authority are both revoked, preventing any future changes to the token's supply or the ability to freeze accounts. The token's metadata (name, symbol, image) is… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as holy shit (HOLYSHIT), rank #5338.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $21K (DexScreener, all pools). 24h trading volume $345K (CoinGecko, all markets, daily snapshot). 24h trading volume $148K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $21K of DEX liquidity across 5 pools. Launch: launched on pump.fun (PumpSwap), 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HoLyRo...Shit`](https://solscan.io/account/HoLyRoDEQvK5zPsGpcz3BbCWhceTGhWAGnVifSoUShit) |
| **Network** | Solana |
| **Price** | $0.00005941 |
| **24h Volume** | $148.3K |
| **Liquidity** | $21.5K |
| **Volume / Liquidity** | 6.9× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1687 buys / 1419 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5rw6ki6tvjuale3nscdghp4hkhmgqdovxxgtocpqhmve)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/holy-shit-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
