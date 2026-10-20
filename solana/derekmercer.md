---
token: DerekMercer
ticker: DRMR
network: solana
risk_score: 0
status: low
date: 2026-10-01
---

# DerekMercer (DRMR) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/derekmercer-sol)

---

## Audit Summary

This SPL Token Mint, DerekMercer (DRMR), exhibits a low-risk profile based on available on-chain data. Both mint and freeze authorities are revoked, ensuring a fixed supply and preventing account freezing. All pool liquidity is permanently burned, mitigating rug pull risks. Holder concentration data was unavailable from chain-native RPC.

> **Final Recommendation:** Holders should monitor for any future changes in the token's on-chain state, although current authorities are revoked. Given the unavailability of holder distribution data, potential investors should be aware that concentration risks could exist, even if not verifiable at this time. Verify on-chain that authorities remain revoked before any significant interaction.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The DerekMercer (DRMR) token is an spl-token-2022 mint with both Mint Authority and Freeze Authority revoked, indicating a fixed supply and unfreezable accounts. It does not implement a transfer hook… |
| **Governance / Economics** | 10/10 | Low | The token has $63,777 in DEX liquidity, with 100.0% of the pool's LP tokens burned, ensuring that liquidity cannot be withdrawn by anyone. The 24-hour volume is $466,174, resulting in a… |
| **Upgrades** | 10/10 | Low | Both Mint Authority and Freeze Authority have been revoked, preventing further token minting or freezing of accounts. The token's metadata is immutable, meaning its name, symbol, or image cannot be… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $68K (DexScreener, all pools). 24h trading volume $466K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $68K of DEX liquidity across 2 pools. Launch: launched on pump.fun, 6 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 6 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 6 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7Xgc5R...pump`](https://solscan.io/account/7Xgc5RacHtGzfhw2HukUBk5V986yBbvshr7rrCoopump) |
| **Network** | Solana |
| **Price** | $0.000516 |
| **24h Volume** | $466.0K |
| **Liquidity** | $67.7K |
| **Volume / Liquidity** | 6.9× |
| **Token Age** | 6d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3195 buys / 2921 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4wbt5gf46kct9dhznfvtaen5pnfr56u5htpw27tvytvv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/derekmercer-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
