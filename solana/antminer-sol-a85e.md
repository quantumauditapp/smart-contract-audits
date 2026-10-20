---
token: AntMiner
ticker: ANT
network: solana
risk_score: 37
status: medium
date: 2026-10-08
---

# AntMiner (ANT) — Smart Contract Security Analysis | Solana

> **Risk Score: 37/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/antminer-sol-a85e)

---

## Audit Summary

The AntMiner (ANT) SPL Token Mint exhibits a low overall risk profile. Both mint and freeze authorities have been revoked, preventing further token issuance or account freezing. The primary finding is that the token's metadata is mutable, allowing for potential changes to its name, symbol, or image post-launch. Third-party risk registry data showed no adverse flags, and chain-native RPC data for holder distribution was unavailable.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the metadata (name, symbol, image) aligns with expectations, as it can be changed by an authority. Monitor the token's official communication channels for any announcements regarding metadata updates. No further critical on-chain verification steps are required regarding minting or freezing capabilities, as these authorities are revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The AntMiner (ANT) token is implemented using the spl-token-2022 program, indicating modern SPL token standards. Crucially, both the Mint Authority and Freeze Authority have been revoked, ensuring no… |
| **Governance / Economics** | 8/10 | Low | Holder concentration is low, with the top 10 holders that can sell accounting for 27.72% of the supply, which does not indicate significant centralization risk. The token has a liquidity of $105,192… |
| **Upgrades** | 8/10 | Low | The Mint Authority and Freeze Authority are both revoked, preventing any further changes to the token's supply or account freeze status. While the `transfer_fee_upgradable` flag is true, the current… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 3.0% · upgradeable |

## Security Findings

_🟢 1 Low · ⚪ 7 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by `metadata_mutable: True`.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 31.5% of supply. Of that, 3.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 12.9% in wallets, 14.8% in other contracts. 946 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as AntMiner (ANT), market cap $2M, rank #2579. 946 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

95.9% of the pool's LP is burned or time-locked. 95.9% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. 4.1% is held, unlocked, by 2 address(es) other than the pool's creator. This assessment covers the main pool, which holds 90% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $118K (DexScreener, all pools). 24h trading volume $783K (CoinGecko, all markets, daily snapshot). 24h trading volume $491K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $118K of DEX liquidity across 4 pools. Launch: 16 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 16 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 16 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7ypCq2...uGrQ`](https://solscan.io/account/7ypCq2CJ4fnbtS3z2B1W1UT2he5E3u7Md6Gy1ri7uGrQ) |
| **Network** | Solana |
| **Price** | $0.001596 |
| **24h Volume** | $445.5K |
| **Liquidity** | $106.6K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 16d |
| **Top-10 Holders** | 31.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1725 buys / 1360 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3b2ys5yvewj7d6susgtespunmauznithmnnftsmamxst)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/antminer-sol-a85e)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
