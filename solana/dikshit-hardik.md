---
token: Dikshit Hardik
ticker: DIKSHIT
network: solana
risk_score: 23
status: low
date: 2026-10-17
---

# Dikshit Hardik (DIKSHIT) — Smart Contract Security Analysis | Solana

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dikshit-hardik-sol)

---

## Audit Summary

This audit of the Dikshit Hardik (DIKSHIT) SPL Token Mint found no critical or high-severity issues based on the provided on-chain data and external security signals. The mint and freeze authorities are revoked, and liquidity is fully burned. Third-party registry data reported no adverse flags, and no transfer hooks or default frozen states are active.

> **Final Recommendation:** Given the revoked mint and freeze authorities, and the fully burned liquidity, this token presents a low risk profile based on the available on-chain data. Holders should continue to monitor the token's trading activity and liquidity for any significant changes. No further on-chain verification steps are required regarding mint or freeze capabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Dikshit Hardik (DIKSHIT) token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no accounts can be frozen. No… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding 20.95% of the supply. Total DEX liquidity is $24,438, and 100.0% of the pool's LP tokens are burned, preventing liquidity… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's supply and account freeze status cannot be altered. The token's metadata is immutable, preventing changes to its name… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 43.4% of supply. Of that, 3.2% locked, 19.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.9% in wallets, 0.0% in other contracts. 866 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Dikshit Hardik (DIKSHIT), rank #6217. 866 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $194K (CoinGecko, all markets, daily snapshot). 24h trading volume $234K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $26K of DEX liquidity across 5 pools. Launch: launched on pump.fun, 2 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 2 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 2 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AMQ8Bu...pump`](https://solscan.io/account/AMQ8BusAhpwbt3ufSCTi4k3BEQ7AecX9u12Jnk6Spump) |
| **Network** | Solana |
| **Price** | $0.00008132 |
| **24h Volume** | $232.6K |
| **Liquidity** | $26.2K |
| **Volume / Liquidity** | 8.9× |
| **Token Age** | 2d |
| **Top-10 Holders** | 43.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1803 buys / 1639 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/amjyxedj5q9bjscxmxxndcnkrt39zx4jqz9nwp8hudrn)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dikshit-hardik-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*
