---
token: Nigga Inu
ticker: NI
network: solana
risk_score: 14
status: low
date: 2026-09-30
---

# Nigga Inu (NI) — Smart Contract Security Analysis | Solana

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nigga-inu-sol)

---

## Audit Summary

This SPL Token Mint for Nigga Inu (NI) presents significant risks primarily due to extremely low liquidity ($2,533) and a high volume-to-liquidity ratio (90.60x), which is a strong indicator of potential wash trading. While mint and freeze authorities are revoked, holder distribution data was unavailable, preventing a full assessment of supply concentration.

> **Final Recommendation:** Given the very low liquidity and potential for wash trading, extreme caution is advised. Holders should be aware that exiting positions may incur severe slippage due to the limited liquidity. Monitor DEX market data for any changes in liquidity levels and trading patterns. Verify on-chain that the mint and freeze authorities remain revoked to ensure the token's fixed supply and unfreezable nature.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Nigga Inu (NI) token is an SPL Token-2022 mint. Both the Mint Authority and Freeze Authority have been revoked, ensuring no new tokens can be minted and no accounts can be frozen by an external… |
| **Governance / Economics** | 9/10 | Low | The token exhibits very low liquidity, with only $2,533 available in DEX pools. This is compounded by a 24-hour volume of $229,461, resulting in a volume/liquidity ratio of 90.60, which strongly… |
| **Upgrades** | 10/10 | Low | The Mint Authority and Freeze Authority are both revoked, meaning no further changes can be made to the token's supply or account freeze status. The token utilizes the spl-token-2022 program but does… |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $2,533. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the extremely low liquidity in any swap calculation and consider the difficulty of exiting positions.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 90.60x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise extreme caution, as high volume relative to low liquidity often indicates manipulated trading activity designed to mislead potential investors.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $22K (DexScreener, all pools). 24h trading volume $283K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $22K of DEX liquidity across 3 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8y2h8R...pump`](https://solscan.io/account/8y2h8RDbF1FVKhcHNqaZFg4yJ5azXUyUeoByEAvJpump) |
| **Network** | Solana |
| **Price** | $0.000069 |
| **24h Volume** | $219.0K |
| **Liquidity** | $22.3K |
| **Volume / Liquidity** | 9.8× |
| **Token Age** | 12h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6822 buys / 1711 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/azunhxfqfrya2pefxxa4xb3dh33dpcxsuxqt1tfficse)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nigga-inu-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-30*
