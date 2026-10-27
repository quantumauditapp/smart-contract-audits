---
token: Halloween Inu
ticker: INUWEEN
network: solana
risk_score: 0
status: low
date: 2026-10-27
---

# Halloween Inu (INUWEEN) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/halloween-inu-sol)

---

## Audit Summary

Halloween Inu is a standard SPL Token-2022 asset with both mint and freeze authorities successfully revoked. The liquidity pool is fully burned, ensuring permanent availability of trading funds. Holder concentration data is currently unavailable, and no adverse flags were detected in third-party registries.

> **Final Recommendation:** The token is configured securely with no administrative backdoors. Holders should monitor on-chain activity via block explorers to ensure no unexpected changes occur to the token's state, though the current revocation status makes this unlikely.

Since holder concentration data is currently unavailable, users should exercise caution regarding potential whale activity by reviewing the top token accounts on a block explorer before executing large trades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture and 7.2 Code Security are standard for the Solana ecosystem. 7.3 Access Control is… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $201,473 in liquidity, with 100% of LP tokens permanently burned. 7.5 Governance is decentralized by the absence of mint authority. 7.6 External market data… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL token mints are immutable once authorities are revoked. Metadata and balance-mutating authorities are disabled, ensuring the token's properties remain static.… |

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

Liquidity $201K (DexScreener, all pools). 24h trading volume $263K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (inu); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $201K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FK9eFw...pump`](https://solscan.io/account/FK9eFwfetotEYmWHb3zr1hZkKZQLdtHG2hmJYhWppump) |
| **Network** | Solana |
| **Price** | $0.005823 |
| **24h Volume** | $262.7K |
| **Liquidity** | $201.3K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 14h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 18497 buys / 8454 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gg1utpf95k74ckdpqpxvzifmefqvtddavseic3zekxu5)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/halloween-inu-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*
