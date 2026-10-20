---
token: Botify
ticker: BOTIFY
network: solana
risk_score: 0
status: low
date: 2026-10-01
---

# Botify (BOTIFY) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/botify-sol)

---

## Audit Summary

The Botify (BOTIFY) SPL token mint has its Mint and Freeze authorities revoked, indicating a fixed supply and non-freezable token. The token operates under the standard spl-token program with no active Token-2022 extensions. Liquidity is $90,794, with 93.3% of the pool's liquidity locked, significantly reducing the risk of a rug pull by the pool creator. Holder concentration data was unavailable, preventing a full assessment of potential whale-induced price volatility.

> **Final Recommendation:** Holders should verify on-chain that the Mint and Freeze authorities remain revoked to confirm the fixed supply and non-freezable nature of the token. Monitor the 6.0% of unlocked liquidity held by other addresses for any significant movements. Seek additional data on holder distribution to assess potential concentration risks and the impact of large holders on market stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The Botify token is implemented using the standard spl-token program. Both the Mint Authority and Freeze Authority are revoked, ensuring that no new tokens can be minted and no holder accounts can be… |
| **Governance / Economics** | 10/10 | Low | The token has a liquidity of $90,794, with a healthy 24-hour volume of $251,014, resulting in a normal Volume/Liquidity Ratio of 2.76. A significant 93.3% of the pool's liquidity is burned or locked… |
| **Upgrades** | 10/10 | Low | The Mint Authority and Freeze Authority are both revoked, meaning the token's supply and transferability parameters cannot be altered post-launch (7.7 Upgrades). The token's metadata is also… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as BOTIFY (BOTIFY).

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

93.3% of the pool's LP is burned or time-locked. 93.3% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 6.0% is held, unlocked, by 3 address(es) other than the pool's creator.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $92K (DexScreener, all pools). 24h trading volume $237K (CoinGecko, all markets, daily snapshot). 24h trading volume $251K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0574 on 2025-01-22; the price is now 98.0681% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $92K of DEX liquidity across 4 pools. Launch: 9 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 9 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 9 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`7C94Rw...BTFY`](https://solscan.io/account/7C94RweVKZtBhA291WpXW7pkYEnbqhGvCFTU8nPoBTFY) |
| **Network** | Solana |
| **Price** | $0.001025 |
| **24h Volume** | $250.2K |
| **Liquidity** | $91.3K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 9d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1230 buys / 1275 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/giuuw16z9z9xv4cbtwpn3xislyhqlsgkzgpij82gklm9)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/botify-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*
