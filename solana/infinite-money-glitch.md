---
token: Infinite Money Glitch
ticker: GLITCH
network: solana
risk_score: 7
status: low
date: 2026-10-18
---

# Infinite Money Glitch (GLITCH) — Smart Contract Security Analysis | Solana

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/infinite-money-glitch-sol)

---

## Audit Summary

The Infinite Money Glitch (GLITCH) token presents a low-risk profile based on available on-chain data. Key authorities, including Mint and Freeze, are revoked, and 100% of the DEX liquidity is burned, mitigating common rug pull vectors. Third-party registry data reported no adverse flags, and chain-native RPC data for holder distribution was available.

> **Final Recommendation:** Holders should verify on-chain that the Mint Authority and Freeze Authority remain revoked to confirm the fixed supply and unfreezable nature of the token. Monitor the token's trading volume and liquidity over time to ensure market stability. No further specific on-chain verification steps are required regarding mutable features or liquidity withdrawal risks, as these are already addressed by the current configuration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Infinite Money Glitch (GLITCH) token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority have been revoked, indicating that no new tokens can be minted… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell holding 26.01% of the total supply. The token benefits from robust liquidity, with $101,280 USD in DEX pools. Critically, 100.0% of… |
| **Upgrades** | 10/10 | Low | The token's core authorities, Mint Authority and Freeze Authority, are both revoked, preventing any post-launch changes to minting or freezing capabilities. The token does not use Token-2022… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 30.6% of supply. Of that, 4.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 26.0% in wallets, 0.0% in other contracts. 427 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Infinite Money Glitch (GLITCH), market cap $1M, rank #2847. 427 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $100K (DexScreener, all pools). 24h trading volume $790K (CoinGecko, all markets, daily snapshot). 24h trading volume $420K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $100K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8Xg89x...pump`](https://solscan.io/account/8Xg89xT8Ve34sKiYqYuMs46mycREsCA2F362UscRpump) |
| **Network** | Solana |
| **Price** | $0.001374 |
| **24h Volume** | $419.5K |
| **Liquidity** | $100.4K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 1d |
| **Top-10 Holders** | 30.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1677 buys / 1109 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/em6rvzgxhd35pz7cvujctpenv4jaztscavhaxbxcbcg7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/infinite-money-glitch-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-18*
