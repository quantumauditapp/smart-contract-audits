---
token: Backed By Belief
ticker: NOTHING
network: solana
risk_score: 26
status: low
date: 2026-10-27
---

# Backed By Belief (NOTHING) — Smart Contract Security Analysis | Solana

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/backed-by-belief-sol-e5d7)

---

## Audit Summary

The token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the protocol exhibits high risk due to extreme wash-trading signals and the lack of locked liquidity, which allows for potential sudden removal of pool funds. Holder concentration data is unavailable, and third-party registry signals indicate a high volume of unlocked LP tokens.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume. Monitor the pool's liquidity levels on-chain to detect potential withdrawals by the pool creator.

Verify that no further administrative actions are possible by confirming the null status of the mint and freeze authorities via a block explorer. Avoid large positions given the high slippage potential and the absence of verifiable holder distribution data.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access… |
| **Governance / Economics** | 5/10 | Medium | The volume/liquidity ratio of 50.38 indicates significant wash-trading activity (7.4 Economic). 100% of the pool liquidity is unlocked, posing a risk of sudden withdrawal (7.6 External). Holder… |
| **Upgrades** | 8/10 | Low | The token mint is immutable with no upgrade paths for metadata or transfer logic (7.7 Upgrades). Operational security is maintained through the permanent revocation of administrative authorities (7.8… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool's liquidity is burned or locked, meaning the remaining liquidity can be withdrawn by the pool creator at any time.

**Recommendation:** The liquidity provider should burn or lock the LP tokens to ensure the pool's stability and prevent rug-pull scenarios.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 50.38, which significantly exceeds the threshold of 20, indicating artificially inflated trade volume.

**Recommendation:** Exercise caution as the reported volume may not reflect genuine market demand.


### `M-01` — Large Amount of LP Unlocked  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry signals indicate a large amount of LP is unlocked, increasing the risk of liquidity removal.

**Recommendation:** Monitor the liquidity pool for sudden decreases in total value locked.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $186K (DexScreener, all pools). 24h trading volume $9.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $186K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4MtErP...bsEG`](https://solscan.io/account/4MtErPfdRBxHVecToHX5vMu9WzWd8Bgv5ad1TZK7bsEG) |
| **Network** | Solana |
| **Price** | $0.0001233 |
| **24h Volume** | $9.16M |
| **Liquidity** | $186.2K |
| **Volume / Liquidity** | 49.2× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16068 buys / 10050 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ch3t8k5ttqoepspdmfkikhwgpmdpaqpuaetchez2mc9y)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/backed-by-belief-sol-e5d7)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
