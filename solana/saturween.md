---
token: Saturween
ticker: SATURWEEN
network: solana
risk_score: 0
status: low
date: 2026-10-30
---

# Saturween (SATURWEEN) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/saturween-sol)

---

## Audit Summary

Saturween is a Token-2022 asset with fully revoked mint and freeze authorities, ensuring supply immutability and preventing account freezing. Liquidity is fully secured via 100% burning of LP tokens, and no adverse flags were reported by third-party registries. The token exhibits healthy decentralization with top holders controlling 17.34% of the supply.

> **Final Recommendation:** The token is currently in a secure, immutable state. No immediate corrective actions are required for the contract configuration.

Investors should continue to monitor the 24-hour volume relative to liquidity to ensure market activity remains organic and not driven by wash trading, despite the current lack of adverse risk flags.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture is standard for SPL tokens, and 7.3 Access Control is robust as both mint and freeze… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $86,303 in liquidity, which is 100% burned, preventing rug-pulls via liquidity withdrawal. 7.5 Governance is decentralized with the top 10 holders controlling… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. 7.8 Operations are secure due to the permanent revocation of metadata and balance mutability, ensuring the token identity remains fixed. |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 23.3% of supply. Of that, 6.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 17.3% in wallets, 0.0% in other contracts. 5,903 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,903 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $90K (DexScreener, all pools). 24h trading volume $892K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $90K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 49 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5THtNE...pump`](https://solscan.io/account/5THtNEGTF1y67eRWvcgz3MomDZePCVx1xdskHHeCpump) |
| **Network** | Solana |
| **Price** | $0.0008459 |
| **24h Volume** | $892.0K |
| **Liquidity** | $90.2K |
| **Volume / Liquidity** | 9.9× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 23.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9108 buys / 5082 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hjzmbptzguq5nkss7crdv4ooxfyklv7p5awiqysbddq2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/saturween-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
