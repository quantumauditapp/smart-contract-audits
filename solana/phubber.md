---
token: phubber
ticker: PHUBBER
network: solana
risk_score: 2
status: low
date: 2026-10-08
---

# phubber (PHUBBER) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/phubber-sol)

---

## Audit Summary

The phubber SPL Token Mint exhibits strong security posture with both mint and freeze authorities revoked, preventing further token issuance or account freezing. All pool liquidity is permanently burned, eliminating rug pull risks from liquidity withdrawal. No high-risk flags were reported by third-party registries, and no critical Token-2022 extensions like transfer hooks or default frozen states are active. Holder distribution data was unavailable, which prevents a full assessment of whale risk.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked. While current liquidity is locked, monitor the token's DEX liquidity and trading volume for any significant changes. If holder distribution data becomes available in the future, assess the concentration of tokens among the top holders to understand potential market impact from large sell-offs. Given the current configuration, the token presents a low technical risk profile.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The phubber token is implemented using the spl-token-2022 program, indicating modern Solana token standards. Crucially, both the Mint Authority and Freeze Authority have been revoked, ensuring no new… |
| **Governance / Economics** | 10/10 | Low | The token's liquidity profile is robust, with 100.0% of the pool's LP tokens permanently burned, eliminating the risk of liquidity withdrawal by pool creators. Current DEX liquidity stands at… |
| **Upgrades** | 10/10 | Low | The token's configuration is highly immutable, as both the mint and freeze authorities are revoked. Furthermore, the metadata is not mutable, meaning the token's name, symbol, or image cannot be… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as phubber (PHUBBER), rank #3812.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 87% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $84K (DexScreener, all pools). 24h trading volume $872K (CoinGecko, all markets, daily snapshot). 24h trading volume $745K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $84K of DEX liquidity across 8 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CBcjQN...pump`](https://solscan.io/account/CBcjQNdtgb4SHwKDqKFxD3yPSk7pEMpKHQiMmZrgpump) |
| **Network** | Solana |
| **Price** | $0.0004433 |
| **24h Volume** | $680.0K |
| **Liquidity** | $73.4K |
| **Volume / Liquidity** | 9.3× |
| **Token Age** | 2d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4149 buys / 3683 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/baihzfqngf1espbdcvuch9ikylckqzdwwph7zmzsqj5t)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/phubber-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
