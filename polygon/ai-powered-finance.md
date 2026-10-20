---
token: AI Powered Finance
ticker: AIPF
network: polygon
risk_score: 30
status: low
date: 2026-10-20
---

# AI Powered Finance (AIPF) — Smart Contract Security Analysis | Polygon

> **Risk Score: 30/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ai-powered-finance-poly)

---

## Audit Summary

The AIPF token is a standard ERC-20 implementation with additional minting capabilities. While ownership has been renounced, the contract retains a centralized minting mechanism controlled by two specific addresses (hgl and qem). The architecture follows standard patterns, but the ability to arbitrarily increase supply poses a significant economic risk to token holders.

> **Final Recommendation:** The protocol should consider implementing a hard cap on the total supply or transitioning the minting authority to a multi-signature wallet or a decentralized governance contract. This would provide transparency and prevent unilateral supply expansion by the current controllers.

Investors should be aware that the 'hgl' and 'qem' addresses have the power to mint tokens at any time. We recommend monitoring these addresses for any unexpected activity that could impact the token's market value.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-style ERC-20 logic for transfers and allowances. 7.1 Architecture is straightforward, relying on standard state variables for balances. 7.2 Code Security… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic risk is elevated due to the minting function. 7.5 Governance is non-existent as ownership is renounced, yet the minting controllers (hgl, qem) operate without community oversight. This… |
| **Upgrades** | 7/10 | Low | 7.7 Upgrades are not applicable as the contract is not a proxy. The implementation is immutable, which provides security against logic changes but prevents fixing the minting issue without a… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Medium · Status: Unresolved)*

The mint(address,uint256) function allows the 'hgl' and 'qem' addresses to create new tokens at will. This allows these controllers to increase the total supply, which directly dilutes the value of all existing tokens held by users.

**Recommendation:** Implement a maximum supply cap or move the minting function to a governance-controlled contract to ensure that supply changes are transparent and community-approved.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 98.9% of supply. Of that, 10.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.6% in wallets, 87.4% in other contracts. 43,753 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as AI Powered Finance (AIPF), market cap $31M, rank #638. 43,753 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $6.6M (DexScreener, all pools). 24h trading volume $167K (CoinGecko, all markets, daily snapshot). 24h trading volume $182K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: 0% on buy, 5% on sell. Market: $6.6M of DEX liquidity across 3 pools. Launch: 335 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2c72...6e28`](https://polygonscan.com/address/0x2c72d25530191ebd244eb6325e1892480b0e6e28) |
| **Network** | Polygon |
| **Price** | $0.358 |
| **24h Volume** | $181.8K |
| **Liquidity** | $6.57M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 98.9% of supply |
| **Buy / Sell Tax** | 0.0% / 5.0% |
| **24h Transactions** | 1524 buys / 2028 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ✅ | Ownership renounced — the deployer can no longer alter the contract. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/polygon/0x124fcfd1b923485c8ccf275afbee4bf557b232d6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ai-powered-finance-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*
