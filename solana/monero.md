---
token: Monero
ticker: XMR
network: solana
risk_score: 99
status: critical
date: 2026-10-21
---

# Monero (XMR) — Smart Contract Security Analysis | Solana

> **Risk Score: 99/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/monero-sol)

---

## Audit Summary

The token is currently high-risk primarily due to an active mint authority, which allows for unlimited supply inflation. While the freeze authority is revoked, the liquidity pool is entirely unlocked and controlled by a single external wallet, posing a significant risk of liquidity removal. Third-party risk registry data confirms the mint authority remains enabled.

> **Final Recommendation:** Investors should monitor the mint authority address for a potential revocation transaction. Given that 100% of the liquidity is held by an unlocked wallet, users should be prepared for the possibility of sudden liquidity withdrawal.

Verify the current mint authority status on-chain using a block explorer before committing capital. Avoid holding large positions until the mint authority is set to null and liquidity is moved to a time-locked contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token utilizes the standard spl-token program. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is currently compromised by an active mint authority… |
| **Governance / Economics** | 4/10 | Medium | 7.4 Economic factors show moderate holder concentration at 36.89% for the top 10. 7.6 External liquidity is $449,314 with a healthy volume/liquidity ratio of 0.94. However, 100% of pool liquidity is… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not applicable as SPL tokens do not use proxy patterns. Metadata is mutable, allowing for potential branding changes. The mint authority remains active, which is the primary concern… |

## Security Findings

_🔴 2 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 2yy692W8JX511d63i5BdKHqULJCnQyBYrfnkavnzjZuE. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `QA-IDENTITY` — Imitation of Monero (XMR)  *(Severity: Critical · Status: Acknowledged)*

Presents itself as Monero (XMR), but CoinGecko lists no Monero contract on solana at all (CoinGecko). Holders who think they own the real asset own this contract instead; it has none of the real asset's backing, liquidity or redemption.

**Recommendation:** Do not buy, hold or accept this token as the asset it names. Verify any token address against the issuer's official site.


### `H-01` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

100% of the pool's liquidity is held, unlocked, by wallet 5weo7C…pcTd. This wallet can remove that liquidity at any moment and leave holders unable to sell.

**Recommendation:** Watch that wallet's liquidity position; treat the pool as removable until the liquidity is burned or locked.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the pool's creator. One of them — a wallet, 5weo7C…pcTd — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. This assessment covers the main pool, which holds 44% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `L-01` — Flagged by Third-Party Registry  *(Severity: Low · Status: Unresolved)*

An independent third-party risk registry flags the mint authority as enabled.

**Recommendation:** Monitor the mint authority status via on-chain tools.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 57.9% of supply. Of that, 21.0% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 12.7% in wallets, 24.2% in other contracts. 36,316 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.0M (DexScreener, all pools). 24h trading volume $5.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Imitation of Monero (XMR)  *(Severity: Informational · Status: Acknowledged)*

A token presenting itself under the name or ticker of an established asset without being that asset's contract. Its only reason to borrow that identity is to be mistaken for it. Scored as an imitation (see the identity finding). Basis: launched on pump.fun (PumpSwap), a meme launchpad; behaves as: meme token. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.0M of DEX liquidity across 30 pools. Launch: launched on pump.fun (PumpSwap), 175 days of market history.

**Recommendation:** Do not treat this token as the asset it names. Use only the official contract address published by that asset's issuer.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`WXMRyR...teJp`](https://solscan.io/account/WXMRyRZhsa19ety5erZhHg4N3xj3EVN92u94422teJp) |
| **Network** | Solana |
| **Price** | $594.9700 |
| **24h Volume** | $430.1K |
| **Liquidity** | $449.2K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 5mo |
| **Top-10 Holders** | 57.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3611 buys / 3399 sells |

## Security Flags (2/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/4td7od3mmscwkxbagh2qdtgbnwuzh4hel7x3ubvsva56)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/monero-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
