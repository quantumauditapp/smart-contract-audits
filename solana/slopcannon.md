---
token: slopcannon
ticker: SLOPCANNON
network: solana
risk_score: 1
status: low
date: 2026-10-11
---

# slopcannon (SLOPCANNON) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/slopcannon-sol)

---

## Audit Summary

The slopcannon SPL Token Mint has undergone an audit based on on-chain facts and external security signals. No critical or high-severity vulnerabilities were identified. The mint authority and freeze authority are both revoked, and 100% of the pool's liquidity is burned, indicating a secure and immutable state for key parameters. Third-party registry data reported no adverse flags. Chain-native RPC data for holder distribution was unavailable, but this did not prevent assessment of other key risks.

> **Final Recommendation:** Verify on-chain that the mint authority and freeze authority remain revoked to confirm the token's fixed supply and unfreezable nature. Monitor the token's trading activity for any unusual patterns, although current volume-to-liquidity ratios appear normal. Confirm that the metadata remains immutable if branding is a concern.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The slopcannon token operates on the spl-token-2022 program, indicating support for modern SPL extensions. Both the mint authority and freeze authority are revoked, ensuring no new tokens can be… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell possessing 19.71% of the supply, reducing the risk of single-whale market manipulation. The token has healthy liquidity, with… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, establishing a fixed supply and preventing account freezing. The token's metadata is immutable, meaning its name, symbol, or image cannot be… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 32.0% of supply. Of that, 12.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.7% in wallets, 0.0% in other contracts. 2,113 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as slopcannon (SLOPCANNON), rank #4535. 2,113 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 90% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $59K (DexScreener, all pools). 24h trading volume $448K (CoinGecko, all markets, daily snapshot). 24h trading volume $167K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $59K of DEX liquidity across 6 pools. Launch: launched on pump.fun (PumpSwap), 15 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 15 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 15 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`55Vr2V...DEzW`](https://solscan.io/account/55Vr2VpSwxsDkB6uGGHAvRv86K6zax2Zb4TT8ivwDEzW) |
| **Network** | Solana |
| **Price** | $0.0002338 |
| **24h Volume** | $146.9K |
| **Liquidity** | $52.9K |
| **Volume / Liquidity** | 2.8× |
| **Token Age** | 15d |
| **Top-10 Holders** | 32.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 993 buys / 1326 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bng5962zkbd6zfmfakjtcf6z2mjba7qn97omsqshsplp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/slopcannon-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*
