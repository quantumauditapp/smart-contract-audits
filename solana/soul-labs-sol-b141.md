---
token: Soul Labs
ticker: SO
network: solana
risk_score: 29
status: low
date: 2026-10-21
---

# Soul Labs (SO) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-b141)

---

## Audit Summary

The primary risks identified involve extreme volume-to-liquidity distortion alongside completely unlocked DEX pool reserves. Specifically, 24-hour volume reached $53,269,706 against $335,109 in liquidity (a 158.96 ratio indicative of artificial activity), while 0.0% of pool liquidity is burned or locked. Chain-native RPC data for holder concentration was unavailable during this assessment.

> **Final Recommendation:** Inspect decentralized exchange transaction signatures on a block explorer to determine whether trading activity stems from distinct retail wallets or automated loops between correlated accounts. Verify the specific wallet addresses holding the liquidity pool tokens to ascertain whether major liquidity providers commit their holdings to a verifiable timelock.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the standard spl-token program with 6 decimals and a raw supply of 99,999,999,654,733,683. The mint authority and freeze authority are both revoked (None), meaning no… |
| **Governance / Economics** | 5/10 | Medium | Market parameters demonstrate significant economic anomalies, with total DEX liquidity standing at $335,109 across a pair created 0 days ago. The 24-hour trading turnover generated a… |
| **Upgrades** | 8/10 | Low | SPL token mints contain no proxy upgrade mechanisms, and the configuration here is fully finalized. Mint and freeze authorities are irrevocably nullified, disallowing administrative state changes.… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 158.96x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Examine trading signatures to differentiate legitimate buyer turnover from cyclical transactions executed by automated market bots.


### `M-01` — Pool Liquidity Not Locked  *(Severity: Medium · Status: Unresolved)*

Only 0.0% of the pool's liquidity is burned or locked; the rest can be withdrawn by whoever holds it (Solana LP holders are anonymous in the available data).

**Recommendation:** Monitor LP token balances and establish alerts for significant liquidity withdrawals from the primary market pool.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $323K (DexScreener, all pools). 24h trading volume $48.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $323K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3z3VVd...YbnD`](https://solscan.io/account/3z3VVdRPvu742VDsNKtjASJfrPVQZDKJ8B4VC63FYbnD) |
| **Network** | Solana |
| **Price** | $0.00001874 |
| **24h Volume** | $48.45M |
| **Liquidity** | $323.1K |
| **Volume / Liquidity** | 149.9× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 24373 buys / 22091 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7ry4a9qx9bbvk3p81qevg9eznmpmcpach3rtpqjksg48)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/soul-labs-sol-b141)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
