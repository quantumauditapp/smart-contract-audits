---
token: The Bee King
ticker: BKING
network: solana
risk_score: 42
status: medium
date: 2026-10-22
---

# The Bee King (BKING) — Smart Contract Security Analysis | Solana

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-bee-king-sol)

---

## Audit Summary

The Bee King (BKING) is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong protection against supply inflation and account freezing. However, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading, and liquidity is low. All third-party risk registry data was available and reported no adverse flags.

> **Final Recommendation:** Investors should monitor the liquidity pool for significant slippage due to the low total value locked. Given the high volume-to-liquidity ratio, users should exercise caution regarding the authenticity of trading volume.

Verify the current supply and holder distribution on-chain using a block explorer to ensure no single wallet holds a majority stake. No further action is required regarding authority management as they are already revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the Token-2022 program with no active extensions like transfer hooks or default frozen states. 7.1 Architecture is standard for SPL mints. 7.3 Access Control is robust as both mint… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic analysis shows a volume/liquidity ratio of 46.00, which exceeds the 20 threshold and indicates suspicious trading activity. 7.5 Governance is decentralized as no single entity controls… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to this mint as it is a fixed-authority asset. Metadata is immutable, preventing branding changes. No transfer fee or hook upgrades are possible. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $8,748. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for high slippage in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 46x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; trading volume may not reflect genuine market demand.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $8K (DexScreener, all pools). 24h trading volume $436K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 55.8% of supply. Of that, 31.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 24.1% in wallets, 0.0% in other contracts. 259 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

259 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $8K of DEX liquidity across 6 pools. Launch: launched on pump.fun, 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8okvwo...pump`](https://solscan.io/account/8okvwotUnbwujEG23SptHYqpyPyssrGgyfjG3SaLpump) |
| **Network** | Solana |
| **Price** | $0.00001349 |
| **24h Volume** | $401.5K |
| **Liquidity** | $8.4K |
| **Volume / Liquidity** | 48.0× |
| **Token Age** | 3d |
| **Top-10 Holders** | 55.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4933 buys / 4181 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/b41jlyrhhap9zmqanba2guwn88h6pdoggwdkydjwwn83)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-bee-king-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*
