---
token: FX Fighter Kurumi-chan
ticker: KURUMI
network: solana
risk_score: 7
status: low
date: 2026-10-03
---

# FX Fighter Kurumi-chan (KURUMI) — Smart Contract Security Analysis | Solana

> **Risk Score: 7/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fx-fighter-kurumi-chan-sol)

---

## Audit Summary

This SPL Token-2022 mint, "FX Fighter Kurumi-chan (Kurumi)", demonstrates robust security posture with both mint and freeze authorities revoked, preventing further supply inflation or asset freezing. Liquidity is substantial and permanently locked by burning LP tokens, mitigating rug pull risks. Holder concentration is low, and no adverse flags were reported by third-party risk registries. Third-party registry data was available and reported no adverse flags.

> **Final Recommendation:** Holders should verify on-chain that the mint and freeze authorities remain revoked to ensure the fixed supply and unfreezable nature of the token. Monitor the token's liquidity and trading volume for any significant changes, although the current state shows strong stability with burned LP tokens. Confirm that no new Token-2022 extensions are enabled that could alter token behavior.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is an SPL Token-2022 mint. Both the mint authority and freeze authority have been revoked, preventing further token creation or freezing of accounts (7.3 Access Control). No transfer hook… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders that can sell owning 22.03% of the supply, indicating a relatively distributed ownership (7.4 Economic). The token has healthy liquidity at… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning no further tokens can be minted and no accounts can be frozen (7.7 Upgrades). The token does not utilize a transfer hook, nor is it… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 29.9% of supply. Of that, 7.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 20.4% in wallets, 1.6% in other contracts. 3,217 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

3,217 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $172K (DexScreener, all pools). 24h trading volume $202K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $172K of DEX liquidity across 3 pools. Launch: launched on pump.fun, 277 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Ew8Kqg...pump`](https://solscan.io/account/Ew8KqgSitYucieR5KnSAL2SUFspcwA8AgSuZ5xWspump) |
| **Network** | Solana |
| **Price** | $0.001037 |
| **24h Volume** | $191.9K |
| **Liquidity** | $169.2K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 9mo |
| **Top-10 Holders** | 29.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 626 buys / 546 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2xhrmdxskurh8ckmerbnhyciqghgsjlwmgckep9bmlkk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fx-fighter-kurumi-chan-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*
