---
token: goat.fun
ticker: GOAT
network: solana
risk_score: 32
status: low
date: 2026-11-02
---

# goat.fun (GOAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 32/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/goatfun-sol)

---

## Audit Summary

The GOAT token utilizes the SPL Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully locked, mitigating rug-pull risks, though the token is flagged as a 'Copycat' by a third-party registry. Holder concentration data is unavailable, and liquidity is currently below the $10,000 threshold.

> **Final Recommendation:** Investors should exercise caution due to the 'Copycat' classification from third-party registries, which suggests the token may be attempting to impersonate another project. Verify the mint address against official project channels before interacting.

Monitor the liquidity pool for any changes in the locked status, although the current 100% lock is a strong security feature. Given the low liquidity, execute trades in small increments to minimize slippage impact.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the SPL Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is standard for SPL… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic factors show 100% of liquidity is locked, preventing creator withdrawals. 7.5 Governance is decentralized due to the lack of mint authority. 7.6 External signals indicate a 'Copycat'… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints do not utilize proxy patterns. Metadata is immutable, and extension configurations are locked. No further administrative changes to the token's core… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $9,102. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity depth when planning trade sizes.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $50K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 2 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ApQTyc...goat`](https://solscan.io/account/ApQTyckfEL2LfG4ETVPhYf3ETpEXMGmS1YNHJd1Ugoat) |
| **Network** | Solana |
| **Price** | $0.00001235 |
| **24h Volume** | $34.8K |
| **Liquidity** | $9.1K |
| **Volume / Liquidity** | 3.8× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 277 buys / 263 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/a6n323d8rgwgbqexaah9v6kizzpx8vxnumtsmmu1ufqg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/goatfun-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
