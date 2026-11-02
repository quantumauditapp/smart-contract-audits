---
token: Color of Crypto
ticker: F7931A
network: solana
risk_score: 47
status: medium
date: 2026-11-02
---

# Color of Crypto (F7931A) — Smart Contract Security Analysis | Solana

> **Risk Score: 47/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/color-of-crypto-sol)

---

## Audit Summary

The Color of Crypto token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a permanent lock, and no adverse flags were reported by third-party registries. Holder concentration data was unavailable, and metadata remains mutable.

> **Final Recommendation:** Investors should verify the current metadata on-chain to ensure it aligns with expected branding, as the metadata remains mutable. Given the 1.00% transfer fee, ensure that swap calculations account for this cost to avoid unexpected slippage.

Monitor the token's official channels for any announcements regarding the transfer fee, as this parameter is currently upgradable. No further action is required regarding authority management as both mint and freeze capabilities are permanently revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the SPL Token-2022 program, which supports advanced extensions. 7.1 Architecture is standard, with 7.3 Access Control confirmed by the revocation of both mint and freeze… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic stability is supported by $18,791 in liquidity, which is 100% locked in a permanent LP locker. 7.5 Governance is limited as the mint is fixed. 7.6 External market data shows a 24h volume… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to SPL mints in the EVM sense, but the token metadata is mutable, allowing for potential branding changes. The transfer fee configuration is also marked as upgradable.… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Transfer Fee** | ⚠️ 1.0% · upgradeable |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable and can be changed by the owner at any time.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `L-01` — Upgradable Transfer Fee  *(Severity: Low · Status: Unresolved)*

The transfer fee configuration is marked as upgradable, allowing the fee authority to modify the 1.00% fee rate.

**Recommendation:** Monitor the token's fee parameters periodically to ensure they remain within expected ranges.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $14K (DexScreener, all pools). 24h trading volume $129K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the buy/sell tax; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $14K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3Di8Hz...A67E`](https://solscan.io/account/3Di8HztV3HPKXnch6SBr3r8NGEoW7DgbmRsAipG5A67E) |
| **Network** | Solana |
| **Price** | $0.00002707 |
| **24h Volume** | $127.0K |
| **Liquidity** | $13.8K |
| **Volume / Liquidity** | 9.2× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1142 buys / 826 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gedpnnhylzdphi1yz36sbbpdxtu8k4dxbfx3efet4btf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/color-of-crypto-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
