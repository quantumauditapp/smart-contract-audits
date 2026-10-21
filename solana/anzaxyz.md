---
token: anza.xyz
ticker: ANZA
network: solana
risk_score: 19
status: low
date: 2026-10-21
---

# anza.xyz (ANZA) — Smart Contract Security Analysis | Solana

> **Risk Score: 19/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anzaxyz-sol)

---

## Audit Summary

The ANZA token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While liquidity is fully burned, a third-party risk registry has flagged the creator for historical involvement in rug-pull activities. The protocol demonstrates standard token architecture with no active transfer hooks or mutable metadata.

> **Final Recommendation:** Given the third-party risk registry flag regarding the creator's history, users should exercise extreme caution regardless of the technical security of the mint. Monitor the top holder wallets for any signs of coordinated selling activity.

Verify the current mint and freeze authority status directly on-chain using a block explorer to confirm they remain null. Do not rely solely on the technical immutability of the token if the project's governance or historical reputation is in question.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or… |
| **Governance / Economics** | 9/10 | Low | Top 10 holders control 28.20% of the supply, indicating moderate distribution (7.4 Economic). Liquidity is $11,935 and is 100% burned, preventing withdrawal by the creator (7.4 Economic). Trading… |
| **Upgrades** | 10/10 | Low | Metadata is immutable, preventing branding changes (7.7 Upgrades). There are no upgradeable transfer hooks or fee configurations (7.7 Upgrades). The token program state is locked, ensuring consistent… |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `M-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Medium · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on the developer's history of creating rugged tokens.

**Recommendation:** Exercise extreme caution and perform independent due diligence on the project team before interacting with this token.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 53.8% of supply. Of that, 25.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 28.2% in wallets, 0.0% in other contracts. 216 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

216 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $13K (DexScreener, all pools). 24h trading volume $55K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $13K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 6 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3qrHwZ...pump`](https://solscan.io/account/3qrHwZchJwYc4rRCqDoqXyKPpW3G4AyjfLqYH8rXpump) |
| **Network** | Solana |
| **Price** | $0.00003019 |
| **24h Volume** | $54.7K |
| **Liquidity** | $13.3K |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 6d |
| **Top-10 Holders** | 53.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 937 buys / 642 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9k7fyk5vjkakwprhuaka6dqomyr4phzjkjakxzfgvfyc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anzaxyz-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*
