---
token: onkey
ticker: ONKEY
network: solana
risk_score: 19
status: low
date: 2026-10-24
---

# onkey (ONKEY) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/onkey-sol)

---

## Audit Summary

The onkey token is a Token-2022 asset with both mint and freeze authorities successfully revoked. While the technical configuration is secure, a third-party risk registry has flagged the creator for a history of rugged tokens, necessitating caution. All liquidity is permanently burned, ensuring the pool cannot be withdrawn by the creator.

> **Final Recommendation:** Investors should exercise caution due to the third-party risk registry flag regarding the creator's history. While the on-chain technical state is secure and liquidity is burned, the reputation of the deployer remains a significant non-technical risk factor.

Verify the current holder distribution and monitor for large, coordinated sell-offs from the top 10 wallets. Use on-chain explorers to confirm that the mint and freeze authorities remain null and that no new extensions have been initialized.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or frozen account states. 7.1 Architecture and 7.2 Code Security are standard for SPL mints. 7.3 Access Control is robust as… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance metrics show the top 10 holders control 25.65% of the supply. 7.6 External signals indicate a third-party risk registry has flagged the creator's history. Liquidity is… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints do not support proxy-based logic updates. Metadata is immutable, and extension configurations such as transfer fees are not upgradable. The token… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Medium · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on the developer's history of deploying rugged tokens.

**Recommendation:** Exercise extreme caution; the developer's past behavior suggests a potential for malicious intent despite the current secure technical configuration.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 72.1% of supply. Of that, 46.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 25.6% in wallets, 0.0% in other contracts. 421 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as onkey (ONKEY), rank #6752. 421 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $68K (CoinGecko, all markets, daily snapshot). 24h trading volume $89K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), 66 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9nXSvn...gPs1`](https://solscan.io/account/9nXSvn8bUmboPdgA4qnmtzxQdgjXWquK6sYaCFLRgPs1) |
| **Network** | Solana |
| **Price** | $0.0000534 |
| **24h Volume** | $89.3K |
| **Liquidity** | $22.2K |
| **Volume / Liquidity** | 4.0× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 72.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 756 buys / 534 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6pihhhbkurxd4nvlqq9opdaqywrvmws1d518hozcjv6c)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/onkey-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*
