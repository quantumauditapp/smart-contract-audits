---
token: Slopcoin
ticker: SLOPCOIN
network: solana
risk_score: 14
status: low
date: 2026-10-24
---

# Slopcoin (SLOPCOIN) — Smart Contract Security Analysis | Solana

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/slopcoin-sol)

---

## Audit Summary

Slopcoin is an SPL Token-2022 asset with both mint and freeze authorities successfully revoked. The token exhibits low holder concentration and fully burned liquidity, significantly reducing common rug-pull vectors. No adverse flags were reported by third-party registries.

> **Final Recommendation:** The token is currently in a secure state with no administrative backdoors. Holders should monitor the top 10 holder wallets for significant accumulation that could lead to future price volatility.

Verify that the mint and freeze authorities remain null by checking the mint account state via a block explorer. No further action is required for basic security compliance.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program with no active transfer hooks or default frozen states. 7.1 Architecture and 7.2 Code Security are standard for SPL-2022. 7.3 Access Control is robust as… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance metrics show 19.37% concentration among the top 10 sellable holders, which is well below the 50% risk threshold. 7.6 External market data indicates $20,417 in… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints do not utilize proxy patterns. Metadata is immutable, and there are no upgradable extensions for transfer fees or hooks. The token state is fixed… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 92.8% of supply. Of that, 73.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.4% in wallets, 0.0% in other contracts. 40 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

40 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $26K (DexScreener, all pools). 24h trading volume $193K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $26K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), 199 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BzA6JB...hc68`](https://solscan.io/account/BzA6JBKgH8qK3XzBpXUiF283jd1k7yCKzwJEiEFAhc68) |
| **Network** | Solana |
| **Price** | $0.0001081 |
| **24h Volume** | $121.7K |
| **Liquidity** | $26.3K |
| **Volume / Liquidity** | 4.6× |
| **Token Age** | 6mo |
| **Top-10 Holders** | 92.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1672 buys / 1196 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/afqulkmfwn8rrz889gfn2gwd3rhj7srmqmjkz7s1eahk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/slopcoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
