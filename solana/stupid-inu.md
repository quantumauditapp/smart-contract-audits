---
token: Stupid Inu
ticker: SI
network: solana
risk_score: 16
status: low
date: 2026-10-06
---

# Stupid Inu (SI) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/stupid-inu-sol)

---

## Audit Summary

The Stupid Inu (SI) token mint has revoked both mint and freeze authorities, indicating a fixed supply and unfreezable accounts. However, a significant portion of the supply, 59.00%, is concentrated among the top ten holders that can sell, posing a risk of market manipulation. Third-party registry data also flags high holder concentration. Chain-native RPC data for holder distribution was unavailable.

> **Final Recommendation:** Holders should monitor the wallets identified as top holders for any significant movements that could impact market stability. While liquidity is locked, the concentration of tokens in a few hands remains a risk factor. Verify on-chain that the mint and freeze authorities remain revoked to confirm the immutability of supply and account status.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Stupid Inu (SI) token is implemented using the spl-token-2022 program. Both the mint authority and freeze authority have been revoked, ensuring no new tokens can be minted and no existing… |
| **Governance / Economics** | 9/10 | Low | A notable concern is the holder concentration, with the top 10 holders that can sell controlling 59.00% of the total supply. This level of concentration is flagged by a third-party risk registry and… |
| **Upgrades** | 10/10 | Low | The mint authority and freeze authority are both revoked, meaning the token's supply and account freeze status are immutable. The token does not utilize any Token-2022 extensions that would allow for… |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell hold 59.00% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range. This concentration is also flagged by a third-party risk registry.

**Recommendation:** Be aware that a significant portion of the token supply is concentrated among a few holders, which could lead to price volatility if they decide to sell. Monitor these large holder wallets for unusual activity.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 68.1% of supply. Of that, 10.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 13.8% in wallets, 44.0% in other contracts. 1,484 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,484 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $92K (DexScreener, all pools). 24h trading volume $663K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $92K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 6 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3VPoXa...pump`](https://solscan.io/account/3VPoXaRcXxju8qgkVRN87UuXZxbdBD7zyaXPDqqmpump) |
| **Network** | Solana |
| **Price** | $0.0007065 |
| **24h Volume** | $662.5K |
| **Liquidity** | $91.5K |
| **Volume / Liquidity** | 7.2× |
| **Token Age** | 6d |
| **Top-10 Holders** | 68.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6212 buys / 3786 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gnpvosiacuqbkxpptfo2c79cx2qtukgxawhekyljodbe)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/stupid-inu-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-06*
