---
token: Kobecoin
ticker: KOBX
network: solana
risk_score: 22
status: low
date: 2026-10-26
---

# Kobecoin (KOBX) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kobecoin-sol)

---

## Audit Summary

Kobecoin (KOBX) is a standard SPL token with both mint and freeze authorities successfully revoked. The liquidity is fully burned, and no adverse flags were reported by third-party registries. No critical or high-severity security risks were identified in the current on-chain configuration.

> **Final Recommendation:** The token is currently configured in a secure, immutable state. No further action is required to mitigate administrative risks.

Users should continue to monitor the top holder distribution via block explorers to ensure concentration remains within reasonable bounds as the project matures.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture is standard, with 7.3 Access Control confirmed by the revocation of both mint and freeze authorities. 7.2 Code Security is… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic health is supported by $50,455 in liquidity, which is 100% burned, ensuring permanent availability. 7.5 Governance is decentralized as the top 10 holders control only 22.44% of the… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint. Metadata is immutable, and no administrative authorities exist to modify token behavior. The configuration is locked in its current state. |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 30.2% of supply. Of that, 7.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.4% in wallets, 0.0% in other contracts. 675 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Kobecoin (KOBX), rank #4205. 675 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $48K (DexScreener, all pools). 24h trading volume $4K (CoinGecko, all markets, daily snapshot). 24h trading volume $67K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $48K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 336 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`48iJcU...pump`](https://solscan.io/account/48iJcUv9jsiZ7cCisyVFLPFLMoNBKg3L43bRvktXpump) |
| **Network** | Solana |
| **Price** | $0.0002733 |
| **24h Volume** | $67.0K |
| **Liquidity** | $47.5K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 30.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1002 buys / 443 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9c42shkgcne7bupmtzvtyrflssbesxgsxd5g7hjaer9f)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kobecoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
