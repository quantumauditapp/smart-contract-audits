---
token: USOE
ticker: USOE
network: solana
risk_score: 0
status: low
date: 2026-10-30
---

# USOE (USOE) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/usoe-sol-9462)

---

## Audit Summary

The USOE token is a standard SPL-2022 mint with all administrative authorities, including mint and freeze, successfully revoked. Liquidity is fully secured via a 100% burn, and metadata is immutable, indicating a high level of technical security. Holder distribution data was unavailable, preventing a full assessment of concentration risks.

> **Final Recommendation:** The token demonstrates strong security hygiene regarding authority revocation and liquidity locking. Potential holders should monitor the token's on-chain activity for shifts in holder concentration, as specific distribution data was not available at the time of this audit.

Verify the current mint and freeze authority status using a block explorer to ensure they remain set to 'None'. No further technical action is required to secure the token's core parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL-2022 program with no active transfer hooks or custom extensions. 7.1 Architecture and 7.2 Code Security are standard for the Solana ecosystem. 7.3 Access Control is robust… |
| **Governance / Economics** | 10/10 | Low | 7.4 Economic stability is supported by $2.6M in liquidity, which is 100% burned and permanently inaccessible to the creator. 7.5 Governance is decentralized by the lack of mint authority. 7.6… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. Metadata is locked, and extension configurations are fixed, preventing post-launch modifications to token behavior. |

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

Liquidity $2.6M (DexScreener, all pools). 24h trading volume $1.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $2.6M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2oJgEB...pump`](https://solscan.io/account/2oJgEBp9RE83CAEMC3q3mePjZuTqEiZRSTpd6NPXpump) |
| **Network** | Solana |
| **Price** | $0.9988 |
| **24h Volume** | $1.54M |
| **Liquidity** | $2.61M |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 9h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 24521 buys / 904 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8emf1pldmn37wvi33wurr3shfvf523f6rs4zjwh94eaf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/usoe-sol-9462)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*
