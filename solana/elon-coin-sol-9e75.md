---
token: Elon Coin
ticker: ELON
network: solana
risk_score: 48
status: medium
date: 2026-10-20
---

# Elon Coin (ELON) — Smart Contract Security Analysis | Solana

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/elon-coin-sol-9e75)

---

## Audit Summary

Elon Coin (ELON) is a Token-2022 asset with both mint and freeze authorities successfully revoked. The protocol demonstrates strong liquidity security with 99.7% of pool liquidity permanently locked. Risks are limited to mutable metadata and a configurable transfer fee, which are standard for this token program.

> **Final Recommendation:** Investors should verify the current transfer fee percentage via the token's on-chain account data before executing large swaps, as this value is subject to change. 

Given the high volume/liquidity ratio, users should utilize limit orders or slippage protection to mitigate the impact of potential volatility. No further on-chain action is required to secure the token, as authority revocation is already confirmed.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the Token-2022 program, ensuring compatibility with advanced extensions. 7.1 Architecture is standard for SPL mints, while 7.2 Code Security relies on the audited core program. 7.3… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic health is supported by $139,572 in liquidity, with 99.7% of the pool locked, mitigating 7.8 Operations risk. 7.5 Governance is decentralized, with the top 10 holders controlling 23.84%… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to the mint itself, though the token metadata remains mutable. The transfer fee is currently set at 100 bps (1.00%) and is marked as upgradable by the fee authority.… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 7 Informational_

### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable, allowing the current controller to modify branding post-launch.

**Recommendation:** Verify the token metadata against official project channels before interacting with the asset.


### `L-01` — Upgradable Transfer Fee  *(Severity: Low · Status: Unresolved)*

The transfer fee is currently 1.00% but is configured as upgradable, meaning the fee authority can adjust this rate at any time.

**Recommendation:** Monitor the transfer fee extension state periodically to ensure the cost of trading remains within expected parameters.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 27.6% of supply. Of that, 3.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.8% in wallets, 0.0% in other contracts. 5,503 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

5,503 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

99.7% of the pool's LP is burned or time-locked. 99.7% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. 0.3% is held, unlocked, by 2 address(es) other than the pool's creator. This assessment covers the main pool, which holds 72% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $201K (DexScreener, all pools). 24h trading volume $2.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (elon). Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $201K of DEX liquidity across 10 pools. Launch: 3 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 3 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 3 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`B2GESk...2sZx`](https://solscan.io/account/B2GESkSErPjuCq6n4LcaJP5v2z1kJnw3xHVZnop2sZx) |
| **Network** | Solana |
| **Price** | $0.001834 |
| **24h Volume** | $1.46M |
| **Liquidity** | $144.7K |
| **Volume / Liquidity** | 10.1× |
| **Token Age** | 3d |
| **Top-10 Holders** | 27.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7051 buys / 5738 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cnhqem7jpbja5p2xhbgphqg7e9nkzwcqr9q6r9ywb7zf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/elon-coin-sol-9e75)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
