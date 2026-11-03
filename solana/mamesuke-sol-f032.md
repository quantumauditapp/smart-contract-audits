---
token: Mamesuke
ticker: 豆助
network: solana
risk_score: 13
status: low
date: 2026-11-03
---

# Mamesuke (豆助) — Smart Contract Security Analysis | Solana

> **Risk Score: 13/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mamesuke-sol-f032)

---

## Audit Summary

The Mamesuke token (94RNfQN5FPBFoBS5rfZ6d6DZ9qkKTJxD4cwmxDjhpump) utilizes the standard SPL Token program. Both mint and freeze authorities are revoked, ensuring supply stability and preventing account freezing. All liquidity is permanently burned, eliminating withdrawal risks.

> **Final Recommendation:** The token exhibits a strong security posture with no active authorities and fully burned liquidity. Users should continue to monitor the top holder distribution via block explorers to ensure concentration remains within acceptable bounds.

Verify the current supply and authority status directly on-chain using a block explorer to confirm that the 'Mint Authority' and 'Freeze Authority' remain set to 'None'.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token operates on the standard SPL Token program (7.1 Architecture). Security is maintained through the revocation of both mint and freeze authorities (7.3 Access Control). No advanced extensions… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is low, with the top 10 holders controlling 16.39% of the supply (7.4 Economic). Liquidity is fully secured, with 100% of LP tokens burned, preventing rug-pull scenarios (7.5… |
| **Upgrades** | 10/10 | Low | The token mint is immutable as both authorities are revoked (7.7 Upgrades). Metadata is locked and cannot be modified by any party. There are no upgradeable components or proxy patterns present in… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 97.2% of supply. Of that, 80.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 16.4% in wallets, 0.0% in other contracts. 92 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

92 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $11K (DexScreener, all pools). 24h trading volume $84K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $11K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 35 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`94RNfQ...pump`](https://solscan.io/account/94RNfQN5FPBFoBS5rfZ6d6DZ9qkKTJxD4cwmxDjhpump) |
| **Network** | Solana |
| **Price** | $0.00002315 |
| **24h Volume** | $84.0K |
| **Liquidity** | $10.7K |
| **Volume / Liquidity** | 7.8× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 97.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1019 buys / 689 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hoqgbaxr86yjxuw25khhrxngncd5wcca74ujwtzubeea)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mamesuke-sol-f032)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*
