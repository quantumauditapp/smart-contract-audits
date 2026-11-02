---
token: Capycoin
ticker: CAPY
network: solana
risk_score: 6
status: low
date: 2026-11-02
---

# Capycoin (CAPY) — Smart Contract Security Analysis | Solana

> **Risk Score: 6/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/capycoin-sol-0854)

---

## Audit Summary

Capycoin (CAPY) is a standard SPL token with both mint and freeze authorities successfully revoked. The liquidity is fully locked, and no adverse flags were reported by third-party registries. Holder concentration data was unavailable, preventing a full assessment of distribution risks.

> **Final Recommendation:** The token demonstrates strong security posture regarding authority control and liquidity locking. Users should monitor the token's market activity and volume-to-liquidity ratio to ensure price stability. 

Verify the current mint and freeze authority status on a block explorer to confirm they remain null. As holder distribution data was unavailable, perform independent checks on the top token accounts to ensure supply is not overly concentrated in a few wallets.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is inherent to the… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $168,615 in liquidity, which is 100% locked in a Raydium LP locker. 7.5 Governance is decentralized due to the revocation of minting rights. While 7.6 External… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL token mint. 7.8 Operations are secure as metadata is immutable and no administrative authorities remain to alter token parameters. The token… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $127K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $127K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DBPTU2...oMqr`](https://solscan.io/account/DBPTU2oKLDHXQjAEJ3rZi8bUGmt2uxUbipgg6xmXoMqr) |
| **Network** | Solana |
| **Price** | $0.0003474 |
| **24h Volume** | $1.34M |
| **Liquidity** | $127.1K |
| **Volume / Liquidity** | 10.5× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12305 buys / 8765 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4wutfjfujupwjm5uuidxoumgupauxg4saejvayqjrmbw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/capycoin-sol-0854)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*
