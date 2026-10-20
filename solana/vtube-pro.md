---
token: Vtube Pro
ticker: VTUBEPRO
network: solana
risk_score: 37
status: medium
date: 2026-10-12
---

# Vtube Pro (VTUBEPRO) — Smart Contract Security Analysis | Solana

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vtube-pro-sol)

---

## Audit Summary

The Vtube Pro (VTubePro) SPL token mint exhibits a high-risk profile primarily due to very low liquidity, which can lead to severe slippage and difficulty in exiting large positions. While core authorities like mint and freeze are revoked, and liquidity is fully burned, the limited market depth poses a significant concern for potential holders. No adverse flags were reported by third-party risk registries.

> **Final Recommendation:** Before interacting with this token, users should be aware of the extremely low liquidity, which will result in high slippage for any significant trade. Monitor DEX market data closely for any increase in liquidity to mitigate this risk. Verify on-chain that the mint and freeze authorities remain revoked to ensure the token's fixed supply and unfreezable nature.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Vtube Pro token is implemented using the spl-token-2022 program. Both the Mint Authority and Freeze Authority have been revoked, ensuring no new tokens can be minted and no accounts can be… |
| **Governance / Economics** | 7/10 | Low | Holder concentration is relatively low, with the top 10 holders that can sell holding 28.92% of the supply. A significant positive is that 100.0% of the pool's LP tokens are burned, preventing… |
| **Upgrades** | 8/10 | Low | The token's upgradeability and mutability features are minimal, enhancing its immutability. Both the Mint Authority and Freeze Authority are revoked, preventing any future changes to the token supply… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $9,343. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the low liquidity in any swap calculation and consider the potential for high slippage. Avoid large trades that could significantly impact the price.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $39K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 56.8% of supply. Of that, 27.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 26.2% in wallets, 2.7% in other contracts. 126 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

126 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 9 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 9 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 9 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BzLRJm...pump`](https://solscan.io/account/BzLRJmKYYvDaKW5ewyaJADiMV4eRCFV8scCEENbUpump) |
| **Network** | Solana |
| **Price** | $0.00001546 |
| **24h Volume** | $38.8K |
| **Liquidity** | $9.4K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 9d |
| **Top-10 Holders** | 56.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 411 buys / 393 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2rcvezx6fbeaqonbyjqpdvaks9ovk7qerhmh91mdxcod)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vtube-pro-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-12*
