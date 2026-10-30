---
token: ZEROday
ticker: ZERODAY
network: solana
risk_score: 36
status: medium
date: 2026-10-30
---

# ZEROday (ZERODAY) — Smart Contract Security Analysis | Solana

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zeroday-sol-8bb7)

---

## Audit Summary

The ZERODAY token mint has successfully revoked both mint and freeze authorities, mitigating primary centralization risks. However, the token exhibits high-risk economic indicators, including extreme wash-trading signals and a lack of locked liquidity. Third-party registry data indicates significant liquidity risks due to the unlocked status of LP tokens.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume. Monitor the liquidity pool for sudden withdrawals, as the current configuration allows the pool creator to remove all funds at any time.

Verify the current liquidity status via on-chain block explorers before executing any trades. Avoid large positions that cannot be supported by the current $93,159 liquidity depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the standard spl-token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access Control). The… |
| **Governance / Economics** | 4/10 | Medium | The token shows a volume/liquidity ratio of 213.99, indicating potential wash-trading (7.4 Economic). 100% of pool liquidity is unlocked, posing a significant risk of withdrawal (7.6 External).… |
| **Upgrades** | 8/10 | Low | The token mint is immutable (7.7 Upgrades). Metadata is not mutable, and no transfer hooks or upgradeable extensions are active (7.8 Operations). |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 213.99, which significantly exceeds the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity is often used to create a false impression of market interest.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked, meaning the pool creator or current LP holders can withdraw all liquidity at any time.

**Recommendation:** Monitor the liquidity pool for sudden withdrawals and avoid providing liquidity to this pair.


### `M-01` — Third-Party Risk Registry Flag  *(Severity: Medium · Status: Unresolved)*

The token is flagged by a third-party registry for having a large amount of unlocked LP and a low number of liquidity providers.

**Recommendation:** Review the token's liquidity provider distribution and consider the risks associated with low-participation pools.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 82.1% of supply. Of that, 51.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 30.2% in wallets, 0.0% in other contracts. 1,888 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,888 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $66K (DexScreener, all pools). 24h trading volume $14.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $66K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`39755Z...bDf8`](https://solscan.io/account/39755Znjp5t876QC2CNL76hWFuyT4txBfBampTYNbDf8) |
| **Network** | Solana |
| **Price** | $0.0001038 |
| **24h Volume** | $14.16M |
| **Liquidity** | $65.5K |
| **Volume / Liquidity** | 216.1× |
| **Token Age** | 1h |
| **Top-10 Holders** | 82.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13928 buys / 9544 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/32h9sricjtu77btefelhsazdhb5haghrpwjgxpv31rdc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zeroday-sol-8bb7)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
