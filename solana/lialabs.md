---
token: LiaLabs
ticker: LIA
network: solana
risk_score: 27
status: low
date: 2026-11-06
---

# LiaLabs (LIA) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lialabs-sol)

---

## Audit Summary

The LiaLabs (LIA) token mint has successfully revoked both mint and freeze authorities, ensuring supply stability and preventing account freezing. However, the protocol exhibits high risk due to extreme wash-trading signals and the lack of locked liquidity, which remains fully withdrawable by anonymous holders. Third-party registry data indicates a high concentration of unlocked liquidity and a low number of liquidity providers.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume. Monitor the pool's liquidity levels on-chain to detect sudden withdrawals by the liquidity providers.

Verify that the mint and freeze authorities remain null by checking the mint account state via a block explorer. Avoid large positions given the high slippage risk associated with the current liquidity depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.2 Code Security are standard for this program. 7.3 Access Control is robust as both mint and freeze authorities are… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance risks are significant due to the 143.94 volume/liquidity ratio, which indicates heavy wash trading. 7.6 External signals confirm that 100% of the $113,146 liquidity is… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL token mint. Metadata is immutable, and no upgradeable extensions are configured. The token state is fixed and cannot be modified by the… |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 143.94, which significantly exceeds the 20x threshold, indicating artificially inflated trade volume.

**Recommendation:** Exercise caution; high volume may not reflect genuine market demand.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked, meaning the entire $113,146 in liquidity can be withdrawn by the anonymous holders of the LP tokens.

**Recommendation:** Monitor the liquidity pool for sudden withdrawals and avoid providing liquidity to this pair.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $106K (DexScreener, all pools). 24h trading volume $14.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $106K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`VLxDCj...ZjNv`](https://solscan.io/account/VLxDCjbbJ853sqtmiXfpWuYMRvDTRrYWf2GuS4GZjNv) |
| **Network** | Solana |
| **Price** | $0.0001057 |
| **24h Volume** | $14.60M |
| **Liquidity** | $106.3K |
| **Volume / Liquidity** | 137.3× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 15258 buys / 10715 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/ds3fb8u6szz69x5qanf4mepldcbjtoybbsyjd4lvn1qg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lialabs-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*
