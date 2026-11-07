---
token: The Roaring Kitty
ticker: TRK
network: solana
risk_score: 22
status: low
date: 2026-11-07
---

# The Roaring Kitty (TRK) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/the-roaring-kitty-sol)

---

## Audit Summary

The TRK token mint has successfully revoked both mint and freeze authorities, ensuring supply immutability and preventing account freezing. Liquidity is robustly secured with 96.9% locked, mitigating rug-pull risks. The primary identified risk is the mutability of token metadata, which allows for future changes to branding or naming.

> **Final Recommendation:** Investors should note that while the token is technically secure regarding supply and liquidity, the metadata remains mutable. Verify the token name and symbol on-chain before executing trades to ensure they match expected branding.

Monitor the top 10 holder distribution periodically to ensure no single entity accumulates a majority stake, which could impact market stability despite the current low concentration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is effectively managed as both mint and freeze… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance factors are favorable, with 96.9% of liquidity locked for good. Holder concentration is moderate at 33.14% for the top 10 holders. 7.6 External market data shows a… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints in the EVM sense. Metadata is currently mutable, allowing for potential changes to the token's name or symbol. No other upgradeable parameters exist for… |

## Security Findings

_🟢 1 Low · ⚪ 7 Informational_

### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

The token metadata (name, symbol, image) is currently mutable and can be changed by the owner of the metadata update authority.

**Recommendation:** Verify the token metadata against official project channels before interacting. If the project intends to finalize branding, the metadata authority should be revoked.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 33.1% of supply. Of that, 10.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 22.3% in wallets, 0.0% in other contracts. 554 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

554 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

97.0% of the pool's LP is burned or time-locked. 97.0% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 3.0% is held, unlocked, by 2 address(es) other than the pool's creator.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $37K (DexScreener, all pools). 24h trading volume $242K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $37K of DEX liquidity across 3 pools. Launch: 7 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 7 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 7 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`E8c9gv...BAGS`](https://solscan.io/account/E8c9gvuE7gW4R8AVcaTCbbTG1zJGdUR9KGtS94eXBAGS) |
| **Network** | Solana |
| **Price** | $0.0001693 |
| **24h Volume** | $241.4K |
| **Liquidity** | $36.2K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 7d |
| **Top-10 Holders** | 33.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2191 buys / 1374 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9kwqddbnybnedf56dr2ackzeiz2ak6anrwtjhnzlhtlc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/the-roaring-kitty-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*
