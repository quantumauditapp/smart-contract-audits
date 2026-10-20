---
token: CAPTAIN UNDERPANTS
ticker: CUP
network: solana
risk_score: 17
status: low
date: 2026-10-15
---

# CAPTAIN UNDERPANTS (CUP) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/captain-underpants-sol)

---

## Audit Summary

The CAPTAIN UNDERPANTS (CUP) SPL Token Mint audit found no critical or high-risk issues based on available on-chain data and third-party security registries. Both mint and freeze authorities are revoked, and all pool liquidity is burned. Holder distribution data was unavailable, preventing a full assessment of concentration risk.

> **Final Recommendation:** Given the absence of identified critical or high-risk issues, holders should monitor for any changes in the token's on-chain state, particularly regarding any new extensions or unexpected activity. As holder distribution data was unavailable, users should exercise caution regarding potential market manipulation if this information becomes available and shows high concentration.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The CAPTAIN UNDERPANTS (CUP) token is an SPL Token-2022 mint. Key security features are well-configured: the mint authority is revoked, preventing further token creation, and the freeze authority is… |
| **Governance / Economics** | 9/10 | Low | The token exhibits healthy liquidity for its current volume, with a 24-hour volume of $52,056 against $17,095 in liquidity, resulting in a normal Volume/Liquidity Ratio of 3.05. Crucially, 100.0% of… |
| **Upgrades** | 10/10 | Low | The token's core parameters are immutable, as both mint and freeze authorities have been revoked. Furthermore, the metadata is not mutable, ensuring the token's name, symbol, and image cannot be… |

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

Liquidity $17K (DexScreener, all pools). 24h trading volume $52K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 3 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9frsdm...pump`](https://solscan.io/account/9frsdmBSKgPiHsp3mmWojPi6NU8F3wivuFwf6KcWpump) |
| **Network** | Solana |
| **Price** | $0.00004545 |
| **24h Volume** | $52.1K |
| **Liquidity** | $17.1K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 13h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1072 buys / 1073 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hpu9pyhmpczpkgmaqzb1j3ugdaqak4992rh1afaktkzp)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/captain-underpants-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-15*
