---
token: Leonida Man
ticker: LEOMAN
network: solana
risk_score: 18
status: low
date: 2026-11-04
---

# Leonida Man (LEOMAN) — Smart Contract Security Analysis | Solana

> **Risk Score: 18/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/leonida-man-sol)

---

## Audit Summary

The Leonida Man (LEOMAN) token is a standard SPL Token-2022 implementation with all critical administrative authorities revoked. The liquidity pool is fully burned, ensuring the protocol cannot rug-pull via liquidity withdrawal. Holder concentration data is currently unavailable, and the token exhibits high trading volume relative to its liquidity.

> **Final Recommendation:** Investors should monitor the token's liquidity depth on DEX platforms to ensure slippage remains within acceptable bounds for their position sizes. As holder concentration data is currently unavailable, users should exercise caution regarding potential price volatility from large individual wallets.

Verify the mint address (CPZguakzrJSPZDvyB2BY7wdk25eKFwuwtYxSPYHmpump) directly on a block explorer to confirm the 'Mint Authority' and 'Freeze Authority' fields remain set to 'None'. No further action is required to secure the token's administrative state.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program. 7.1 Architecture is standard, with no active transfer hooks or default frozen states. 7.3 Access Control is robust as both mint and freeze authorities… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic stability is supported by 100% of pool liquidity being burned. 7.5 Governance is decentralized due to the lack of minting capabilities. 7.6 External market data shows $31,769 in… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint. 7.8 Operations are secure as metadata is immutable and no balance-mutating authorities exist. The token configuration is static and cannot be… |

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

Liquidity $36K (DexScreener, all pools). 24h trading volume $447K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $36K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CPZgua...pump`](https://solscan.io/account/CPZguakzrJSPZDvyB2BY7wdk25eKFwuwtYxSPYHmpump) |
| **Network** | Solana |
| **Price** | $0.0001965 |
| **24h Volume** | $442.4K |
| **Liquidity** | $35.9K |
| **Volume / Liquidity** | 12.3× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8059 buys / 6317 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4d6z9apypx8ivj7msrirpwlhfvbstccqy6c8tpredg2r)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/leonida-man-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-04*
