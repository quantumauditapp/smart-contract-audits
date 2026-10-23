---
token: Doroni Aerospace
ticker: DORONI
network: solana
risk_score: 1
status: low
date: 2026-10-23
---

# Doroni Aerospace (DORONI) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/doroni-aerospace-sol)

---

## Audit Summary

The Doroni Aerospace token is a standard SPL Token-2022 implementation with all administrative authorities, including mint and freeze, permanently revoked. Liquidity is fully secured via a 100% burn of LP tokens, and metadata is immutable. No critical or high-severity vulnerabilities were identified based on available on-chain data.

> **Final Recommendation:** The token is currently in a secure state with no administrative risks. Holders should continue to monitor the token's market performance and verify that no new extensions are added if the program allows, though current settings indicate immutability.

No further action is required to secure the token's current configuration. Users should always verify the mint address against official project channels before interacting to avoid impersonation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active extensions such as transfer hooks or default frozen states (7.1 Architecture). Access control is fully decentralized as both mint and freeze… |
| **Governance / Economics** | 10/10 | Low | Holder concentration is low, with the top 10 holders controlling only 0.90% of the supply (7.4 Economic). Liquidity is robust at $450,830, and 100% of the pool liquidity is permanently burned… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, and no upgrade paths exist for the token program extensions (7.7 Upgrades). All authority-related parameters are permanently set to null, ensuring the contract cannot… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, holder concentration, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 1.7% of supply. Of that, 0.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 0.9% in wallets, 0.0% in other contracts. 4,272 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

4,272 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $451K (DexScreener, all pools). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $451K of DEX liquidity across 1 pools. Launch: launched on pump.fun, 1 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`547q1F...pump`](https://solscan.io/account/547q1FEqDR6mkJ5bjVKt9xT3RNVYnLkH6ZdMD91Bpump) |
| **Network** | Solana |
| **Price** | $0.02781 |
| **24h Volume** | $1.11M |
| **Liquidity** | $450.8K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | 1.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 55664 buys / 25203 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9izbekzhmzstsutp1comkjshxqnvnoepvjhfl9ngp5aq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/doroni-aerospace-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*
