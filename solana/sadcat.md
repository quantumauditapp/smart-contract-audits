---
token: sadcat
ticker: SADCAT
network: solana
risk_score: 44
status: medium
date: 2026-10-26
---

# sadcat (SADCAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 44/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sadcat-sol)

---

## Audit Summary

The sadcat token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. While the token architecture is secure regarding administrative control, the project exhibits high market risk due to very low liquidity and a high volume-to-liquidity ratio indicative of wash trading. Third-party registry data confirms the low liquidity risk.

> **Final Recommendation:** Investors should exercise extreme caution due to the low liquidity, which may prevent exiting positions without significant slippage. Monitor the top holder distribution to ensure no single wallet accumulates a majority stake.

Verify that no new extensions are added to the token account if the project attempts to migrate or update, though the current configuration is immutable. Use decentralized exchanges with caution and avoid placing large market orders.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is deployed on the SPL Token-2022 program, ensuring modern extension support. 7.1 Architecture is standard for SPL mints, with 7.2 Code Security relying on the audited native program. 7.3… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic stability is compromised by a liquidity pool of only $6,449. 7.5 Governance is decentralized as no single entity controls the mint. However, the 35.50 volume/liquidity ratio suggests… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is fixed and non-mutable, preventing branding changes. The token configuration is final and cannot be altered by any authority. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $6,449. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity constraints before executing trades.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 35.50x liquidity, a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Perform independent volume verification before relying on market activity metrics.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $296K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.5% of supply. Of that, 23.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 24.9% in wallets, 0.0% in other contracts. 308 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

308 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 8 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Bjqjs6...pump`](https://solscan.io/account/Bjqjs6qTTkEmuoPVifaWfEcMXtCdU3V3aG9HRorppump) |
| **Network** | Solana |
| **Price** | $0.0000165 |
| **24h Volume** | $226.1K |
| **Liquidity** | $9.2K |
| **Volume / Liquidity** | 24.6× |
| **Token Age** | 3h |
| **Top-10 Holders** | 48.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3576 buys / 2781 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3havfwpentcstufnxmlnda3qxwxjnzh1tc85egt1ckvw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sadcat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*
