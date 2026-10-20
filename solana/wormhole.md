---
token: Wormhole
ticker: W
network: solana
risk_score: 10
status: low
date: 2026-10-08
---

# Wormhole (W) — Smart Contract Security Analysis | Solana

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wormhole-sol)

---

## Audit Summary

The Wormhole Token (W) mint has revoked both mint and freeze authorities, indicating a fixed supply and unfreezable accounts. However, a significant portion of the token's DEX liquidity is not locked or burned, posing a risk of liquidity withdrawal. Additionally, the token's metadata is mutable, allowing for potential changes to its branding. Third-party registry data indicates mutable metadata but does not flag the token as high-risk. Chain-native RPC data for holder distribution was fully available.

> **Final Recommendation:** Holders should monitor the liquidity pool's status to ensure that the unlocked liquidity is not withdrawn, which could severely impact the ability to trade the token. It is also advisable to periodically verify the token's metadata (name, symbol, image) against official sources to confirm it aligns with expectations, given its mutability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Wormhole Token (W) is implemented using the standard `spl-token` program. Both the mint authority and freeze authority have been revoked, ensuring that no new tokens can be minted and no holder… |
| **Governance / Economics** | 7/10 | Low | The token exhibits a moderate level of holder concentration, with the top 10 holders that can sell accounting for 36.19% of the total supply. The DEX liquidity stands at $132,300, which is sufficient… |
| **Upgrades** | 8/10 | Low | The mint authority and freeze authority are both revoked, preventing any further changes to the token's supply or account freeze status. While the token uses the classic SPL Token Program v3, its… |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `M-01` — Pool Liquidity Not Locked  *(Severity: Medium · Status: Unresolved)*

Only 0.0% of the pool's liquidity is burned or locked; the rest can be withdrawn by whoever holds it. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified. (Fact: Pool Liquidity Burned or Locked for Good: 0.0%)

**Recommendation:** Exercise caution as a significant portion of liquidity can be removed.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch. (Fact: metadata_mutable: True)

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 36.2% of supply. What remains: 24.5% in wallets, 11.7% in other contracts. 96,571 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Wormhole (W), market cap $115M, rank #264. On GoPlus's list of trusted tokens. 96,571 holders. Verified by: CoinGecko, GoPlus.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified. This assessment covers the main pool, which holds 34% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $388K (DexScreener, all pools). 24h trading volume $46.8M (CoinGecko, all markets, daily snapshot). 24h trading volume $407K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1.66 on 2024-04-03; the price is now 98.9462% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Governance token  *(Severity: Informational · Status: Acknowledged)*

A token whose main use is voting on a protocol's decisions (delegation and vote checkpoints in its code). The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Governance. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $388K of DEX liquidity across 30 pools. Launch: launched on pump.fun (PumpSwap), 918 days of market history.

**Recommendation:** Check how much of the voting supply insiders hold and what governance can change.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`85VBFQ...QAmQ`](https://solscan.io/account/85VBFQZC9TZkfaptBWjvUw7YbZjy52A6mjtPGjstQAmQ) |
| **Network** | Solana |
| **Price** | $0.01615 |
| **24h Volume** | $117.8K |
| **Liquidity** | $132.6K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 2y |
| **Top-10 Holders** | 36.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1217 buys / 1507 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4gbdoceuxqqcyzgaqkn3wc5fivb34fwfjvtvgduf6vlz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wormhole-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*
